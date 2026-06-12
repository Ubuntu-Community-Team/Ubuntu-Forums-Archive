---
title: "Connect to FTP server first deletes all old files, then copies new"
date: 2006-12-02
forum: Desktop Environments
---

### Post by radiobuzzer on 2006-12-02
Hi. I have a website on an FTP server. I used the  (gnome) Locations > Connect to server menu to connect to my server as FTP, then I copied and pasted all the new files in the folder of the old ones. They were 198 files all to be replaced by their new versions.

It asked me: Files exist. Replace them? I selected yes to all...

And then. The stupid, look at what it did: It deleted all the old files first, while preparing the transfer, and AFTERWARDS started putting the new version of theirs. The result was that the site was more or less down for two hours and about two hundred of visitors got a file not found error (it is a popular site).

It think it stupid, really. Has anybody had the same problem? If it is confirmed, it should definitely be reported as an issue to be fixed.

---

### Post by paparucino on 2006-12-02
> **radiobuzzer said:**
> 

It think it stupid, really. Has anybody had the same problem? If it is confirmed, it should definitely be reported as an issue to be fixed.
Why don't you use gftp? It, like all other ftp-tools, don't has that problem.
But.... I haven't understand how do you connect to your ftp server

---

### Post by radiobuzzer on 2006-12-03
Gnome menu: Places > Connect to server...

---

### Post by lhtown on 2006-12-09
It would be great if you would file a bug report with the gnome developers. 

This appears to be one of those things that doesn't affect that many people, but is still very important for the overall usefulness and reliability of the system.

---

