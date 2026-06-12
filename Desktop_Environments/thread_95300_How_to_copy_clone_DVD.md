---
title: "How to copy/ clone DVD"
date: 2005-11-26
forum: Desktop Environments
---

### Post by topic58 on 2005-11-26
Hi all, anyone who knows a simple way to copy/ clone a DVD. I sometimes record from teve/ Camcorder into a DVD-RW from my DVD-recorder and i want to copy/ clone this program into a DVD-R on my pc. Have tried dvdcopy, but my DVD-recorder can't read it. I can see the movie in VLC (.vob) but not in Totem (missing titel). Any good suggestions here?

---

### Post by akiro.yamamoto on 2005-11-26
Now this may seem a little extravagant but if you want to do DVD copying I'd try 
DVD Decrypter in wine..
That works for me. It's a free solution....
Check out this website for full details....:

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

Regards
:smile:

---

### Post by topic58 on 2005-11-26
When using dvdbackup I type: dvdbackup -i /dev/dvd -o /home/myuser/directory/mydvd -M

VIDEO_TS is complete but no VIDEO_RM in that directory. So I simply add VIDEO_RM from the DVD-RW. Maybe that is too simple/ wrong? Should maybe VIDEO_RM be empty?

---

### Post by speedman on 2005-11-26
Have a look here:

[http://dvdshrink.sourceforge.net/index.html](http://dvdshrink.sourceforge.net/index.html)


Regards,

SM

---

### Post by artinla on 2005-11-26
xdvdshink.. works great for me anyway.  Easy to use and there are good instructions:

[http://ubuntuforums.org/showthread.php?t=92198&highlight=dvdshrink](http://ubuntuforums.org/showthread.php?t=92198&highlight=dvdshrink)

---

### Post by liontooth on 2005-11-26
You can also use k3b and select "copy to iso".

Incidentally, if you rip to iso, you can either mount the iso and access the individual files that way (if you don't just want to burn it to disk):

    mkdir loop
    mount -o loop -t iso9660 *.iso loop

or, if it's a video DVD, you can play the iso directly, without mounting it:

    xine dvd:/full-path/file.iso

Note you need the full path. It will play the iso as though you had a DVD in a drive.

Dave

---

### Post by topic58 on 2005-11-26
Okay. I have tried to make an .ISO by using Nautilus. Works fine for me. Works in both my DVD-recorder and my pc. Will try DVDbackup later some more. Thanks. :)

---

