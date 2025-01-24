# TGDrive - A Google Drive Clone with Telegram Storage

Welcome to TGDrive! This web application replicates Google Drive's functionalities using Telegram as its storage backend. Manage folders and files, perform actions like uploading, renaming, and deleting, utilize trash/bin support, enable permanent deletion, and share public links. The application offers admin login and automatically backs up the database to Telegram.


## Features

- **File Management:** Upload, rename, and delete files with integrated trash/bin functionality and permanent deletion support.
- **Folder Management:** Easily create, rename, and delete folders.
- **Sharing:** Seamlessly share public links for files and folders.
- **Admin Support:** Secure admin login for efficient management.
- **Automatic Backups:** Automated database backups sent directly to Telegram.
- **Multiple Bots/Clients:** Support for multiple bots/clients for file operations and streaming from Telegram.
- **Large File Support:** Upload files up to 4GB using Telegram Premium accounts.
- **Auto Pinger:** Built-in feature to keep the website active by preventing idle timeouts.
- **URL Upload Support:** Upload files directly to TG Drive from any direct download link of a file.
- **Bot Mode:** Upload files directly to any folder in TG Drive by sending the file to the bot on Telegram ([Know More](#tg-drives-bot-mode))

## Tech Stack

- **Backend:** Python, FastAPI
- **Frontend:** HTML, CSS, JavaScript
- **Database:** Local storage as a class object, saved to a file using the pickle module.
- **Storage:** Telegram

## Demo


Feel free to test the features with the provided login credentials.

### Environment Variables

#### Required Variables

| Variable Name            | Type    | Example                   | Description                                                          |
| ------------------------ | ------- | ------------------------- | -------------------------------------------------------------------- |
| `API_ID`                 | integer | 123456                    | Your Telegram API ID                                                 |
| `API_HASH`               | string  | dagsjdhgjfsahgjfh         | Your Telegram API Hash                                               |
| `BOT_TOKENS`             | string  | 21413535:gkdshajfhjfakhjf | List of Telegram bot tokens for file operations, separated by commas |
| `STORAGE_CHANNEL`        | integer | -100123456789             | Chat ID of the Telegram storage channel                              |
| `DATABASE_BACKUP_MSG_ID` | integer | 123                       | Message ID of a file in the storage channel for database backups     |

> Note: All bots mentioned in the `BOT_TOKENS` variable must be added as admins in your `STORAGE_CHANNEL`.

> Note: `DATABASE_BACKUP_MSG_ID` should be the message ID of a file (document) in the `STORAGE_CHANNEL`.

#### Optional Variables

| Variable Name          | Type                 | Default                                    | Description                                                                                                 |
| ---------------------- | -------------------- | ------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| `ADMIN_PASSWORD`       | string               | admin                                      | Password for accessing the admin panel                                                                      |
| `STRING_SESSIONS`      | string               | None                                       | List of Premium Telegram Account Pyrogram String Sessions for file operations                               |
| `SLEEP_THRESHOLD`      | integer (in seconds) | 60                                         | Delay in seconds before retrying after a Telegram API floodwait error                                       |
| `DATABASE_BACKUP_TIME` | integer (in seconds) | 60                                         | Interval in seconds for database backups to the storage channel                                             |
| `MAX_FILE_SIZE`        | float (in GBs)       | 1.98 (3.98 if `STRING_SESSIONS` are added) | Maximum file size (in GBs) allowed for uploading to Telegram                                                |
| `WEBSITE_URL`          | string               | None                                       | Website URL (with https/http) to auto-ping to keep the website active                                       |
| `MAIN_BOT_TOKEN`       | string               | None                                       | Your Main Bot Token to use [TG Drive's Bot Mode](#tg-drives-bot-mode)                                       |
| `TELEGRAM_ADMIN_IDS`   | string               | None                                       | List of Telegram User IDs of admins who can access the [bot mode](#tg-drives-bot-mode), separated by commas |

> Note: Premium Client (`STRING_SESSIONS`) will be used only to upload files when file size is greater than 2GB.

> Note: File streaming/downloads will be handled by bots (`BOT_TOKENS`).

> Note: Read more about TG Drive's Bot Mode [here](#tg-drives-bot-mode).

## Deploying Your Own TG Drive Application

### 1. Clone the Repository

First, clone the repository and navigate into the project directory:


### 2. Set Up Your Environment Variables

Create a `.env` file in the root directory and add the necessary [environment variables](#environment-variables).

> **Note:** Some hosting services allow you to set environment variables directly through their interface, which may eliminate the need for a `.env` file.

### 3. Running TG Drive

#### Deploying Locally

1. Install the required Python packages:

   ```bash
   pip install -U -r requirements.txt
   ```

2. Start the TG Drive application using Uvicorn:

   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8000
   ```

#### Deploying Using Docker

1. Build the Docker image:

   ```bash
   docker build -t tgdrive .
   ```

2. Run the Docker container:

   ```bash
   docker run -d -p 8000:8000 tgdrive
   ```

Access the application at `http://127.0.0.1:8000` or `http://your_ip:8000`.



## Contributing

Contributions are welcome! Fork the repository, make your changes, and create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Support

For inquiries or support, join our [Telegram Support Group](https://telegram.me/smnetworkk) or email [isoraflix@gmail.com](mailto:isoraflix@gmail.com).
