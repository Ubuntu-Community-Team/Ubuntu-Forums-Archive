---
title: "File System is Corrupt-Cant Acces Root Files"
date: 2006-12-31
forum: Desktop Environments
---

### Post by dontgetshocked on 2006-12-31
I cant access any root files either from user or as root. They simply do not show up, no errors.
Below is what shows in the terminal box after using sudo nautilus

Any suggestions?



(nautilus:26388): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:26388): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

---

### Post by meng on 2006-12-31
These messages are normal! What files are you trying to access, where are they located? I'm wondering if you may be looking in the wrong place!

---

### Post by dontgetshocked on 2006-12-31
Normally I can use termail with sudo nautilus and password to look at and change the folders below root, i.e. Sounds, etc... Now, I cant even see any folders or files belwo the root folder either as user or root

---

### Post by taurus on 2006-12-31
Please try to use gksudo when you run a GUI app!!!

```
gksudo nautilus
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dontgetshocked on 2006-12-31
No Luck with this either

---

### Post by meng on 2006-12-31
Are you sure these files you are looking for are in /root and not in /

---

