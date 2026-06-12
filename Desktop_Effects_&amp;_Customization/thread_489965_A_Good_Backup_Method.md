---
title: "A Good Backup Method"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by ubonetu on 2007-07-01
Hi!

I've had trouble with the backup software in Ubuntu and remembered an old method posted here to backup your  Ubuntu system.  All you have to do is add this to your /etc/crontab file as root and fix the directories to match your system:

```
## Ward's Super Backup Genious of the Gods ;-)
00 12	* * *   root    tar -cjpsf /media/sda3/backupDay2.tgz --exclude=/media --exclude=/proc --exclude=/tmp --exclude=/var /  
```

To re-create your drive, just untar the file (you should all know how to do that by now, if not:```
tar -xzvf <filename>
``` to your newly wiped and reformatted drive, you can use DSL (Damn Small Linux) as a temp os for reformatting and untarring the file to your drive.  Then just add the directories, empty, where we excluded them, again DSL for the install-grub:

```
install-grub or install_grub  /dev/hda (or whatever drive:  /dev/sda etc)
```

follow the grub directions (I install to the master boot record) and reboot.

Anyway, anybody who's really lost it might appreciate this.  Please feel free to add if I've screwed anything up.

Hope this helps somebody (and I don't ever find myself looking this up from DSL),
Ward

p.s.  You can do really cool thing with the "date" command, like make the filename:
```
tar -czvf /media/sda3/`date +%m-%d-%Y`.tgz
```
I'd do this but I have very little drive space (shut up, I'm an old Maccie and all my stuff's Firewire).

---

### Post by ubonetu on 2007-07-02
I don't think this will work.  So much for my contribution.  I'll have to put some effort into simple-backup this time :-|

Peace,
ubonetu

---

