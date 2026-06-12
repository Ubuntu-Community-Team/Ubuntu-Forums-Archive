---
title: "DVD-RW and CD-RW"
date: 2005-05-05
forum: Desktop Environments
---

### Post by Calgarian on 2005-05-05
I am brand new to Kubunto/Ubunto having just switched from SuSE an hour ago (9.3 problems made me really mad). I think I'm going to like this distro a lot. I'm not a Linux techie, I'm a user so "it just works" is a priority for me. Now a couple of questions:

1. I backed up (like a smart guy) all my files to DVD-RW before the install. However, the install does not recognize my devices. I have both a DVD-RW and a CD-RW. I looked in fstab (and now realize I need to the right click thing to edit as root), and got a bit scared about making changes. I was going to put:

/dev/dvdrw      /media/dvd      auto      ro,user,auto 0 0
/dev/cdrw        /media/cd        auto      ro,user,auto 0 0

does that look correct? There are also entries for:

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

that I thought I would remove. I would like these devices to automount when I put media in and umount when I close the /media folder.

2. I have a real problem with very weak fonts and a bad set of display colours? The fonts look very thin and the display colours are washed out. I can hardly see the lines around group boxes in screens. I did the font thing in the Control center and tried adjusting colours to no avail. I think I have a learning curve to climb here, but I'm looking forward to it.

TIA

---

### Post by Calgarian on 2005-05-05
Just got the problem with fonts and colours fixed. It was settings in my LCD menu that had been done for SuSE. Did an autocinfig on the screen and it's great. Now I know I love this distro for sure.

---

### Post by Calgarian on 2005-05-07
Using the System Icon and then the Storage Media section I can get my devices to work. Haven't tried writing yet. I guess that's part of a learning curve for a new approach. However, they seem really slow. Can I do anything to get them back to speed?

---

### Post by Takis on 2005-05-07
[QUOTE=Calgarian]I was going to put:

/dev/dvdrw      /media/dvd      auto      ro,user,auto 0 0
/dev/cdrw        /media/cd        auto      ro,user,auto 0 0

does that look correct? There are also entries for:

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

that I thought I would remove. I would like these devices to automount when I put media in and umount when I close the /media folder.[/QUOTE]

Heh dude it's found the devices no problem. You don't need to (and shouldn't) edit your fstab for this issue. 
> I would like these devices to automount when I put media in and umount when I close the /media folder.
This sounds excessively difficult to implement, and not particularly useful. I think you'll find as you use Linux more and more that you'll be doing a lot of terminal work (when you learn it, it's easier, faster and more powerful) and significantly less from Konqueror. If you umount your disk drives whenever you close konqueror, it'll be a real PITA to remount them whenever another program (game, media player) tries to access them. I find the Storage Media applet is pretty useful.

Now when you complain they're slow, do you mean the mounting takes a little bit to complete (as it will, you can't *really* help that), or that the drives are slow transferring data? If it's the latter, you might want to have a look at your dma settings.
[http://www.ubuntuforums.org/showthread.php?t=30949](http://www.ubuntuforums.org/showthread.php?t=30949)

---

