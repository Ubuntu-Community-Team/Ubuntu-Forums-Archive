---
title: "Help accessing windows partion"
date: 2009-03-03
forum: General Help
---

### Post by racermike1967 on 2009-03-03
Hi all,

Recently, my windows partition got infected with a trojan.  I tried to remove it using various types of anti-virus program (AVG - free version) in vain.  My most recent attempt to remove the trojan resulted in the computer freezing up and me having to shut down the laptop by holding down the power button.  When I try to load up the windows partition again, I am able to get up to the desktop however, all desktop icons including the taskbar (start menu, shorcuts, etc) are missing.  

Ctrl-alt-delete is non-responsive.
Ctrl-esc is non-responsive
Right-mouse button click is non-responsive.

The only things that appear to work is the caps lock button, Num Lock button and Scroll Lock button.

I have several important files that I need access to however as a result of the trojan and anti-virus reaction, I am unable to access anything.

I can't even access the windows parition via Ubuntu since the windows partition was not closed properly.

**Can anyone help me to either mount the windows partition so that I can access my files or to get rid of the trojan via ubuntu?**

Help would be greatly appreciated.

---

### Post by neer2005 on 2009-03-03
you would have to install ntfs-3g in order to mount the windows partition

---

### Post by James- on 2009-03-03
in terminal you can run 

*fdisk -l*

to list the disks and the partitions

When you see the partition size/format(usually NTFS) that corresponds to windows

Create your mount folder
*sudo mkdir /media/<mount point>*

mount drive:

*sudo mount <Windows path here> /media/<mount point>*
i.e. sudo mount /dev/sda1 /media/windows

if you did not do a proper shutdown you will have to force it(not really recommended it may not find all disk error)

*mount -t ntfs-3g <Windows path here> /media/<mount point> -o force*

---

### Post by Qsl1pknotp on 2009-03-03
Hi Racer, 

Have you tried MalwareBytes? (Google for it). Also ComboFix, (But don't use COmboFix if you r using Vista). And yes, There are a few programs out there that will scan your windows Partition for you from a boot up cd (Though I can't think of any at the moment). 

Oh, and if you use ComboFix, make sure you're in safe mode.

---

### Post by Qsl1pknotp on 2009-03-03
Also, you can boot to your repair cd[Windows](Or Repair Console) and type in 

Chkdsk C: /f (fix repair so you can mount from Ubuntu)


> **James- said:**
> in terminal you can run 
*fdisk -l*

to list the disks and the partitions

When you see the partition size/format(usually NTFS) that corresponds to windows

Create your mount folder
*sudo mkdir /media/<mount point>*

mount drive:

*sudo mount <Windows path here> /media/<mount point>*
i.e. sudo mount /dev/sda1 /media/windows

if you did not do a proper shutdown you will have to force it(not really recommended it may not find all disk error)

*mount -t ntfs-3g <Windows path here> /media/<mount point> -o force*

---

### Post by theozzlives on 2009-03-03
> **James- said:**
> in terminal you can run 

*fdisk -l*

to list the disks and the partitions

When you see the partition size/format(usually NTFS) that corresponds to windows

Create your mount folder
*sudo mkdir /media/<mount point>*

mount drive:

*sudo mount <Windows path here> /media/<mount point>*
i.e. sudo mount /dev/sda1 /media/windows

if you did not do a proper shutdown you will have to force it(not really recommended it may not find all disk error)

*mount -t ntfs-3g <Windows path here> /media/<mount point> -o force*

after that go:
```
sudo apt-get install clamav
```
then:
```
mkdir /tmp/virus
```
```
clamscan -ri --move=/tmp/virus <mountpoint>
```

---

### Post by racermike1967 on 2009-03-04
> **theozzlives said:**
> after that go:
```
sudo apt-get install clamav
```
then:
```
mkdir /tmp/virus
```
```
clamscan -ri --move=/tmp/virus <mountpoint>
```

I tried to do what you said but when I type in:
fdisk -l

I get the following message:

Cannot open /dev/sda


Any suggestions?

---

