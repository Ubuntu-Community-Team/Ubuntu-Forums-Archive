---
title: "ubuntu enterprise or server edition"
date: 2005-08-20
forum: Desktop Environments
---

### Post by dbrine on 2005-08-20
I want to dump my win 03 server for a linux server install. I am, for the most part, a newbie. But I need to share HDD's, webserver, ftp, etc. Is there a preferred flavor of linux to do all this easily? I must admint I use windows but am trying to switch to linux to completely  but like the GUI easy to use windows as well. any help would be great. I also want to host my own e-mail and I have dyndns if it matters.

---

### Post by Reb on 2005-08-20
You can use Ubuntu as a server pretty easily.  
Firstly, how much do you know about apache and setting up a simple static website (if any  ;-))?

---

### Post by dbrine on 2005-08-20
nothing about apache at all. I used IIS on win and frontpage but nothing in linux

---

### Post by Velox Letum on 2005-08-20
There are several guides you can use to assist your setup of Apache on Linux. You can also mount your NTFS partition as read-only into Ubuntu and copy over all your website data, OR you can make a FAT32 partition in between that both Windows and Linux can read/write to, and store your web data there if you must use IIS and Apache.

In my honest opinion, IIS is a walking security breach.

---

### Post by dbrine on 2005-08-21
Do you need to convert my NTFS drive to fat32 in linux to work and share correctly? I have mulitple hdd using ntfs

---

### Post by Velox Letum on 2005-08-21
You can read NTFS easily from Linux...however writing is somewhat...finnicky. When I partitioned my Ubuntu drive I left a small, 1gb partition for both Windows and Linux to share, though both can read each other's filesystems (by mounting with Linux, by a program like Explore2fs. However if I wanted a webroot to be shared for example (not just read, but written as well) I'd make it on the FAT32 partition. But no, you don't need to convert to FAT32 and I'd suggest you don't.

---

