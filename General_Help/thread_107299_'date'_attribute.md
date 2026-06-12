---
title: "'date' attribute"
date: 2005-12-22
forum: General Help
---

### Post by ercork on 2005-12-22
I've been searching the forum and google for help on this problem but haven't found a single reference to it. Whenever I copy files from an external USB drive to my laptop (running Ubuntu 5.10) the 'date modified' attribute gets overwritten to the current time and date. For me, this is a very important piece of data that I want to hang on to. I've never seen this happen either in Windows or in several other linux distros that I've tried. Any body got any ideas as to how I could prevent the copying process from destroying the date modified attribute?

---

### Post by ape on 2005-12-22
try using the "-p" argument to the cp command.  From the 'cp' man page:

 [FONT="Courier New"]-p     same as --preserve=mode,ownership,timestamps

 --preserve[=ATTR_LIST]
              preserve   the   specified   attributes   (default:  mode,owner-
              ship,timestamps), if possible additional attributes: links, all[/FONT]

---

### Post by ercork on 2005-12-23
Thanks for the help ape. I tried your suggestion but got an 'Operation not permitted' message. However, when I added sudo, it worked fine. Not being too command line savy I'd rather be able to copy files using the gui. The location I'm copying to is a FAT32 partition mounted at /media/hda4/. It says in the permissions dialog when you do right click / properties that the folder (and all subfiles) are owned by root. I tried to change ownership with:
sudo chown t22.t22 /media/hda4/*
but again got the 'Operation not permitted' message. Am I doing it the wrong way?
(By the way, t22 is my username)

---

### Post by ape on 2005-12-23
so I see two possible issues:

1. The proper syntax of chwon is <userid>:<groupid> using the colon and not the period.

2. What are the permissions on the mount point '/media/hd4'?  

    Is this FAT32 partition automounted at boot time?  If so, what does the relevant line in the /etc/fstab file look like?

---

### Post by ercork on 2005-12-28
I tried the chown command again with the proper syntax that you suggested but got the same 'Operation not permitted' message. The FAT32 partition is automounted at boot and the relevant fstab line is:

/dev/hda4       /media/hda4     vfat	umask=000	0	0

The parmissions on '/media/hda4' allow read and write for everbody but the owner is root.

---

### Post by ape on 2005-12-28
ercork,

  The files are showing up as owned by root as the drive is automounted at boot time by root.  Try the following:

  1. Using sudo, umount /media/hd4.
 
  2. As t22, see if you can mount /media/hd4.  If not, try adding the 'user' argument in the /etc/fstab line for hd4 (using sudo), then try remounting the drive as user t22.

  3. If the mounting is successful, see which user the files are owned by.

Let me know.

---

### Post by Refrozen on 2005-12-28
If you just want to change the timestamps, look up the [touch -d](http://manlib.com/man/225) command.

---

### Post by ercork on 2005-12-28
I did as you suggested ape and I was able to mount the partition without using 'sudo' after I added the 'user' argument. Now the files are owned by 't22' and the timestamps are preserved when I copy from external media. Of course, when I restart the computer it goes back to the old way where everything is owned by 'root'. Any way I can prevent that?

Refrozen, I tried your sugestion too and it's a very handy way of altering timestamps manually. I can repair  a lot of my old ones now. Thanks for that.

---

### Post by ape on 2005-12-29
From the man page for mount, it looks as though you should be able to pass the the following args in your fstab line for this device:

   uid=t22, gid=<t22's gid>

This should put the ownership of all files on that drive to t22.  These would go along with your umask= entry.

---

### Post by ercork on 2005-12-30
Great stuff - the 'uid' and 'gid' arguments did the trick. I left out the 'umask' altogether and went with 'defaults' and now everything's perfect.
Thanks again for the help.

---

