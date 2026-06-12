---
title: "Understanding fstab"
date: 2009-05-26
forum: General Help
---

### Post by CaptainMark on 2009-05-26
Okay Im new to Ubuntu but Im quickly trying to get my head round everything, but I cant figure this one out. I have a partition /dev/sdb1 which I want to mount in my mount point /mnt/usb
So Ive used sudo to mount the drive but I cant get the permissions to read and write apparently due to the fact that its formatted as FAT32. After trawling through google pages I know to automatically mount it I have to add it to my fstab files, which now reads

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sdb1 /mnt/usb vfat defaults,user,exec,uid=999,gid=999,umask=000 0 2

The drive mounts but again it wont give me read write permissions.  What am I doing wrong??
Any help would be appreciated, Im pulling my hair out.

---

### Post by cariboo on 2009-05-26
You may want to change your fstab entry to something like this:

```
/dev/sdb1 /mnt/usb vfat relatime  0	2
```

Then change the permissions of the mount point.

```
sudo chmod -R 777 /mnt/usb
```

This will change the permissions to world read/write.

---

### Post by CaptainMark on 2009-05-26
Tried this, it hasnt helped, again the drive mounts but not writable

---

### Post by Diabolis on 2009-05-26
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[http://baboontu.blogspot.com/2009/05/montar-particiones.html](http://baboontu.blogspot.com/2009/05/montar-particiones.html)

---

### Post by CaptainMark on 2009-05-26
Thanks for these links they helped me understand some of the options a bit better, but still no luck, its driving me crazy. Ive got this entry in my fstab file

/dev/sdb1 /mnt/usb vfat noauto,user,exec,rw,sync 0 2

if I understand it all correctly typing ```
sudo mount /dev/sdb1
``` should mount /dev/sdb1 into /mnt/usb with full read and write permissions.  Someone help, what on earth have I done wrong.

---

### Post by CaptainMark on 2009-05-26
Okay Im ready to rip my own head off now. 
The thing that gets me is that im running a live session from a usb and trying to access the actual files on the usb whilst still running a live session from it, normaly I would think im just asking the impossible but Ive done this before I know it can be done. I was doing it up until yesterday when my usb died and needed reformatting. 

Maybe Im just going round the long way, lets go back a step.  Is there a way to have Ubuntu bootable from USB and be able to create and access files that you can also access from a Windows machine just by clicking on the USB stick in my computer??
Help me, my sreens about to go flying out the window

---

### Post by Diabolis on 2009-05-26
So you want to have access to the files in your **boot-able USB** from Windows?

I've never used one of those, but I'm almost sure that a USB of that kind is formatted with a ext2/3/4 file system, so you'll need a special tool for that. Something like fs-driver.

Which is the problem that you encounter when you mount your partition? You don't have read/write permissions? If so, just change the permissions of the folder, the mount point, with the **chmod** command.

If permissions are right (644 by default) just change the ownership of the folder with this command:
```
chown USERNAME:USERNAME
```
That means that the folder is owned by USERNAME and its in the group USERNAME.

---

### Post by CaptainMark on 2009-05-26
Not so easy im afraid, a bootable usb made by ubuntu formats to fat32, i can read files fine from a windows pc but i cant put them there in the first place because while im running a live session from the usb it wont let me write straight to it.  It lets me write files to the live sessions' document folder, but then i cant access these files from any other computer. Id have to take the usb to another computer turn it off, boot from usb in live session, plonk the files to the windows drive, then reboot the pc in windows to access the files, way too long winded. I know this is possible as ive done it before. I think making two partitions on the same usb might save my sanity.

---

### Post by Iowan on 2009-05-26
[Here]("http://ubuntuforums.org/showthread.php?&t=283131") is another How-To that may/not be helpful.

---

