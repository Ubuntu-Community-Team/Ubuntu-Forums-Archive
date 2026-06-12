---
title: "Hope to install my Ubuntu &quot;Fiesty Fawn&quot; Live CD on this PC again"
date: 2009-05-30
forum: General Help
---

### Post by SonicRacer1412 on 2009-05-30
But I have so much installed on here. How could I install a dual-boot at this point with absolutely no risk. I have been using Linux for a few months in the Fall, as you can remember, and I liked it. How would I know how much space I have left on my computer and how much left free space there will be on my WinXP partition once I have Ubuntu re-installed. Unlike before, I am using an OEM version of Windows XP Home Edition (I realized we had the original restore disk, so I popped it in and restored the OEM version, because I wanted to play "The Movies" PC game and my clean install of WinXP Pro didn't have a 3D accelerator card driver on it). Any help? Thanks.

---

### Post by ajgreeny on 2009-05-30
Simply boot the live CD and then in terminal run the command ```
df -h
``` and it will tell you the free space in Kb Mb or Gb on each partition and virtual file-system mounted at the time.  To see all your hard disks or partitions, mount them all before running the command.  A new vanilla install of ubuntu will be about 2.6 Gb but you will need a lot more for all your docs and photos and personal files, of course, as well as any other applications you install.

---

### Post by mocoloco on 2009-05-30
Unless you have a specific reason to, I would recommend against installing Fiesty Fawn, since it's no longer supported.  If you're concerned about space and afraid of the idea of partitioning, I would recommend you install the latest version of Ubuntu (9.04, *Jaunty Jackalope*) using [Wubi]("http://www.wubi-installer.org/").  This is done from inside of Windows, and instead of partitioning your disk, it uses a file (of whatever size you choose) on your Windows partition to contain all of the Ubuntu data.  It's only slightly slower than a "real" install on a second partition, but without the concern, and is perfect if you're just testing or not planning on using Ubuntu as your primary OS.

If you feel a partitioned install is better, download the latest [9.04 ISO]("http://www.ubuntu.com/getubuntu/download"), burn a disc and use it.  The installer will give you control over how much space you want to leave for your Windows partition.

---

### Post by SonicRacer1412 on 2009-05-30
> **mocoloco said:**
> Unless you have a specific reason to, I would recommend against installing Fiesty Fawn, since it's no longer supported.  If you're concerned about space and afraid of the idea of partitioning, I would recommend you install the latest version of Ubuntu (9.04, *Jaunty Jackalope*) using [Wubi]("http://www.wubi-installer.org/").  This is done from inside of Windows, and instead of partitioning your disk, it uses a file (of whatever size you choose) on your Windows partition to contain all of the Ubuntu data.  It's only slightly slower than a "real" install on a second partition, but without the concern, and is perfect if you're just testing or not planning on using Ubuntu as your primary OS.

If you feel a partitioned install is better, download the latest [9.04 ISO]("http://www.ubuntu.com/getubuntu/download"), burn a disc and use it.  The installer will give you control over how much space you want to leave for your Windows partition.
But I only have the Feisty Fawn 7.4 Live CD available and I don't have any CD-RWs with me.

---

### Post by lisati on 2009-05-30
> **SonicRacer1412 said:**
> But I only have the Feisty Fawn 7.4 Live CD available and I don't have any CD-RWs with me.

Although you probably will be able to install 7.04 you might find it difficult to install updates because of lack of "official" support - it might be a good idea to wait until you have a suitable blank CD and download a newer version to use. You could also request a free CD from Canonical - [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by mocoloco on 2009-05-30
You can go ahead and install with the Fiesty disc and it will give you options about partitioning.
However: you will not be able to download any new applications or updates! This is because once a release is out of support the repositories for that version are turned off.
Now you will be given the option to upgrade. You can do an in-place upgrade, but you can only go one version at a time, so you would upgrade to Gutsy (7.10) next, but it's also out of support! From there you could upgrade to Hardy (8.04) which is supported.  However that's a lot of time, lot of data to download, and in-place upgrades sometimes cause problems (it's gotten better than it used to be).

Again, I would say go for Wubi.  No CD required for it, just click and run right from Windows.

---

### Post by merlinus on 2009-05-30
FWIW, reasons not to use wubi:

Windows crashes and no longer will run.  This is not uncommon.  What happens to ubuntu and the data stored there?

Ubuntu will not run as well under windows, and basically will be plagued by the usual microsoft problems -- viruses, spyware, and assorted other vermin.

IMFFHO, better to start with a fresh install of ubuntu, and go from there.  If you need more disk space you could get a second hdd, or use gparted to resize some of your partitions and create some room.

My $.05 worth....

---

### Post by cmost on 2009-05-30
> **merlinus said:**
> FWIW, reasons not to use wubi:

Windows crashes and no longer will run.  This is not uncommon.  What happens to ubuntu and the data stored there?

Ubuntu will not run as well under windows, and basically will be plagued by the usual microsoft problems -- viruses, spyware, and assorted other vermin.

IMFFHO, better to start with a fresh install of ubuntu, and go from there.  If you need more disk space you could get a scond hdd, or use gparted to resize some of your partitions and create some room.

My $.05 worth....

I agree!!  Wubi is a nice idea whose time hasn't come yet.  Stick with the traditional method and go for Ubuntu 8.04 LTS edition.  Don't try to reinstall Feisty - it's too old and no longer supported.

---

### Post by jmszr on 2009-05-30
Actually there is an easy fix for:> Windows crashes and no longer will run. This is not uncommon. What happens to ubuntu and the data stored there?
 
Wubi installs Ubuntu into a windows folder usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/f  in Windows and then shutting down properly.

> IMFFHO, better to start with a fresh install of ubuntu, and go from there. If you need more disk space you could get a scond hdd, or use gparted to resize some of your partitions and create some room.

+1

---

### Post by SonicRacer1412 on 2009-05-30
Wait a minute... I can burn ISOs to CD, but I can't burn other files to CD though.

---

