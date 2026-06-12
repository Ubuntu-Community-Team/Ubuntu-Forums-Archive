---
title: "Network-Manager-Gnome has memory loss!!"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Hellcom on 2006-07-01
Newb here

I've starting using network-manager-gnome at the recommendation of: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

It works great and connects to my WPA network without any hassle, but it never remembers my encryption or pass phrase (tried WEP). Every time I log on it requests that I input the encryption or pass phrase even though I have already done that.

I think the reason why this occurs is shown in the screenshot below. 

[IMG]http://img.photobucket.com/albums/v608/Hellcom/90916f43.jpg[/IMG]

After I input my encryption or pass phrase it requests a password. The reason for I don't know, so I have clicked deny each time. Will entering a password fix the issue, and will I have to enter that password at each logon? The wiki, support pages, network manager's own site, and all other sources I could think of don't have any help or support information.

---

### Post by plexi50 on 2006-07-01
Yes, the keyring will store your password/SSID. Once you enter a keyring password, you will only be prompted to enter that password to connect.

---

