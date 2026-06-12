---
title: "Mounting a new hard drive"
date: 2008-06-23
forum: Desktop Environments
---

### Post by Mecharuva on 2008-06-23
Sorry if I haven't searched hard enough for this.
I recently (finally) got VirtualBox working, which forwarded me to another situation:  my Linux OS is running out of space.
So I booted the LiveCD, went to GPartEd, and took a 100Gb chunk out of my secondary hard drive (/dev/sdb2), made it Primary, and set it to ext3.
I believe I meant to make it ext2...
But it's ext3.  I can change that if need be.
So now it sits, mounted and available on the desktop, named "107.4Gb media".
I want to rename it LinuxSecondary and set it to automount at startup.
I have yet to manage it x.x

---

### Post by linfidel on 2008-06-24
Ext3 is fine, and preferred over Ext2, I think.  All of my partitions are Ext3.

So, if all you want to do is automount it, it's pretty easy.  
1.  Decide where you want it to be mounted in your filesystem.  If it's for data, you might want it to be in your home directory. 
2.  Create a directory where you want it to be, and name the directory whatever you want.  You can name it LinuxSecondary if you want.
3.  Open a terminal, and type:  sudo blkid 
     This will give you the UUID for the partition you want.  Find /dev/sdb2, and copy the
     UUID to the clipboard.
4.  Using a text editor (gedit or gvim, for example), open /etc/fstab, using sudo or gksudo;
     example:  sudo gedit /etc/fstab
5.  Add a line to fstab looking something like this:
#/dev/sdb2 (2nd hard drive, spare partition)
UUID=big-long-uuid-number /home/username/LinuxSecondary ext3  defaults    0    3
The number 3 is just the next number in the list - it may not be 3, that was just a guess.  I don't know that it matters that much.  Put your username for "username", or change the directory to whatever you used for the one your created.

To label the partition (to LinuxSecondary), type  
 sudo e2label /dev/sdb2 LinuxSecondary

To try it out immediately, type
sudo mount -a
This mounts everything in fstab.

Hope this helps a little.

---

### Post by Mecharuva on 2008-06-24
Okay, I almost got it.
Some kind of error with that hard drive, showed up at boot.
Maybe a reboot will fix it; it was working fine after the partitioning yesterday.

---

### Post by Mecharuva on 2008-06-24
Okay, error is gone.
It's still called 107.4Gb Media though?
The e2label command looked like it worked, but didn't.
Or does it require a restart?

---

### Post by Mecharuva on 2008-06-24
x

---

### Post by linfidel on 2008-06-24
> **Mecharuva said:**
> Okay, error is gone.
It's still called 107.4Gb Media though?
The e2label command looked like it worked, but didn't.
Or does it require a restart?
I don't think it requires a restart, but it may need a remount.  

There's another command that will label the partition... 
sudo tune2fs -L newlabel /dev/sdb2


I don't know if making the partition primary affects anything, but it's usually best not to make partitions primary unless necessary.  There's a fairly low limit to the number of primary partitions.

---

