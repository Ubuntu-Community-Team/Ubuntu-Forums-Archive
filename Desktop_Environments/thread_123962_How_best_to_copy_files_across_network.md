---
title: "How best to copy files across network?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by stig on 2006-01-31
Hi,
I have two Ubuntu computers networked and I want to back up the files from each onto the other.

I have done this on a Windows network by using the context (right click) menu and the "Send to" function. It sends a copy of the files to a shared folder of my choice on the other computer.

On Ubuntu, when I right click and choose "Send to" it only offers me Evolution email. I don't want to back up by email over the Internet. How do I change the "Send to" so that it targets a shared folder on the other computer?

Or is there a different way of doing the job on Ubuntu?

Thanks!

---

### Post by joselin on 2006-01-31
The best way is to shared files through NFS.

Check this link:
[https://wiki.ubuntu.com/SettingUpNFSHowTo]("https://wiki.ubuntu.com/SettingUpNFSHowTo")

---

### Post by jshein on 2006-01-31
If what you are trying to acheive is a reliable backup system on 2 PCs then take a look at using rsync and cron.

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

The best way to acheive this is to create a seperate drive, partition or  directory on each computer, let say named "backups".

You will rsync the items on PC-A to the "backups" location on PC-B and rsync the items on PC-B to the "backups" location on PC-A.

---

### Post by stig on 2006-01-31
I've got no problems sharing files - I do that with Nautilus-Share. What I want is to be able to copy files from one PC to a shared folder on the other PC, like I do on Windows with the "Send To" function.

I can drag copies of files from one to the other but then the copies of simple text files won't open when I click them - I get a warning saying they are executable text files (which the originals were not) and aksing me if I want to run or display them.

---

### Post by stig on 2006-01-31
Thanks jshein, I'll take a look at rsync and cron.

---

### Post by joselin on 2006-02-01
Other option for backup porposals like rsync is unison.

[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/~bcpierce/unison/")

---

### Post by stig on 2006-02-02
[QUOTE=joselin]Other option for backup porposals like rsync is unison.

[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/~bcpierce/unison/")[/QUOTE]

Thanks - this looks interesting, it is in the Ubuntu repository, and it has a GUI option too.
:)

---

