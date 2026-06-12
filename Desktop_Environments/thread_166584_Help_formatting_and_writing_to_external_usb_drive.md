---
title: "Help formatting and writing to external usb drive"
date: 2006-04-26
forum: Desktop Environments
---

### Post by BoboChimp on 2006-04-26
I was just given a hard drive that i would like to use as an external drive.  i managed to repartition it on an XP box i have.  I couldn't figure out how to over ride the "read only" settings in Ubuntu.  I brought it back to my Ubuntu machine to format vfat (xp only formats ntfs apparently).  

I'm pretty sure i managed to get the FS on correctly b/c it shows as vfat in Disks Manager.  The problem is that Root is the owner.  I cannot write to the disk as a regular user.  You'd think if you format a disk from inside a user account (albeit, i did have to use my sudo password to access Disks Manager), you would be the owner of it.

I followed the advice in this thread:
[http://www.ubuntuforums.org/showthread.php?t=122523](http://www.ubuntuforums.org/showthread.php?t=122523)

but i must have done something wrong b/c it still shows root as the owner.  

Can anyone help out?

---

### Post by jpkotta on 2006-04-26
Use the "user" option to mount it.  Here's how I have my USB drive in /etc/fstab (I don't use GNOME, so I just mount it by hand).

```
/dev/sdb1       /media/removable  vfat    rw,user,noauto,dmask=077,fmask=177  0      0
```

Alternatively, ```
mount -o user /dev/sdb1 /media/removable
```

Finally, ```
man mount
```

---

### Post by BoboChimp on 2006-04-26
It is working now.  Sad to say that I don't know what I did to fix it.  I unplugged it and plugged it back in and now it works.  But, on a positive note, i found a great informational page that explains the /etc/fstab file very well.  After i finish digesting that, i'll look more closely at your fstab entry and see if it something that makes sense for me.

btw, the page i was referring to is [here]("http://www.tuxfiles.org/linuxhelp/fstab.html") in case you are interested or want to point others to it in the future.

thanks again.

---

