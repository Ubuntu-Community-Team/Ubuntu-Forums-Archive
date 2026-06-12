---
title: "Can't mount hard drive"
date: 2009-06-08
forum: General Help
---

### Post by interestinfellow on 2009-06-08
Have an emachine, installed xubuntu.
Swapped my hdd from another ubuntu machine into the emachine because the ubuntu machine had a motherboard keyboard error.

Ran ok, everything worked well enough.

EMachine wasn't fast enough, so I put the xubuntu hdd back in the machine, checked my jumpers, and fired it up.  Xubuntu starts fine and runs fine, but I can't mount my 2nd hdd with all my crap on it.

The bios and post identify the hdd (120gb 7200rpm OEM drive) and fdisk -l sees the drive as follows
> Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c0bed9c

It doesn't see the drive in "places" and I can't mount it (as follows)
> user@Teenee:~$ mount /dev/sdb
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
user@Teenee:~$ sudo mount /dev/sdb
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
user@Teenee:~$ 

Someone please help....

---

### Post by synapsys on 2009-06-08
You have to give it a place to mount. Just typing mount /dev/sdb is fine if you've already told your system where to mount /dev/sdb. This information is held in /etc/fstab which is a configuration file for mounting hard disk partitions. To mount the drive for this session only, make a folder in /media/ for the drive to mount to.

```
cd /media
sudo mkdir disk
sudo mount /dev/sdb /media/disk
```If you want this drive to automatically mount every time you start your system you'll need to edit /etc/fstab to tell your partition where to mount. There are plenty of tutorials on how to add a partition to your fstab. Find out what file system it's using and google 'adding (your file system) to fstab'.

---

### Post by yeats on 2009-06-08
You need to define a directory to be the mount point on your system.  This is done automatically when you mount through the GUI, but you have to specify it when doing it manually.  So...

Create a directory:

```
sudo mkdir /media/hdisk
```

Then mount the drive as follows:

```
sudo mount -t ext3 /dev/sdb /media/hdisk
```

(the "-t ext3" part describes the _t_ype of filesystem - see *man mount* for details about how to define other types)

---

### Post by interestinfellow on 2009-06-08
I don't necessarily want to use the terminal, I only did that to try and diagnose the problem.

Why doesn't the drive just show up in the gui ("Places"?)?  How do I make it show up?  And yes, I would like the drive to be accessible every time.

And I believe the drive was ntfs and a dynamic disk (created by xp originally)

What happen's if I specify the wrong file system type?

and THANK YOU for the quick replies!

---

### Post by interestinfellow on 2009-06-08
and here's what I get.
> user@Teenee:/$ sudo mount -t ntfs /dev/sdb /media/hdisk/
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


---

### Post by synapsys on 2009-06-08
Please post results of:

```
sudo fdisk -l
```

---

### Post by interestinfellow on 2009-06-08
.
> user@Teenee:/$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe64a4d43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7388    59344078+  83  Linux
/dev/sda2            7389        7476      706860    5  Extended
/dev/sda5            7389        7476      706828+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c0bed9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   42  SFS
user@Teenee:/$ 


---

### Post by synapsys on 2009-06-08
Your filesystem is on sdb1 not sdb. It is labeled as SFS which should be able to be read using ntfs driver. Try mounting again:

```
sudo mount -t ntfs /dev/sdb1 /media/hdisk/
```If that works, I will show you how to add it to your fstab so that it auto mounts on every boot.

****NOTE: /media/hdisk must be an actual folder or this will not work****

---

### Post by interestinfellow on 2009-06-08
OK....

That worked.  Why?  Why is it sdb1 and not sdb as indicated by fdisk-l?

Why does it not automatically show up, like my 2g jump drive, or sd card, in "Places" (or automatically like in my other install(s) of ubuntu)? how do i get it there?

Thanks!

---

### Post by synapsys on 2009-06-08
sdb is the name of the physical hard drive that sdb1 resides on. sdb1 is the name of the partition which the filesystem resides on. If you look at fdisk -l first it shows the drive info for sdb. The next block shows the partition information for sdb. In this case there is only one partition and it has the SFS label indicating it's file type. 

Now to make the sdb1 partition mount automatically with every boot. 

```
sudo mousepad /etc/fstab
```***WARNING: Editing fstab can be dangerous. Deleting the wrong line can get you in lots of trouble. Be careful.***

Once fstab is open in your text editor add this line to the very end. Leave everything else alone!

> /dev/sdb1       /media/hdisk/   ntfs    ro,user,auto,noexec,umask=0  0       0Save the file and reboot your system. It should show up on your desktop when you reboot, and also be in 'places'

Let me know if this works.

---

### Post by interestinfellow on 2009-06-09
didn't work....

should that /mnt/hdisk be media/hdisk (or should I create /mnt/hdisk)?

thanks!

---

### Post by synapsys on 2009-06-09
yeah sorry should be /media/hdisk/ just like when you mounted it in the terminal. I edited my post when I realized but it was too late.....

---

### Post by interestinfellow on 2009-06-09
alrighty then.....

SO it auto mounts, but doesn't show up on the desktop or "places".  I'm gonna puts around and get that to work now, and/or wait for you to tell me.

in either case, I truly appreciate your assistance!  Thanks!

---

### Post by synapsys on 2009-06-09
quick question... can you see the contents of the folder?

places >> computer >> filesystem >> media >> hdisk

---

### Post by interestinfellow on 2009-06-09
yes sir! I have access to all my files, I'm just missing that nice little gui shortcut (i'm slack)...

---

### Post by synapsys on 2009-06-09
I believe there is an option in XFCE to show mounted hard drives on the desktop. I'm not quite sure as I use Ubuntu not Xubuntu. You could always make a link to the folder and place it on the desktop like a shortcut in windows. Maybe google how to show mounted hard drives on desktop in XFCE. 

Anyways here's how to make a link:

```
sudo nautilus /media
```

Right click hdisk and choose 'make link'
It should be called shortcut to hdisk or something like that.
Copy/paste that to desktop

---

### Post by interestinfellow on 2009-06-10
Thanks again!!!

---

### Post by interestinfellow on 2009-06-16
I'm still not sure why Xubuntu doesn't just detect my Z drive automaticly, like Ubuntu does.  Can anyone explain this (just out of curiousity)?

Now, I have access to all those files, and in Gnumeric, I can modify those files, but in OO Calc, it always opens as read only.  the problem here is that Gnumeric doesn't maintain all my formatting and fonts and such, and I don't have time to go throught the 100's of docs that would need to be reformatted.

SO, how do I (pick one)

get Xubuntu to automatically present the drive with the appropriate permissions intact in the same fasion as Ubuntu?
OR
get Gnumeric to recognize the formatting of OOCalc?
OR
Take ownership of the mount/drive, so I have unrestricted access to my files? (not sure if this is what happens in Ubuntu normally and/or it would be a bad idea?)

Please help!

---

### Post by interestinfellow on 2009-06-16
Bump

---

### Post by wapicke on 2009-06-30
> **synapsys said:**
> Please post results of:

```
sudo fdisk -l
```

> ```
_______@__________:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa156a156

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433        4865    19543072+   5  Extended
/dev/sda5            2433        2563     1052226   82  Linux swap / Solaris
/dev/sda6            2564        4865    18490783+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1ae51ae4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20673   156287848+   c  W95 FAT32 (LBA)
wapicke@wapstation:~$ 
```
I used the commands you listed for the other gentleman, with mods to the second drive here, but I get some errors with this.  I'm using Ubuntu 9.04, if that helps.

---

### Post by wapicke on 2009-06-30
Never mind, I figured it out from an old lesson I went through using SuSe 9.0.  W95 FAT32 is aka vfat.  That worked, thanks.

---

### Post by arnelcolar on 2009-12-09
hey I don't have that thing after Device Boot  Start         End      Blocks   Id  System why is that? I got xubuntu from synaptic package manager because im running on ubuntu and decided to try xubuntu and starting to like it...

```
arnel@myUbuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.5 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce2c42cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2382    19133383+  83  Linux
/dev/sda2            2383        2491      875542+   5  Extended
/dev/sda5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16a816a8

   Device Boot      Start         End      Blocks   Id  System
```

And when I followed the commands that you have given here, this shows up:

```
mount: special device dev/sdb does not exist

```

It does the same thing when I tried it on dev/sdb1

---

### Post by JKyleOKC on 2009-12-09
Instead of all the tedious (and error-prone) manual editing of fstab, why not install the "pysdm" package via Synaptic and run it to get everything as you want it?

After installation on Xubuntu, the program will show up in the Application menu under System as "Storage Device Manager." The first time you run it you'll see the detected drives in the window's left pane. Click the triangle to expand the tree and show partitions. Click a partition to set up its configuration. Use the "Assistant" button of the right pane to select the options you want, and the "Mount" button to mount the partition (the button will say "Unmount" if it's already mounted).

To make the partition show up in Places, use File Manager to navigate to /media, then highlight the partition's name in the right pane and drag it over to the left pane. This creates a shortcut, and you can rename the shortcut to anything you like. 

Hope this helps! It's much easier than all the editing...

---

### Post by arnelcolar on 2009-12-09
I tried what you said but i cant seem to open sdb. heres the screenshot:
[IMG]http://lh4.ggpht.com/_6n89c6efCHA/SyBAZviZOZI/AAAAAAAABMI/R9HgxxMeWw0/Screenshot.png[/IMG]

As you can see on the right side everything is disabled.Why is that?

---

### Post by arnelcolar on 2009-12-10
Nevermind... I'll just install the whole thing and change my fs to ext4...

---

### Post by JKyleOKC on 2009-12-10
For some reason your system isn't finding the partition on the sdb drive; apparently it's totally blank (at least so far as your system can tell). That's why your "fdisk -l" report doesn't show any partitions for it, and why the righthand pane of Storage Device Manager is grayed out.

Perhaps your "install the whole thing" will make the partitions visible, but it's also possible that a bad choice while doing the install may have actually wiped the disk clean of everything...

---

