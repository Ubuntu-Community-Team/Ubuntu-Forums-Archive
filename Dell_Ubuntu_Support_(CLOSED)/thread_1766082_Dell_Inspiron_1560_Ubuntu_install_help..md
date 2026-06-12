---
title: "Dell Inspiron 1560 Ubuntu install help."
date: 2011-05-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Negrumir on 2011-05-23
I don't know if this should go in another forum so if it does, well I screwed up.

This is my first time installing Ubuntu in such a manner so I need a bit of help.

First, the simple details.
I downloaded Ubuntu 11.04 (the latest one) from the site. It's for 64bit as I have a 64 bit system.

I'm currently running Windows 7 64bit.

I don't know if this is the right way to do this but...

I want to run both, Windows 7 by default, and Ubuntu when I want to. I've a 500GB hard drive on which I created a 100GB partition for Ubuntu. Anyway, I burned the ISO and installed from the disk to the new partition (after having to format it/set it up for Ubuntu) Anyway, after I installed I had to restart (obviously) and Windows 7 came back up as expected.

Now what I can't figure out. How do I boot to Ubuntu? Obviously, Windows can't see the Ext3 partition but I also can't select it from any boot options. (via F12 at startup)

So, what did I do wrong? Do I need to reinstall using some other method? 
Remember, I want to keep Windows 7 as the main OS (for now at least, he he he) and be able to boot to Ubuntu whenever.

Thanks in advance, I searched around, but it seems most people have more sophisticated and advanced problems so I found nothing on what I needed. This also leads me to believe that I've done something really stupid as no one else seems to share my problem. lol

---

### Post by garvinrick4 on 2011-05-23
#Put in your install Cd and use Try Ubuntu when it boots up open a terminal ctr/alt/t
and copy and paste this:
```
sudo fdisk -l
``` (lower case L)
Does is have a Linux in there?
Let us see. Copy and paste to this thread.
#You can also hold down shift key while booting to see if grub2 is installed will come up
with menu entry's.
#Maybe Ubuntu is there but no grub2 to boot with?

---

### Post by Negrumir on 2011-05-23
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea1be7a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
/dev/sda2   *          13        1288    10240000    7  HPFS/NTFS
/dev/sda3            1288       48053   375641088    7  HPFS/NTFS
/dev/sda4           48053       60802   102400001    5  Extended
/dev/sda5           48053       60802   102400000   83  Linux
ubuntu@ubuntu:~$ 


Okay.

Didn't get the "Hold shift" thing to work. When during boot was I supposed to do it?

---

### Post by garvinrick4 on 2011-05-24
while in the Live Cd open a terminal and copy and paste these one at a time.
```
sudo mount /dev/sda5 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda
```
```
sudo umount /mnt
```
boot into Ubuntu on hard disk and open a terminal and:
```
sudo update-grub
```
That should now find Windows and put it in grub menu entry and config file.
Now both should boot.

---

### Post by Negrumir on 2011-05-24
Thanks, that did the trick. I already saw Windows 7 in the boot options when (what I assume was) Grub came up.

Did the update grub anyway.

Now all seems to be working fine.

Thanks again.

---

### Post by garvinrick4 on 2011-05-24
> **Negrumir said:**
> Thanks, that did the trick. I already saw Windows 7 in the boot options when (what I assume was) Grub came up.

Did the update grub anyway.

Now all seems to be working fine.

Thanks again.
Anytime you make any changes to grub you run sudo update-grub and it makes a new
configuration (file in /boot/grub/grub.cfg is the path in file system.) When you run the 3
commands I gave you it mounts the drive with grub in it, installs grub2 (grub-pc) and then 
unmounts the file system (yours sda5) that you just mounted in /mnt. (File system path is /mnt) 
When ever you install grub2 to mbr (master boot record) as we just did it overwrites the one there previously. 
Windows grub will only boot Windows. "Grub2" the package has another package called "os-prober" in it 
that go's out and finds all other Operating Systems and puts it in as a menu entry in grub and in the configuration
file previously discussed (/boot/grub/grub.cfg) when update grub is ran.
If you want to you can run this below instead of sudo update-grub and you can watch grub config being made.
```
sudo grub-mkconfig
```#Enjoy your Ubuntu Linux.
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

