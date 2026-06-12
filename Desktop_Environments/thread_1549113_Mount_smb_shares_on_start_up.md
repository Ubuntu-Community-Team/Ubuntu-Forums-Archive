---
title: "Mount smb shares on start up"
date: 2010-08-09
forum: Desktop Environments
---

### Post by JuanitoMint on 2010-08-09
Hi there, there are some times, in a mixed network, when you need to mount a windows folder (smb mount). i read a lot of posts of doing this via fstab editing, i found a way that does not require you to edit such critical file as the /etc/fstab
3 easy steps

Step 1: you will need smbfs package

```
sudo apt-get install smbfs
```

Step 2: Create a folder under your home directory (so you will have /home/someuser/smb

Step 3: Create a new entry in startup applications preferences, type the title you want, then add this command
```
smbmount //morfeo.local/locales/locales /home/someuser/smb/ -o password=''
```

where: " //morfeo.local/locales/locales " is the name of the machine and folder in you network
this connection have no password (is public acces) ig you need to connect with user and password refer to smbmount parameters
[IMG]http://www.webexperts.com.ar/ubuntu/Startup2.png[/IMG]

[IMG]http://www.webexperts.com.ar/ubuntu/Startup1.png[/IMG]

---

