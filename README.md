# SSH-TEST
Repo to Test SSH Keys

In this repo we will make some change to document how we setup SSH Keys.

# Install

The following is based on the following document.

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

1. Create SSH Key

```
cd $HOME/.ssh
ssh-keygen -t ed25519 -C "sma.matthews.developer@gmail.com"
```
The following is the output generated from the above command.

Generating public/private ed25519 key pair.
Enter file in which to save the key (/Users/sam/.ssh/id_ed25519): id_ed25519_password
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in id_ed25519_password
Your public key has been saved in id_ed25519_password.pub
The key fingerprint is:
SHA256:J3keLZm6wSo9tBhpT8RDUsScH6tXFckCzHpn3TsszZc sam.matthews.developer@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|     =o+.. ..o   |
|    . = + . +    |
|     + o o + .   |
|      = +.++. .  |
|     o +S+B .+ ..|
|    + +..* o. *E.|
|   . B o+ .  . o |
|    o =. o       |
|     ....        |
+----[SHA256]-----+


2. Add SSH Key to the SSH-Agent

MAC: 

`eval "$(ssh-agent -s)"`

3. Update $HOME/.ssh/config with the SSH Key and opther information you mentioned above.

```
Host *.github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519_password

```

4. Add private key to the ssh-agent

`ssh-add --apple-use-keychain ~/.ssh/id_ed25519_password`

# TESTS

1. Remove original SSH Keys and use new KEYS.


