---
title: "intrepid: file server"
date: 2009-01-07
forum: General Help
---

### Post by endacoz on 2009-01-07
I am running intrepid.  I have a 250GB secondary hard drive formated in ntfs.  THis hard drive has files on it that I would like to be able to share over my LAN.  I think that I want to use samba?  Can someone point me in the right direction for setting up such a thing.  Point me to documentation or websites for doing such.  Possibly even

---

### Post by northern lights on 2009-01-07
[https://help.ubuntu.com/community/Samba]("https://help.ubuntu.com/community/Samba")
[https://help.ubuntu.com/8.10/samba-fileserver.html]("https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html")

---

### Post by thedarkwinter on 2009-01-07
Yes, samba is probably the best way to go.

```
sudo apt-get install samba smbfs
```

In intrepid, you can simply right-click on a folder and go to "Sharing options". If you are not using a GUI (server edition) then have a look through the following links:

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

[http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html]("http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html")

cheers,
Michael

---

