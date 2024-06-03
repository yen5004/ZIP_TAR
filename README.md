# ZIP_TAR
developer tips for cli commands

# ZIP/TAR

To encode a folder in Linux using the command line, you can use tools like `zip` or `tar` along with encryption options. Here's how you can do it using both methods:

### Using `zip` with Encryption

1. **Install Zip**: If `zip` is not already installed, you can install it using the package manager of your Linux distribution. For example, on Debian/Ubuntu-based systems:
    
    ```
    sudo apt update
    sudo apt install zip
    
    ```
    
2. **Encrypt a Folder**:
    
    ```
    zip -r -e encrypted.zip folder_to_encrypt
    
    ```
    
    Replace `encrypted.zip` with the desired name of the encrypted zip file and `folder_to_encrypt` with the name of the folder you want to encrypt.
    
3. **Enter Password**: You will be prompted to enter a password. This password will be used to encrypt the zip file.
4. **Verify Encryption**:
You can verify that the folder is encrypted by listing the contents of the zip file. It should show encrypted filenames.

### Using `tar` with OpenSSL for Encryption

1. **Encrypt a Folder**:
    
    ```
    tar -cz folder_to_encrypt | openssl aes-256-cbc -e -out encrypted.tar.gz.aes
    
    ```
    
    Replace `folder_to_encrypt` with the name of the folder you want to encrypt and `encrypted.tar.gz.aes` with the desired name of the encrypted file.
    
2. **Enter Password**:
You will be prompted to enter a password. This password will be used to encrypt the tar file.
3. **Verify Encryption**:
You can verify that the folder is encrypted by attempting to extract the contents using `tar`. It should prompt for the password to decrypt the file.

### Decrypting the Encrypted Folder

To decrypt the encrypted folder, you'll need the password used for encryption.

- For `zip`, you can use:
    
    ```
    unzip encrypted.zip
    
    ```
    
- For `tar` with OpenSSL, you can use:
    
    ```
    openssl aes-256-cbc -d -in encrypted.tar.gz.aes | tar -xz
    
    ```
    

Replace `encrypted.zip` or `encrypted.tar.gz.aes` with the actual encrypted file name.

These methods allow you to securely encode and decode folders in Linux using command line tools.
