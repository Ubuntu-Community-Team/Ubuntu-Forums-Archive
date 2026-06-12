---
title: "disk filling up"
date: 2009-02-09
forum: General Help
---

### Post by inTrouble on 2009-02-09
Hi all,
I have a slight problem with my hard drive filling up and I don't know what is causing it. I looked at some other posts and found that I have some fairly large files (>1 Gb) in /var/archives but have no clue what they are or how they got there. I'm new to Ubuntu and Linux, so please be patient with me. Is there a way to check what programs created those files? How can I delete them? What else can fill up my hard drive? I cleaned out a bunch of files last week and haven't used my computer since. Now the disk is full again :confused:.Please help. Thanks.

---

### Post by davideotape on 2009-02-09
Try typing ```
sudo apt-get autoclean
``` into a terminal. This gets rid of all the partially downloaded program files that you don't need any more.

---

### Post by inTrouble on 2009-02-09
I tried autoclean. Something is writing data to the hard drive and fills it up.

---

### Post by inTrouble on 2009-02-09
ok, I was checking thru the different log files and found entries for a backup-manager. Looking at the backup-manager config file I noticed a line refering to /var/archives. I deleted the backups and uninstalled the program. Hope this is it.

---

### Post by mb_webguy on 2009-02-09
Run the Disk Usage Analyser from Applications->Accessories.  (Personally, I prefer kdirstat's graphical display to baobab's, if you want to install it.)  It should be fairly easy to track down what's using up your disk space.

---

