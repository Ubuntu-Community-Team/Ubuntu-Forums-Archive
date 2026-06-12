---
title: "LILO Problem"
date: 2005-09-24
forum: Desktop Environments
---

### Post by Toby2 on 2005-09-24
First of all, I'm a real newbie to Ubuntu, I just installed it yesterday.

I have Windows XP and I set that to one partition, and then I installed Ubuntu in the free space left over (about 15GB). The installation went smoothly, and I installed LILO. But when I booted up, there was no menu to select an OS. So I had a look around these forums and found a solution: editing the /etc/lilo.conf file. I edited it, but when I try to update it in the terminal (sudo lilo) I get this error:

```
toby@ubuntu:~$ sudo lilo
Password:
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/dm'
device-mapper ioctl cmd 12 failed: No such device or address
Fatal: device-mapper: dm_task_run(DM_DEVICE_TABLE) failed
```

What's going wrong? Can anyone help me?

---

### Post by aysiu on 2005-09-24
Frankly, I'm a bit confused about your situation, because I've never seen (or can't remember seeing) Lilo as an option during a 5.04 or 5.10 install of Ubuntu. Are you using Warty, by chance? As far as I can tell, it's always Grub, and to get it to work for a dual boot, you always install Grub to the MBR.

I have found that often times [doing a Google search for an error](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=%22Fatal%3A+device-mapper%3A+dm_task_run%28DM_DEVICE_TABLE%29+failed%22&btnG=Search) can be helpful, though.

---

### Post by Toby2 on 2005-09-24
[QUOTE=aysiu]Frankly, I'm a bit confused about your situation, because I've never seen (or can't remember seeing) Lilo as an option during a 5.04 or 5.10 install of Ubuntu. Are you using Warty, by chance? As far as I can tell, it's always Grub, and to get it to work for a dual boot, you always install Grub to the MBR.[/QUOTE]
I'm using 5.10. I got an option in the installer, and the default was LILO, so that's what I chose. I think GRUB was there too...

As for your suggestion, it came up with no helpful results. I'm confused... is it something I did in the install? Some settings I changed?

---

### Post by serzz on 2005-09-30
Same thing here.

---

### Post by psychicdragon on 2005-10-01
I had no idea lilo was the default boot loader in Breezy. That's completely nuts. Wouldn't that make Ubuntu one of the only distros still using lilo by default? You should probably just install grub.

**sudo grub-install** should work assuming you have the package. Otherwise, you'll have to apt-get it.

Might be better to ask this in the Breezy forum though.

---

### Post by serzz on 2005-10-01
I'm really thiking to switch back Grub byt it seems there some problems with LVM and Grub. Plus I can't figure out grub config file.

---

### Post by vcmsxs on 2005-10-01
I have too just installed the Breezy dist, want the os loader to show me both my linux and my winXP(ntfs) on hda1, got lilo default at installation, got the error message: "Fatal: device-mapper: dm_task_run(DM_D...." when trying to /sbin/lilo (after making some changes in /etc/lilo.conig).  

Have just installed grub but how do I supress lilo and make grub the default os loader ? And how do I make grub giving me the options of both the windows and ubuntu ? 

Thanx alot
J.

---

### Post by daveisadork on 2005-10-07
When you choose XFS as the filesystem instead of ext3, the installer uses LILO as default and advises that there are problems installing GRUB when you're using an XFS partition. I can make changes to lilo.conf and apply them by running LILO, and it will list other OSs as being added, but on boot there is no menu, it just boots the default.

---

### Post by bruyeron on 2005-10-13
Grub is the default bootloader until you put your / partition in LVM.
The problem described here affects those who put their / partition under LVM:
1) breezy switches to lilo in this case
2) sometime recently something broke in either lilo or the libdevmapper (or both) that causes the problem described in the first post:

# lilo
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/dm'
device-mapper ioctl cmd 12 failed: No such device or address
Fatal: device-mapper: dm_task_run(DM_DEVICE_TABLE) failed

The installation of hoary (including LVM+lilo) worked fine. This problem appeared recently when I upgraded to breezy.

lilo Version: 1:22.6.1-6.2ubuntu1
libdevmapper1.01 Version: 2:1.01.03-1ubuntu2

---

