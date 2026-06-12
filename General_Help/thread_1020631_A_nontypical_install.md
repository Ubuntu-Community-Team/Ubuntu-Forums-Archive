---
title: "A nontypical install"
date: 2008-12-24
forum: General Help
---

### Post by Arukas on 2008-12-24
I want to install another variat of ubuntu over an existing one.  The problem I am having is windows is also installed on the same harddrive, and I can't simple reformat and reinstall windows.  


Anyone can shed some light on this?

---

### Post by davec64 on 2008-12-24
You could use Gparted to just format your Linux partitions or alternatively delete them. Then during the install select the free space for the new partitions.

---

### Post by Arukas on 2008-12-24
Is there instructions on how to use gparted, every time I used gparted it has not work one bit.

---

### Post by petersohn on 2008-12-24
What does "not work one bit" mean? It has always been working for me. However, if you want to install ntfs support, you may need to install some additional packages (I don't remember which, search for "ntfs" in Synaptic).

---

### Post by Patrick793 on 2008-12-24
You don't need to re-install. If you want another varient you can do
```
sudo apt-get install kubuntu-desktop
```
or
```
sudo apt-get install xubuntu-desktop
```

That way you can switch the desktop environment you want to use at the login screen.

---

### Post by Arukas on 2008-12-24
Let me rephrase, I don't know how to use gparted.

It loads up fine, but I can't figure out how to make it do anything.  I've asked about gparted before, but I it never got anywhere.

---

### Post by linux_tech on 2008-12-24
You can either download and create gparted cd or you can boot off ubuntu live cd and then run gparted.  

Here are a few gparted resources-
[http://manual.sidux.com/en/part-gparted-en.htm](http://manual.sidux.com/en/part-gparted-en.htm)
GParted LiveCD
	[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Documentation 	[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Screenshots 	[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by namdung on 2008-12-24
> **Patrick793 said:**
> You don't need to re-install. If you want another varient you can do
```
sudo apt-get install kubuntu-desktop
```
or
```
sudo apt-get install xubuntu-desktop
```

That way you can switch the desktop environment you want to use at the login screen.

I agree. In your case you don't need to re-install. 

Learning to use gparted is another case.

---

### Post by ugm6hr on 2008-12-24
> **Arukas said:**
> I want to install another variat of ubuntu over an existing one.

What have you got at the moment, and what do you want to install?

Post output of:
```
sudo fdisk -l
```

And if you really want to install over the top, just do it with the manual option.  Select your current Ubuntu partition and swap as "/" and "swap" respectively (and tick the format box).

---

### Post by cariboo on 2008-12-24
Have you highlighted the partition you want to use and right clicked? 

If you just want to install a different distribution, just install over top of the old one, using the same partitions.

Jim

---

### Post by davec64 on 2008-12-24
Her's a link to a howto using Gparted for a Linux installation. It will give you a flavour of what Gparted can do!

[http://www.ehow.com/how_4442682_use-gparted-live-cd-prepare.html]("http://www.ehow.com/how_4442682_use-gparted-live-cd-prepare.html")

Once you get to grips with it, it is a very powerful tool!

---

### Post by Arukas on 2008-12-24
Lets starts over here for clarity's sake. I want to uninstall Kubuntu 8.10 64 bit and put in its place Kubuntu 8.04 32 bit.  I would like to install the new version in the same paritions because my xp operating system is on it and I don't want to reformat the whole things.  

I don't know how to use gparted, or do a manuel install.  This is what I am trying to figure out.  



Also, as far as I know, 

sudo apt-get install xubuntu-desktop

doesn't do what I want it too.  I've done stuff like this before looking at other desktops and it just messes everything up.

---

### Post by ugm6hr on 2008-12-24
> **ugm6hr said:**
> And if you really want to install over the top, just do it with the manual option.  Select your current Ubuntu partition and swap as "/" and "swap" respectively (and tick the format box).

Do a manual install with Kubuntu 8.04 32-bit.

When you get to partitioning, select the current Kubuntu partition, put a tick in the "format" box, and select "/" as mount point.  Make sure none of the other partitions (specifically the XP one) have a mount point or format ticked.

The installer generally picks up your swap partition automatically.

The rest of the installation is the same as the first time around.

Obviously this will reformat everything on your Kubuntu partition - so backup anything you need to keep.

---

### Post by Arukas on 2008-12-24
How do I tell which partition is my Kubuntu on, When I do a manuel install.  I think i may know, but I want to be for sure as I don't want to format the wrong thing.

---

### Post by ugm6hr on 2008-12-24
> **Arukas said:**
> How do I tell which partition is my Kubuntu on, When I do a manuel install.  I think i may know, but I want to be for sure as I don't want to format the wrong thing.

```
sudo fdisk -l
```

I'll try and help you identify it in the list.

---

### Post by Arukas on 2008-12-24
[PHP]

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4a9b4a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       73852   593216158+   7  HPFS/NTFS
/dev/sda2           73853       91201   139355842+   5  Extended
/dev/sda5           73853       90491   133652736   83  Linux
/dev/sda6           90492       91201     5703043+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x02f3d57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70f670f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       25493   204772491    7  HPFS/NTFS
/dev/sdc2           25494       38913   107796150    5  Extended
/dev/sdc5           25494       38362   103370211   83  Linux
/dev/sdc6           38363       38913     4425876   82  Linux swap / Solaris


[/PHP]

---

### Post by ugm6hr on 2008-12-24
Wow.  3 massive HDs.

You have 2 potential candidates for Kubuntu:
sda5 (on 750GB HD) or sdc5 (on 320GB HD)
Unfortunately - you'll have to work the rest out.


I see you also have 2 swap partitions (sda6 and sdc6). Why?

---

### Post by Arukas on 2008-12-24
accidental double post, couldn't figure out how to delete.

---

### Post by Arukas on 2008-12-24
Why do I have to swap partitions?  Oh that's easy.  Having two swap partitions make Linux goes twice as fast as it can swap faster.  


I have not had a chance to reformat my 320 HDD is the real reason.  It use to be the main boot HDD in my computer until i upgraded, When I finish backing up all the files I want, I'll format it.  


Anyway, I'm going to try and reinstall and see what happens with linux.

---

