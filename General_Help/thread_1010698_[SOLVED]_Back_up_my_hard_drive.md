---
title: "[SOLVED] Back up my hard drive?"
date: 2008-12-14
forum: General Help
---

### Post by jakenbake42 on 2008-12-14
Hi, I'm running Ubuntu 8.10, and I have a good 50 GB external usb harddrive that I can leave always plugged into my machine. So my question is, is there a program that can automatically [like weekly, monthly?] backup my hard drive? Something easy as possible to use. And this is a bit much but is there one that could even wake up my computer in the middle of the night, back up the hard drive, and then turn it off when the process is done?
Thanks much in advance

---

### Post by grappler on 2008-12-14
I'm trying to decide which of the many backup systems available for linux (as usual the problem with linux is the amount of choice available) so I've been reading around a bit. One issue is whether you want to have snapshots or not. This permits several backups to be kept simultaneously with (usually) hard links to save space. 

As to doing this in the middle of the night, you can just run a cron script. 

Here are a few possibilities:
[COLOR="black"]
Timevault[/COLOR] 
> [https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault) - probably a good choice for your particular situation


[COLOR="black"]
Flyback[/COLOR]
> [http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10](http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10)

[COLOR="black"]
Sbackup[/COLOR]
> [http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

Also read this:

> [http://tombuntu.com/index.php/2008/11/18/a-guide-to-system-backup-and-restore-in-ubuntu/](http://tombuntu.com/index.php/2008/11/18/a-guide-to-system-backup-and-restore-in-ubuntu/)


---

### Post by hyper_ch on 2008-12-14
rsync :)

---

### Post by jakenbake42 on 2008-12-14
o, thank you guys so much!
So i'm going to try it using sbackup
do you guys know if its possible in the program or just in ubuntu to have my computer turn it self on at a set time?

---

### Post by grappler on 2008-12-20
Sorry for the delay in answering.

There's a bit of a discussion here

[http://ubuntuforums.org/showthread.php?t=1014650&highlight=automatic+boot](http://ubuntuforums.org/showthread.php?t=1014650&highlight=automatic+boot)

about automatic booting. I have never tried that so don't know how to do it.  

After that you just need to set cron to run the backup package. You can do the latter using "scheduled tasks" from the menu. You have to make sure gnome-schedule is installed - use synaptic.

---

### Post by jospan on 2008-12-20
Look at your BIOS settings - often you will have an option to schedule a power up.

---

### Post by linux_tech on 2008-12-20
I think it would be easiest to use rsync in a bash script or set up a cron job to have it run automatically as explained here [http://linuxbasement.com/content/backups-using-rsync-bash-cron](http://linuxbasement.com/content/backups-using-rsync-bash-cron)

---

