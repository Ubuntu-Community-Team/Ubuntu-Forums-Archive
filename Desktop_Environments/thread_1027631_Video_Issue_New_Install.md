---
title: "Video Issue New Install"
date: 2009-01-01
forum: Desktop Environments
---

### Post by 14ALL on 2009-01-01
Now that I understand the problem better, this should actually be titled:
 "BOOT UP ISSUE - NEW INSTALL"

I installed v8.10 to following  system:
Intel D815EEA Motheboard
PIII-1Ghz Intel Processor
384MB RAM
200GB Hard Drive
ATI Radion 9000 - AGP Graphics Card (Analog)
SamSung SyncMaster 740B Analog/Digital LCD Monitor

Clean Install.  On bootup, get error:
"/dev/disk/by-uuid/4c97a4d6-0049-4b5e-84b4-fd840476916b does not exist.  Dropping to a shell"

---->>>> If I cd to that location, IT DOES IN FACT EXIST. <<<<----

If I type the word "Exit", the PC boots fine.  This happens every time.
How can I correct this problem?

---

### Post by stderr on 2009-01-01
This is probably a problem in /etc/fstab, or might be an issue in /boot/grub/menu.lst

Please post the output of each of the following (in a terminal):

```
cat /etc/fstab
```
```
ls -al /dev/disk/by-uuid
```
```
sudo fdisk -l
```

and identify which UUID is referenced in the boot error message (i.e. what the hex string is). Cheers.

---

### Post by 14ALL on 2009-01-01
Exact UUID referenced in error is:
UUID=4c97a4d6-0049-4b5e-84b4-fd840476916b 
=====================================

14all@My-Wkst1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc/proc  proc defaults  0  0# /dev/sda1
UUID=4c97a4d6-0049-4b5e-84b4-fd840476916b 
/ext3    relatime,errors=remount-ro 0       1# /dev/sda5UUID=52570210-6199-485a-9b2b-e959c10f4ef1 none  swap sw              0 0
/dev/scd0       
/media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0

=====================================

14all@My-Wkst1:~$ ls -al /dev/disk/by-uuid

total 0drwxr-xr-x 2 root root  80 
2009-01-01 16:14 .drwxr-xr-x 5 root root 
100 2009-01-01 16:14 ..lrwxrwxrwx 1 root root  
10 2009-01-01 16:14 4c97a4d6-0049-4b5e-84b4-fd840476916b ->
 ../../sda1 lrwxrwxrwx 1 root root  10 
2009-01-01 16:14 52570210-6199-485a-9b2b-e959c10f4ef1 -> 
../../sda5

======================================

14all@My-Wkst1:~$ sudo fdisk -l
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77f92dd4 Device Boot Start   End  Blocks  Id  System/dev/sda1   *  1 24181 194233851 83  Linux/dev/sda2 24182 24321     1124550    5  Extended /dev/sda5  24182 24321 1124518+  82  Linux swap / Solaris

---

### Post by stderr on 2009-01-02
Hmm... well... unless the problem exists in /boot/grub/menu.lst instead, I'm not 100% sure.

You could try replacing the UUID in fstab with the name instead

```
UUID=4c97a4d6-0049-4b5e-84b4-fd840476916b / ext3 relatime,errors=remount-ro 0 1
```

to

```
/dev/sda1 / ext3 relatime,errors=remount-ro 0 1
```

I'd keep a Live CD to hand, just in case you suddenly can't boot, you can just boot into that, mount your drive and revert any changes.

Therefore, it would be a good idea (as always) to make a backup copy of /etc/fstab first ("sudo cp /etc/fstab /etc/fstab.backup") before editing it as root ("sudo vim /etc/fstab", or "gksudo gedit /etc/fstab").

In an emergency :) Mounting the drive in a live CD environment: something like "sudo mount /dev/sda1 /mntpt". Reverting the file: "sudo cp /etc/fstab.backup /etc/fstab"

---

### Post by 14ALL on 2009-01-02
I'll give it a try.  If all else fails, I'll resolve to typing "Exit" to complete the boot process.  Thanks!

---

### Post by 14ALL on 2009-01-02
Replaced UUID in fstab with suggested string "/dev/sda1 / ext3 relatime,errors=remount-ro 0 1"  This had no affect on bootup process - Got same error message.

Performed several other tests:

TEST 1:
=======
1a.  Boot-up, Error="Alert /dev/disk/by-uuid/4c97a4d6-0049-4b5e-84b4-fd840476916b does not exist."

1b.  Immediately typed "Exit" and error repeated.

1c.  Typed "Exit" again.  Got Message "trying resume from 52570210-6199-485a-9b2b-e959c10f4ef1"

1d.  Booted successfully.

TEST 2:
=======
2a.  Did Reboot & Boot Menu Displayed.

2b.  Chose 1st menu item and booted successfully.

Note:  This is strange, because I had booted from the menu in the past choosing the 1st option and would get the same results as test 1.


TEST 3:
=======
3a.  Did reboot - no boot menu displayed.

3b.  Waited several seconds after error message Error="Alert /dev/disk/by-uuid/4c97a4d6-0049-4b5e-84b4-fd840476916b does not exist."

3c.   Typed "Exit" again.  Got Message "trying resume from 52570210-6199-485a-9b2b-e959c10f4ef1"

3d.  Booted successfully.


TEST 4:
=======
4a.  Backed up and then edited fstab.  Replaced UUID=4c97a4d6-0049-4b5e-84b4-fd840476916b with UUID=52570210-6199-485a-9b2b-e959c10f4ef1 and Rebooted

4b.  Error= "Alert /dev/disk/by-uuid/4c97a4d6-0049-4b5e-84b4-fd840476916b does not exist."

4c.  Immediately typed "Exit" and got repeat error.

Note1: Strangely, Editing fstab had absolutely no affect upon how the system boots up.

Note2:  Twice now typing Exit quickly generated the same error, but waiting and retyping booted successfully.  Seems to be a timing error, so Test 5.

TEST 5:
=======
5a.  Set /boot/grub/menu.lst to default boot in 90 seconds and rebooted.

5b.  After 90 seconds, got same error "Alert /dev/disk/by-uuid/4c97a4d6-0049-4b5e-84b4-fd840476916b does not exist"

5c.  Typed "Exit" and got "trying resume from 52570210-6199-485a-9b2b-e959c10f4ef1"

5d.  System booted successfully

Note 1:  Guess it's not a timing issue either.

If I could figure out a way to make 52570210-6199-485a-9b2b-e959c10f4ef1 the default boot, that might work.  However, editing /etc/fstab and changing to it had no affect on bootup???


Any other suggestions would be greatly appreciated.  Until then, I'll keep typing "Exit" to boot up.

Thanks.

---

### Post by stderr on 2009-01-05
To affect bootup, you need to edit /boot/grub/menu.lst

The boot menu entries (and therefore the default boot) is right at the end of the file after all the config options. 

It might be helpful if you posted the boot menu entries from menu.lst here. We don't need all the configuration variables in the top bit though.

edit: I suppose I should add, I'm getting the same error on one of my Ibex installations :p similarly to you, I'm not minding typing exit occasionally... but I suppose since I only reboot this box once every, say, 50 days, it doesn't affect me too much ;) It would be worth solving though.

---

