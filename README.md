# MySQL-Notes

If you've forgotten the MySQL root password on Windows and need to reset it, you can follow these steps:

### Step 1: Stop the MySQL Server

1. Open a Command Prompt with administrative privileges. To do this, right-click on the Command Prompt and select "Run as administrator."
2. Stop the MySQL service using the following command:
   ```sh
   net stop MySQL
   ```
   Replace `MySQL` with the name of your MySQL service if it's different (e.g., `MySQL80` for MySQL 8.0).

### Step 2: Start MySQL in Safe Mode

1. Open a new Command Prompt window with administrative privileges.
2. Start MySQL in safe mode with the `--skip-grant-tables` option to disable authentication:
   ```sh
   mysqld --skip-grant-tables
   ```

   Leave this Command Prompt window open as it is running the MySQL server in safe mode.

### Step 3: Reset the Root Password

1. Open another Command Prompt window (you can have multiple Command Prompt windows open simultaneously).
2. Log in to MySQL without a password:
   ```sh
   mysql -u root
   ```
3. Once logged in, reset the root password using the following commands. Replace `new_password` with your new desired password:
   ```sql
   FLUSH PRIVILEGES;
   ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
   ```
4. Exit the MySQL shell:
   ```sh
   exit
   ```

### Step 4: Restart the MySQL Server

1. Return to the first Command Prompt window where MySQL was running in safe mode.
2. Stop the MySQL server by closing the Command Prompt window or pressing `Ctrl + C`.
3. Start the MySQL service normally:
   ```sh
   net start MySQL
   ```

### Step 5: Verify the New Password

1. Open MySQL Workbench or another MySQL client.
2. Attempt to log in with the new root password you set.

### Troubleshooting

- If `mysqld` is not recognized, make sure your MySQL bin directory is in the system PATH or navigate to the MySQL bin directory before running the `mysqld` command.
- If you encounter issues starting or stopping the MySQL service, ensure you are running Command Prompt with administrative privileges.

By following these steps, you should be able to reset the MySQL root password on Windows. If you encounter any issues, please let me know!
