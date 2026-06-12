---
title: "Lost file system icons after update"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by charliejamesuk on 2007-06-03
Hi,

I recently update kernel to version 2.6.20-16-386 and on rebooting I noticed that I have lost some icons from my desktop which were automatically created for me.

They were pictures of hard drives (or something) and they were auto created when I added some samba mounts to my /etc/fstab file. The file systems are still mounted as I can browse them from Nautilus, I just like the icon access provided on the desktop.

Any ideas how I can get them returned??

Many Thanks
Charlie

---

### Post by syväpaahto on 2007-06-03
I have a similar problem. After the last updates(2007.06.01) and installing sshfs+fuse, Optical drives(ata) disappeared from nautilus and mounted disks no longer appear on desktop. Automount and browsing do still work, but I have to unmount from terminal(since no icons). System logs don't show any errors, and fstab is ok. I have no idea where to start...

---

### Post by charliejamesuk on 2007-06-04
Lets hope someone reads this who does then ;)
Out of interest, does Ubuntu use something other than /etc/fstab? As if I remove a mount point and run mount -a the file system is still mounted??

---

### Post by syväpaahto on 2007-06-09
I noticed that too. fstab is impotent :(

---

### Post by charliejamesuk on 2007-06-14
I found how to make the filesystem icons re-appear on the Desktop.
Mount all filesystems in /Media and reboot, the icons will now appear on your desktop again. 
Guess a change was made in the kernel upgrade??

---

### Post by KwikSilvr on 2008-03-21
Uhh I actually lost the picts of the ICON, its annoying I kno, I mean the Icon is there but the pic representing the Icon has vanished!! Can any1 help me?

---

