---
title: "Encryption"
date: 2024-01-21
forum: Desktop Environments
---

### Post by mike010 on 2024-01-21
I know Ubuntu uses Luks for full disk encryption but to encrypt any other file or disk like a usb drive you are on your own so i looked into this and have a few choices and a lot of questions to ask. !st Veracrypt seems  to be about the best 3rd party encryption tool out there it does AES and everything there is also AES crypt that looks really good to me as well and it's a lot smaller but there's not much info on it. 

Questions.
Has anyone used AES crypt?
Can it encrypt a usb drive or is it just for files?
Between Veracrypt and AES crypt what would be the best to use?

---

### Post by #&amp;thj^% on 2024-01-21
I use it with my VPN's and other related applications.
Dont know if you have read this yet? [https://proprivacy.com/guides/aes-encryption](https://proprivacy.com/guides/aes-encryption)

Others here may use something different, but I like and use the gpg command for like, folders and usb drives
a quick example for one i
```
gpg --cipher-algo AES256 --symmetric filename.tar.gz
```

This will ask for a passphrase.
```
gpg --cipher-algo AES256 -c filename.tar.gz
```
Decrypt:

```
gpg --output filename.tar.gz --decrypt filename.tar.gz.gpg
```

Plenty of choices on how deep you can go as well
I recommend aes 256 in CBC mode. These are the ciphers modes you have available (only counting AES):

```
aes-128-cbc &#8592; this is okay
aes-128-ecb
aes-192-cbc
aes-192-ecb
aes-256-cbc &#8592; this is recommended
aes-256-ecb

```

Lots of information on the Web about all this.

---

### Post by Holger_Gehrke on 2024-01-22
You do know that you can use LUKS for removable media, don't you ? If you use gnome-disks to partition and format a removable medium you get the option to set up LUKS on it. When you connect such a device the automounter (udisk2) is smart enough to recognize a LUKS container and ask for the password. If you don't mind the command line, then 'cryptsetup' and loop devices even allow you to have containers in files which you can (manually) mount into directories to have encrypted directories using LUKS.

Holger

---

