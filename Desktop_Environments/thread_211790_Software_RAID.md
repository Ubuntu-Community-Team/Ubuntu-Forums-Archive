---
title: "Software RAID?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-07-08
I'm reading the software RAID [howto]("http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html") and it requires me to have the raidtools package. 

Searching apt reveals no such package.
```

sudo apt-cache search raidtools2
sudo apt-cache search raidtools
sudo apt-cache search mkraid

```

Does Ubuntu not support software raid? If so does anyone know of a Ubuntu specific howto for accomplishing this? The idea is to create a RAID5 disc array from 3 320GB IDE drives.

---

### Post by Thund3rstruck on 2006-07-08
It appears I have answered at least part of my question. 

```

linuxuser@ZENMOBILE02:~/scripts$ sudo apt-cache search mdadm
mdadm - tool to administer Linux md device arrays (software RAID)

```

---

### Post by TSMJ on 2006-08-30
Did you find a howto in the end? I'm trying to accomplish RAID0 and am having trouble finding a debian/ubuntu howto for it.

---

### Post by mgmiller on 2006-08-30
If you want a much easier time, get a 3ware pci RAID card eg. model 80062LPKIT.  newegg price is $145.00.  It is true hardware raid and unloads all the work from the cpu.  It allows hot swapping and as far as the install of the OS is concerned, it only sees the raid array as 1 drive and requires no user input at all, a normal graphical install of the OS should work fine.  performance gains of 5% to 25% over software raid.  It supports raid 1, 0 1+0 and JBOD.  Native support for this card is in the kernel, no drivers are needed.  "it just works".  For raid 5, they make other cards that are a bit more expensive, but not prohibitive.  3ware is a linux friendly company.

AFAIK, the current software raid options in Ubuntu don't support RAID 5, just 0, 1 and 1+0. It is installed from the alternate install CD, not the graphical installer.

---

### Post by mgmiller on 2006-08-30
Here's what I have been able to find out, at least for RAID 1 and 0 stuff:
  
**important note....this must be installed from the alternate text mode install CD, not the graphical live/install CD.**

I have 2 200Gb SATA disks that I wanted to use as a RAID 1.

Do a normal install of Ubuntu with the 2 drives installed as non raid on the motherboard.

When you get to the partitioning options part of the install, use the default partitioning options and end up with a small (6.8Gb) swap partition and the remainder as a single large partition. (on each of the drives?) (drives should show up as sda and sdb?)

In orer to be used for creating the RAID both disks had their large partitions edited to change the use to “physical volume for RAID”.

Choose “Configure software RAID” from the options

Create MD Device from the Multidisk configuration options

Select RAID 1 when asked

Answer 2 for active devices

Answer 0 for spare devices

Select the 2 partitions created (one per disk)

The new RAID partition was now created but had to be edited (create ext3 filesystem on each maybe?) before it could be used.
Once complete the remainder of the installation went OK.

Remember, if you want to keep your system bootable even if your drive with grub suffered a failure, you have to manually install grub to the other drive.

Grub works with software RAID1, so long as grub is installed on each disk.

But there is a problem. Lets say you have sda and sdb. If sdb fails, then if grub is installed on sda then it should boot fine. However, if sba fails, then sdb typically becomes sba. If grub was installed on sdb while it was mapped to device hd1, it will not be able to boot correctly (since there is no longer a hd1).

The trick is to make grub think that it is installing on (hd0) when it is installing on sdb.

# grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)

---

### Post by cleentrax on 2006-08-30
I've been trying to get a software raid going using this guide:
[http://www.evileyez.org/quick-and-dirty-linux-software-raid5/](http://www.evileyez.org/quick-and-dirty-linux-software-raid5/)

It seems to be pretty straightforward, but the RAID always crashes before it gets completely rebuilt.

---

### Post by TSMJ on 2006-08-31
Thanks for the responses.

I need to set up RAID0 on 4 SCSI disks and there seem to be 2 options ATM: mdadm (using [http://www.evileyez.org/quick-and-dirty-linux-software-raid5/](http://www.evileyez.org/quick-and-dirty-linux-software-raid5/) as a rough guide) or by re-installing ubuntu server and using the 'Configure software RAID' option during the install. Is this right? Any views on this?

I would like to go for the hardware card and in terms of the simplicity it's tempting. I don't want to spend the money however, and it's a low-load server, so the CPU overhead won't be a problem.

Cheers!

---

### Post by Thund3rstruck on 2006-08-31
TMSJ,

I still haven't started this project since I've determined I need 2.5TB (building a DVD movie server backend with XBMC frontend for the family) but I'm hearing rumblings on digg.com and other places that seagate may release a 1TB HDD by the end of the year. I was going to use 4 750GB disks but now I may hold off until early 2007. 

I found a few guides out there and I was going to try [This Guide]("http://gridpt1.fe.up.pt/mlopes/blog/index.php/software-raid-in-ubuntu/") first as it looked very well written.

---

### Post by hotani on 2006-08-31
I used [this guide](http://users.piuha.net/martti/comp/ubuntu/raid.html) to set up RAID-1 on my system. It uses the alternate install disk. The setup was not very intuitive, and took a few tries to get it going correctly, but it did work.

Would love to see a GUI utility for setting up SW RAID a la Mac OS X (read: drag disks to window, click "apply").

---

### Post by mjziegle on 2006-08-31
I use mdadm for a raid 1.  The man pages are helpful and complete.

If you need a guide search google for an mdadm.

It is preferred over the raidtools package and is already available by default in Ubuntu.

The big advantage is it doesn't require a configuration file and is bootable.

---

### Post by TSMJ on 2006-09-01
OK, looks like mdadm is the way forward - I've done a lot of config on the system and wasn't looking forward to the prospect of re-installing anyway. EVMS looks a bit complicated for now too.

So, going roughly on the several guides I've seen, I need to do this(?) for RAID0:


[INDENT]1. Partition each of the disks (sdd, sde, sdf & sdg) with a single partition each

2. Create array
```
mdadm --create --verbose /dev/md0 --level=0 --raid-devices=4 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
```

3. Synch disks
```
reboot
``` or ```
mkraid /dev/md0
```

and 

```
watch cat /proc/mdstat
``` 
whilst the disks sync


4. Format md0 (with ext3)

5. Add entry in fstab

6. Mount[/INDENT]

Any thoughts? 
I take it I format, add to fstab and mount like any other HDD?
Cheers!

---

### Post by TSMJ on 2006-09-04
Well, in reply to myself - it worked. I followed those instructions, and RAID0 was set up in seconds - it was much easier than I expected. AFAIK, RAID0 does not need to synch it's disks as RAID5 does, so that/rebooting part wasn't needed.

Basically, for RAID0:
1. Partition each of the disks
2. Use mdadm to set up the array:
```
mdadm --create --verbose /dev/md0 --level=0 --raid-devices=4 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
```
3. Format /dev/md0 (your new array) as you would a normal disk
4. Add an entry to fstab for it, again, like a normal disk.

The default install of Ubuntu Server doesn't include mkraid either, so that command didn't work. Not that you need it.

---

### Post by ph8 on 2006-09-13
Is all this done after install (assuming you'd have to install to set the partitions up?)

Also, for RAID1 is it just a case of changing --level=0 to --level=1?? ;) Hoping to install a raid1 system this evening..

Cheers in advance,

Henri

---

### Post by TSMJ on 2006-09-13
Yes, this is done after install. The other option is to set up software RAID during the install process (which is an option).

I cannot say for sure, but I'm confident that changing --level=0 to --level=1 will work. You can find out more about mdadm by reading the man page on it (type `man mdadm`), before trying anything.

---

