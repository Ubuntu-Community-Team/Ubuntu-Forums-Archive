---
title: "File encryption"
date: 2005-08-27
forum: Desktop Environments
---

### Post by dbeckham32 on 2005-08-27
Can anyone please recommend an easy way to encrypt files? Does Ubuntu ship with an encrypt utility? I have some financial files in my home directory that I'd like secured but I'd rather not encrypt the entire home directory.

Any ideas? Must be a command line tool for this.

Thanks in advance!

---

### Post by brk3 on 2005-08-27
gpg is the tool for this. check the repos for a frontend called 'seahorse' which should make this very easy to use. If you have the kde libs installed I would also definatly recomend kgpg

---

### Post by dbeckham32 on 2005-08-27
Thanks. I've downloaded and install Seahorse and used it to create a key. However, I'm having some trouble using gpg at the command line to encrypt my file.

Can someone please assist me with the syntax? I have:



$gpg --encrypt name_of_my_key name_of_file_to_encrypt



It returns an error complaining about the syntax: "usage: gpg [options] --encrypt [filename]"

I've recently switched from Windows, but I'm slowly getting the hang of Linux.

Thanks for your help!

---

### Post by cwaldbieser on 2005-08-28
[QUOTE=dbeckham32]Thanks. I've downloaded and install Seahorse and used it to create a key. However, I'm having some trouble using gpg at the command line to encrypt my file.

Can someone please assist me with the syntax? I have:



$gpg --encrypt name_of_my_key name_of_file_to_encrypt



It returns an error complaining about the syntax: "usage: gpg [options] --encrypt [filename]"

I've recently switched from Windows, but I'm slowly getting the hang of Linux.

Thanks for your help![/QUOTE]
Try one of these:
```

$ gpg --clearsign your-filename(s)
$ gpg --symmetric your-filename(s)

```
The first one uses the default key from your keyring to encrypt the file(s).  The second asks you for a passphrase to do the encryption.  I am not a crypto expert, but using the longer and more random generated key may be harder to crack.
The reason your initial syntax didn't work is because you were trying to use public-private key encryption like you would use to send someone encrypted mail.  The "--encrypt" option doesn't take any parameters-- it just specifies a mode.  You would have to specify a user whose public key you had to combine with your private key to create that kind of encryption.

By the way, thanks to dbeckham32.  kgpg *is* really easy to use.

---

### Post by gorkhal on 2005-09-02
try this...feel free to skip any step already covered.

first install 'gnupg' from synaptic or 'apt-get install gnupg'...

now then, you have to create your own key pair first, so run
$gpg --gen-key

it will just ask some questions answer whatever you feel appropriate. 
Note: at one point it will ask you for your passphrase, do not forget this, because if you do, you will be unable to retrieve your encrypted documents.

Then once you have the key pair made, its quite simple to encrypt and decrypt.

#TO ENCRYPT
$gpg -o Encrypted_File.gpg --encrypt -r [email]bob@bob.com[/email] File_to_encrypt.abc

the email address here is the one you entered during the key generation phase.

#TO DECYRPT
$gpg -o Decrypted_File.abc --decrypt Encrypted_File.gpg

there you go, hope it helps.  :smile:

---

