---
title: "How can I backup my files?"
date: 2006-08-01
forum: Desktop Environments
---

### Post by iOsiris on 2006-08-01
Hi,
   Just today, my Windows XP completely died.  So I decided to download Kubuntu LIVE and to see if I can recover my files.  And for the most part I've recovered all of the smaller files by mounting the ntfs partitions, and then copying some files over on my 1GB flash drive.  However, there are a lot more other files I want to get off my HD but are much bigger than 1GB.  What would be the best way of getting them off?  At first I wanted to burn the files, but this doesn't seem to be the option as I can't take the LIVE DVD out.

   Is it possible to setup a network between a Windows XP Laptop & Kubuntu LIVE?  Or could someone explain to me how to setup a portable FTP in Linux?  Or any other suggestions would be greatly appreciated!  (At the moment, I'm on the laptop)

---

### Post by daller on 2006-08-01
You could install proftpd?

Well, now that I have an external DVD-burner, that would be my personal favourite! (Or an external HDD (maybe without drive, and then put the harddisk in it, and connect it to another pc!) would be just as neat!)

An external case is about $50 AFAIK!

Maybe look into the wiki?:

[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

---

### Post by ardchoille on 2006-08-01
Here is the backup strategy I use:

1. sudo mkdir /home/backups
2. sudo chown user:user /home/backups
3. cd /home
4. tar cjf /home/backups/$(date +%Y%m%d)-backups.tar.bz2 username
(where username is your user account)

That's it. The backups will be found in /home/backups with the date in the filename, ex:

/home/backups/20060801-backups.tar.bz2

This way, you can write a script with the tar command in it and run it as a daily cronjob. You can copy the backups to CD/DVD at your convenience or use rsync to upload them to another computer.

---

