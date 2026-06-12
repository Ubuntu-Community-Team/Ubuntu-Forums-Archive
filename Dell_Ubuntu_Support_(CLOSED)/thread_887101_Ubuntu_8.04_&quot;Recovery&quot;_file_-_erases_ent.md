---
title: "Ubuntu 8.04 &quot;Recovery&quot; file - erases entire disk?"
date: 2008-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2008-08-11
I downloaded Ubuntu 8.04 from the Dell Support site ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)) as I had with Ubuntu 7.10, and I tried to install it on my XPS-M1330 laptop which dual-boots the pre-installed Vista with Ubuntu.  But instead of being a simple installation .iso, the Ubuntu 8.04 .iso file acts as a Dell "Recovery Partition" (see the link), and it warns that it will ERASE THE ENTIRE DISK!  Is this true, or will it just erase the contents of the partition that you point it at?

I prefer to use the Dell .iso file because it contains all the proprietary drivers drivers for my Dell laptop, whereas the 8.04 generic upgrade has presented me only with "Driver Hell".  

*TimDaniels*

---

### Post by superm1 on 2008-08-12
Yes, it will wipe your entire disk.  The scripting that it goes through to install the video drivers is very similar to the actions done by a normal Ubuntu installation that uses Restricted Drivers Manager (Jockey).

---

### Post by TimDaniels on 2008-08-12
> **superm1 said:**
> Yes, it will wipe your entire disk...

Now you tell me.  It completely wiped out everything on the disk, including Vista and Ubuntu 7.10, and it made unneeded FAT16 (165MB) and FAT32 (3GB) partitions, and the Ubuntu 8.04 is 143GB (more than 3 times what I need), and it's ext3 instead of ext2.  **And...** wireless and Bluetooth don't work anymore although the Broadcom driver is installed and enabled.  What a worthless POS this download is.  Why in the world do you guys offer it?  Why didn't you offer it as an installation ISO file - as did with Ubuntu 7.10 - instead of as a entire system eraser?

*TimDaniels*

---

### Post by superm1 on 2008-08-12
Hi Tim:
> **TimDaniels said:**
> Now you tell me.  It completely wiped out everything on the disk, including Vista and Ubuntu 7.10, and it made unneeded FAT16 (165MB) and FAT32 (3GB) partitions

There *was* a warning before the process began.  You had to manually ack it to continue.
This FAT16 partition provides diagnostic utilities as all Dell Factory installs do.  The FAT32 partition is for performing recovery installs without the DVD.
> 
, and the Ubuntu 8.04 is 143GB (more than 3 times what I need), and it's ext3 instead of ext2.  

Ext3 is Ext2 w/ journaling.  You will be able to read ext3 using an ext2 driver in another OS.  This is a factory install DVD.
> 
**And...** wireless and Bluetooth don't work anymore although the Broadcom driver is installed and enabled.

You will have to elaborate details on your BT controller and Wifi.  This install is no different than the 8.04 standard install other than that it is scripted.

> 
What a worthless POS this download is.  Why in the world do you guys offer it?  Why didn't you offer it as an installation ISO file - as did with Ubuntu 7.10 - instead of as a entire system eraser?
*TimDaniels*
It was offered because people asked for it.  This is the same thing that you will get from a factory install with a few extra things that are available in Ubuntu preinstalled (such as AMD/NVIDIA drivers).  If you want to use a dual boot, then you are better off installing Ubuntu 8.04 from a standard Ubuntu 8.04 CD/DVD and then manually doing things that are scripted into this.

*AMD/NVIDIA drivers
*Installing linux-backports-modules
*Installing flash
*Workarounds for other bugs.

---

### Post by TimDaniels on 2008-08-13
> **superm1 said:**
> 
It was offered because people asked for it.  This is the same thing that you will get from a factory install with a few extra things that are available in Ubuntu preinstalled (such as AMD/NVIDIA drivers)...

OK, I suppose you get lots of requests for various forms of system recovery, but I cannot fathom why you provide for download a restoration of partitions other than the Linux root partition and perhaps the swap partition.  Those other partitions are superfluous AND they take up Primary partitions AND allocated area that could be used for the OS.  Allowing for restoration of just the OS partition of a size and location selectable by the user, of a format selectable by the user, of a swap partition of size and location selectable by the user would be quite easy to implement in your script. AND it would make for a LOT more convenience and value for the user.  Since you guys didn't do that, I can only conclude that your goal was to LIMIT the file's convenience and use to just that provided in the original OEM installation and NO MORE.

Please play with this at your next staff meeting:  I chose and bought the XPS-M1330 with Vista pre-intslled BECAUSE it was also offered with Ubuntu pre-installed, and I assumed that installation of Dell's Ubuntu as a dual-boot would be easy.  Now you've taken that advantage away - along with the laptop's value.  Do you think that I will make that mistake again?  No way.  Somebody (or bodies) at Dell isn't looking at the big picture.

*TimDaniels*

---

### Post by superm1 on 2008-08-13
> **TimDaniels said:**
> OK, I suppose you get lots of requests for various forms of system recovery, but I cannot fathom why you provide for download a restoration of partitions other than the Linux root partition and perhaps the swap partition.  Those other partitions are superfluous AND they take up Primary partitions AND allocated area that could be used for the OS.  Allowing for restoration of just the OS partition of a size and location selectable by the user, of a format selectable by the user, of a swap partition of size and location selectable by the user would be quite easy to implement in your script. 

What you see in that ISO is the results of a lot of other variables in the factory that are outside of control during the installation.  The important part about this ISO was that it did exactly the same as the factory install.  Also when OEM installs are preseeded, you are unable to interactively change installation sizes.  Remember this ISO is supposed to handle "all" different configs that ship with Ubuntu.
> 
AND it would make for a LOT more convenience and value for the user.  Since you guys didn't do that, I can only conclude that your goal was to LIMIT the file's convenience and use to just that provided in the original OEM installation and NO MORE.

Bear in mind the purpose of this ISO; for people who purchased a system with an earlier version of Ubuntu that wanted to load the latest without having to do an upgrade.  People who purchased with Vista are better off doing their own dual boot using regular Ubuntu disks in a non OEM mode installation.
> 
Please play with this at your next staff meeting:  I chose and bought the XPS-M1330 with Vista pre-intslled BECAUSE it was also offered with Ubuntu pre-installed, and I assumed that installation of Dell's Ubuntu as a dual-boot would be easy.

There is no such thing as "Dell's Ubuntu".  The same live filesystem on that DVD is on the regular 8.04.1 DVD.  It is great that you are choosing to do a dual-boot, but clearly you have no need to have the recovery framework in place.  You are better off just doing a standard Vista install, leaving some free space and installing using a standard DVD.

Also, worth mentioning, if you have some hardware on your 1330 that isn't working, keep in mind that there is something hardware restricted on the Ubuntu OEM installs of systems because there are probems with it.  In terms of the bluetooth and wireless, all bluetooth configurations should be functional.  Wireless, you should have no trouble with the "G" offerings on the latest kernel, but the "n" offerings have not been tested.
> 
 Now you've taken that advantage away - along with the laptop's value.  Do you think that I will make that mistake again?  No way.  Somebody (or bodies) at Dell isn't looking at the big picture.

*TimDaniels*
I'm sorry that you aren't happy with the end result here, but I do ask, what do you think should be done so that someone else doesn't run into the connundrum that you have?  Keep in mind that install ISO can't be ran interactively.  For 8.10 we may just not ship our factory implementation image.  Since all of the drivers are available in Ubuntu it makes no sense to provide the same thing to customers.

---

### Post by starcannon on 2008-08-13
superm1 > For 8.10 we may just not ship our factory implementation image. Since all of the drivers are available in Ubuntu it makes no sense to provide the same thing to customers.

Please don't take away the added value that I get by downloading my Dell Ubuntu images for my Dell Ubuntu laptops. 

The complaining poster did not read the dialog boxes, he ended up paying the price for not reading the dialog boxes. Part of why I buy my Linux laptops from Dell as opposed to another company is that Dell provides official Dell restore disks and keep them up to date; lose that, and as far as my purchases go, Dell loses their edge, and I lose my incentive for putting Dell at the top of my list.

I would really be saddened to see a click happy end user ruin it for the rest of us. Indeed just the threat of removing value from my purchase is making me feel a bit heated and put off.

---

### Post by hyper_ch on 2008-08-14
I have yet to encounter any restore-cd by a manufactuerer that does not wipe out completely everything but uses an interactive process.

---

### Post by TimDaniels on 2008-08-14
> **superm1 said:**
> The important part about this ISO was that it did exactly the same as the factory install......

There was obviously a format and policy change since Feisty 7.10 because the .iso file offered by Dell for Feisty was in the form of an installation disk where one had control of partitioning, formatting, mount points, location of the Grub boot loader, etc.  What is now offered for Hardy 8.04 is a "recovery partition" where the script in the file controls the contents and formatting of the entire surface of the disk.  If a manufacturer were trying to discourage dual-boot systems, that is EXACTLY what it would do.


> There is no such thing as "Dell's Ubuntu"......

I think everyone reading this realizes that the term meant "Dell's customization of the installation of the current Ubuntu distribution".


> Also, worth mentioning, if you have some hardware on your 1330 that isn't working, keep in mind that there is something hardware restricted on the Ubuntu OEM installs of systems because there are probems with it.  In terms of the bluetooth and wireless, all bluetooth configurations should be functional.  Wireless, you should have no trouble with the "G" offerings on the latest kernel, but the "n" offerings have not been tested.

Currently non-working hardware is Broadcom's 802.11g Wi-Fi.  (What else is new?)  The finger reader and webcam I don't need.  But this "driver hell" is exactly what I assumed I would avoid by buying a laptop that the manufacturer also offered with Linux pre-installed.


> I'm sorry that you aren't happy with the end result here, but I do ask, what do you think should be done so that someone else doesn't run into the connundrum that you have?  Keep in mind that install ISO can't be ran interactively.  For 8.10 we may just not ship our factory implementation image.  Since all of the drivers are available in Ubuntu it makes no sense to provide the same thing to customers.

I don't think that it has yet sunk in:  You guys changed your policy without explicit notification that there had been a CHANGE.  Dell's Feisty .iso was offered as the image of an installation DVD, and I assume that it still is.  Dell's Hardy .iso is offered as the image of a "recovery partition" that wipes away everything on the disk.  You can say that it *says* that it erases the disk, but you should also know that in IT web discussions, "disk" and "drive" are repeatedly interchanged, and that is why I posted my question here.  With no reply visible for a day, I went with the assumption that the format of Dell's .iso file hadn't changed.  Fortunately, I had cloned my Vista installation before proceeding, but it still took me a day to restore Vista, download a generic Hardy installation file, burn it to CD, and then to install Hardy and restore the dual-boot scenario with Vista's BCD.

Here's a marketing hint:  If you guys want to encourage sales to customers like me who want to dual-boot Linux with Windows (with no support expense for Linux), just offer what you provided for Feisty - an installation file that has all the necessary drivers.  Whether or not that means that you're providing anything else than what is contained in a generic Ubuntu distribution, is largely irrelevant.  It's the *perceived* added value that counts (Marketing 101).  But now that we know that there is no added value in a Dell Vista laptop that is also offered in an "n" version (i.e. with Linux pre-installed), the advantage of there also being an "n" version has now evaporated.


*TimDaniels*

---

### Post by TimDaniels on 2008-08-14
> **TimDaniels said:**
> There was obviously a format and policy change since Feisty 7.10 because...

Please change all instances of "Feisty" to "Gutsy".  (In private conversation, I use "Manic Monkey" and "Daffy Duck" for 7.10 and 8.04, and the usual monickers escape me.)

*TimDaniels*

---

### Post by anjilslaire on 2008-08-15
uh, if you had bothered to read the official dell ubuntu wiki, you would have seen what you were getting into with the 8.04 ISO:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04")

> 
By using this disk, you will gain these customizations:

* You will have the Dell recovery framework put in place that allows you to do a recovery from a recovery partition.
* Flash will be pre-installed
* ATI or NVIDIA proprietary drivers will be pre-installed if you select during install
* linux-backports-modules-hardy will be pre-installed to enable the Wifi LED for Intel cards
* A workaround for suspend problems with high speed USB devices is included (see [https://bugs.edge.launchpad.net/dell/+bug/212660](https://bugs.edge.launchpad.net/dell/+bug/212660) for more information)

If you already have a Dell system with Ubuntu shipped on it, you should use that DVD to perform the recovery. The DVD playback software and media playback codecs are *NOT* included in this public image. 

DISCLAIMER: These images are unofficial Dell recovery media and are provided as-is. Do not call Dell Technical support with questions about this image, or software installed by this image, as they will not be able to help you. This image will erase all content on the machine and return it to a factory Ubuntu configuration. **If you want to dual boot a system with Windows, you will want to install using a standard Ubuntu 8.04.1 DVD.** If you have any questions, please send an email to the Dell linux-desktops mailing list. 


---

### Post by TimDaniels on 2008-08-15
> **anjilslaire said:**
> uh, if you had bothered to read

Uh, if you had bothered to read my posting, you would have realized that this marks an unannounced change in Dell's release policy since the Gutsy 7.10 ISO file was in the form of an installation file, not a restoration of the entire disk.  Furthermore, in the notes on the download page, it isn't clear whether "disk" means "disk" or "partition", i.e. "drive".  That is why I posted, but I got no timely reply.  I am not accusing Dell of fraud or lies, but only of changing policy in mid-stream without an explicit heads-up about it.

*TimDaniels*

---

### Post by anjilslaire on 2008-08-15
It's amazing that you're accusing people of not reading (comprehending?) what you're posting, when you are in the situation you're in by not reading & comprehending what the installer itself told you.

I'm not being rude, and I really do sympathize with the data you've lost because it wiped your drive, but you take your chances with any software if you don't have proper backups. 

No-one is trying to start a flame war with you, but you are being at least as unreasonable as you seem to think everybody else is.

---

### Post by hyper_ch on 2008-08-16
why should "disk" be comprehended as "partition"???

---

### Post by TimDaniels on 2008-08-16
> **anjilslaire said:**
> I'm not being rude, and I really do sympathize with the data you've lost because it wiped your drive, but you take your chances with any software if you don't have proper backups.

You yourself don't read.  I explicitly stated that I was fortunate to have cloned the Vista installation before running the Dell download file, and I never stated that I lost anything but a day's time that was needed to restore a dual-boot.

*TimDaniels*

---

### Post by TimDaniels on 2008-08-16
> **hyper_ch said:**
> why should "disk" be comprehended as "partition"???

As I have already explained in this thread -

1) Web discussions frequently interchange "disk" and "drive",
   and "drive" with "logical drive", i.e. a partition.  That
   is why I posted my inquiry.

2) Dell's download file for Ubuntu 7.10, called a
   "Dell OS Reinstallation 7.10 DVD ISO", **did not erase**
   other partitions:
   [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

3) But Dell's downoad file for Ubuntu 8.04, called a
   "Dell OS Reinstallation 8.04.1 DVD ISO", **does erase**
   all partitions.

*TimDaniels*

---

### Post by superm1 on 2008-08-16
> **TimDaniels said:**
> As I have already explained in this thread -

1) Web discussions frequently interchange "disk" and "drive",
   and "drive" with "logical drive", i.e. a partition.  That
   is why I posted my inquiry.

I would hope you can give more credit to an American company who primarily sells computers.

I responded to you later on the same day.

> 
2) Dell's download file for Ubuntu 7.10, called a
   "Dell OS Reinstallation 7.10 DVD ISO", **did not erase**
   other partitions:
   [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

It didn't provide a recovery framework either.  This was something developed for 8.04.

> 
3) But Dell's downoad file for Ubuntu 8.04, called a
   "Dell OS Reinstallation 8.04.1 DVD ISO", **does erase**
   all partitions.

*TimDaniels*
And it warns so both on the wiki and when you run the DVD.

I really think this is running and circles/beating a dead horse.   What the ISO does changed from 7.04, and that changed from 7.10, and it changed again for 8.04.  It's very possible it will change again for 8.10 if such an ISO is provided again.

---

### Post by TimDaniels on 2008-08-16
> **superm1 said:**
> What the ISO does changed from 7.04, and that changed from 7.10, and it changed again for 8.04.  It's very possible it will change again for 8.10 if such an ISO is provided again.

Well then don't keep calling by the same name, i.e. "Dell OS Reinstallation DVD ISO".  If it's an installation DVD, as 7.10 was, call it an **installation DVD**.  If it's an 'as delivered' **entire disk** recovery DVD, as 8.04 is, call it that.  If it's an **operating system** recovery DVD, call it _that_.  But don't keep calling it the same thing when its nature grossly changes with each release.

*TimDaniels*

---

### Post by hyper_ch on 2008-08-17
> **TimDaniels said:**
> 
1) Web discussions frequently interchange "disk" and "drive",
   and "drive" with "logical drive", i.e. a partition.  That
   is why I posted my inquiry.

So, you take web discussions as standard for all documentation?

---

