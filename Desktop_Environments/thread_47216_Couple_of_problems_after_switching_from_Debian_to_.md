---
title: "Couple of problems after switching from Debian to Ubuntu"
date: 2005-07-07
forum: Desktop Environments
---

### Post by fannymites on 2005-07-07
I'm very new to Ubuntu - a couple of days.  I've just switched from Debian SID which I used on and off for the past few months and I still consider myself very much a beginner.
So far everything has gone very well with Ubuntu but I do have a few niggling minor problems I hope someone can help me with - I have already had a couple of them fixed in another thread on this forum so here goes with the 2 remaining ones.

I have a shared partition which I use for sharing files between my Linux and Windows, I also use this partition for my shared firefox bookmarks file and my firefox profile.  For some reason I am unable to find a way to allow write access to this partition as a regular user but I can as root.  After searching around I've found a few suggestions on how to allow user write access but nothing seems to work.  
It was working fine in Debian straight from the install.

The other problem - I have a BT Voyager 105 usb broadband modem.  In Debian I had the modem set to connect as Linux was booting up so once I had logged into KDE/Gnome/XFCE it had finished synching and was ready to go.  In Ubuntu I just can't get it to connect on startup so I have to manually start it which takes quite a while.

This is how it worked in Debian - 
I created a shell script file - /etc/rc.d/rc.local which contained the command to start the modem.
I then symlinked this file to /etc/rc3.d/S99modemstart and /etc/rc5.d/S99/modemstart

Does anyone have any idea where I may be going wrong?

---

### Post by drummer on 2005-07-07
For the shared partition (I'm guessing it's fat32?) you can force it to mount with rw permissions in fstab. I have a secondary hard drive (fat32) for just that purpose and mount it automatically in fstab with the option umask=0000 to give full read/write access. The whole line in /etc/fstab looks like this: ```
/dev/hdc1       /media/share    vfat    defaults,umask=0000        0       0
``` the umask option subtracts values from the permissions, but as I don't really know how octal works I just set it to '0000' to get the permissions '777' (full access to all users).

---

### Post by fannymites on 2005-07-07
I tried your suggestion but now I can't even read from the drive -  I get this error - 
"only root can mount /dev/hda2 on /media/hda2"

---

### Post by drummer on 2005-07-07
Is that when booting or when issuing the mount command? only root can use the mount <drive> command from the terminal (i think because fstab and mtab are in root owned directories) so do a ```
sudo mount -a
``` to update the changes in fstab, or reboot and it should work. Even though root mounts the drive and it's the owner, everyone else can read/write as the drive permissions are 777.

---

### Post by fannymites on 2005-07-07
It worked after changing the mount point from /media/hda2 to mnt/hda2.

Now, if I can just sort out the modem on startup problem I will have a completely, everything working Linux setup for the first time ever.

---

### Post by drummer on 2005-07-07
I'm glad it's worked out, but I wonder why mounting in /media didn't work  :?  ..as for the shell script, all I can suggest is making sure that the script is executable, otherwise I think it will be ignored. ```
sudo chmod +x <script>
```Otherwise I don't know much about startup scripts.

---

### Post by fannymites on 2005-07-07
I can't work out why it works with /mnt and not /media but it works and that's all that matters.
Regarding the modem, the command to start it has to be run as root.  After adding a nopasswd rule to sudoers for that start command, it now starts up as linux is booting.  I did have that entry in sudoers when I used Debian but I had forgotten about it.
Woohoo!  Everything is working like a dream now.  Ubuntu rocks.

---

