---
title: "Webdav in KDE broken?"
date: 2005-10-01
forum: Desktop Environments
---

### Post by Bolverk on 2005-10-01
I have access to a webdav server for use in file transfer (and more importantly) backups. In KDE 3.4 it worked. In KDE 3.4.2 and 3.5beta1 I can no longer access the webdav server. I know it's KDE because I can still access the server through Nautilus and other mechanisms. Konqueror just can't do it, either through the webdav:// protocol or through setting up a network location. Anyone else had this problem? Anyone have a solution?

---

### Post by mlomker on 2005-10-02
I just confirmed that webdav works in both versions.  My webdav server is just a webserver with a test page on it, but it does work.

---

### Post by Bolverk on 2005-10-03
Is your server running through a secure connection? The webdav server I'm trying to access is a secure server that is not under my control. Neither myself nor the other individual here (running KDE 3.4.2) can access the server via KDE. Gnome and Windows have no problems accessing the server, which is why we're assuming that KDE's webdav access is broken. 

The error we're getting is:

> The file or folder webdav://XXXXX@webdisk.XXX.XXX:80/XXXXX does not exist.

---

### Post by mlomker on 2005-10-03
[QUOTE=Bolverk]Is your server running through a secure connection?[/QUOTE]

No.  It is on my local network.  I'm not aware of any servers that I can connect to as a test, otherwise I'd try it for you.

---

