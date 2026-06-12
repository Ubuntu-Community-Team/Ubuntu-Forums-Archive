---
title: "Unable to get MP3player to be detected."
date: 2010-07-12
forum: Desktop Environments
---

### Post by jim_naisium on 2010-07-12
Hi,

I have a Coby MP826-8G USB MP3 player that when plugged into my Windows XP machine is detected, installs, and lets you drag files into it and then plays them without any problems.

When I plug it into my Ubuntu Linux v10.04 PC (completely different PC) the USB icon on the MP3 player lights up flashes a couple of times, then it starts going into battery charge mode so I know that it is getting a connection to the PC, but when I run LSUSB this is what I get:

landon@Core2Duo:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
landon@Core2Duo:~$

It does not show up in Places - Computer either, although if I plug in my old Phillips 512meg MP3 player it works just fine.

If I run GPARTED it shows both of my SATA hard drives and the SD memory card for my camera that is plugged into the 12-in-1 card reader that is listed above in the LSUSB dump.

Any suggestions on getting this to work?

---

### Post by mikeymo1741 on 2010-08-11
I have the same issue with a Coby MP815.   It charges, but will not be recognized as a hard drive.  I've tried it in both USB modes.  

I dual-boot to XP, and Windows sees it fine in either mode.  

I've heard it has something to to with the firmware in the player, but I've not seen anything definitive on it.   It would be nice to have a solution.

---

### Post by Deathspawn on 2010-12-16
It works with virtualbox-nonfree, and you also have to go through some steps to make sure you can use USB devices, which are posted here: [http://ubuntuforums.org/showpost.php?p=9756001&postcount=2](http://ubuntuforums.org/showpost.php?p=9756001&postcount=2)

After you get say Windows XP installed on VirtualBox, plug it in (The mp3 player) and go to Settins > USB and add a filter for it based on device connected, so you will have a filter that says COBY. After that, unplug the mp3 player and boot windows. After Windows is booted, plug in the mp3 player and Windows should detect it and start installing it as a removable device.

---

### Post by jim_naisium on 2011-09-04
I didn't much worry about this since my last car was totaled and my new car didn't have any way to plug an MP3 player into it, I have another stereo in it now that I can plug the MP3 player into and would like it get this working.

I seem to have three problems...

1 - If the MP3 player is plugged into the USB port and I boot up the PC it hangs and sometimes Ubuntu won't load, or if Ubuntu does load neither the keyboard or the mouse's lights will light up leaving me no way to do anything. If the MP3 player is not plugged into the USB port Ubuntu loads like it should.

2 - If I plug in my USB thumb drive (it is storage not the MP3 player) it detects it and lets me use it but is read only, same with my digital camera (read only), both of these devices worked fine under Ubuntu 10.10. 

3 - Assuming the PC boots up and I can login normally... when I plug in the COBY MP3 player it lights up and goes into recharge mode but no icons appear on the screen like they do for the camera and thumb drive.

The MP3 player works like it is supposed to if I plug it into my other PC that runs Windows XP, any suggestions on getting it to work with Ubuntu?

---

### Post by larrinski on 2011-10-10
Sorry to bump, but my son just got the Coby MP826 for his birthday. I've got the same problem. I don't have Windows, so Virtualbox is not an option. 

Has anyone got an idea on how to get it working?

---

### Post by zzarko on 2011-10-23
I got the same player (Coby MP826-8G), and it doesn't work in Ubuntu (11.04 nor 11.10). There is a thread for libmtp at sourceforge:
[http://sourceforge.net/projects/libmtp/forums/forum/535190/topic/3931702](http://sourceforge.net/projects/libmtp/forums/forum/535190/topic/3931702)
about this player, but it was started last year, and still no response. I guess the chances are very slim at the moment that this will work with anything but Windows...

---

### Post by EtienneG on 2012-01-25
I got it to work.  Basically, it needs the "usb-storage.quirks=1e74:4631:mw" kernel parameter.  A straightforward way to add that is to create a file /etc/modprobe.d/coby-option.conf with the following content:

```

options usb-storage quirks=1e74:4631:mw

```

Then, unload/reload the usb-storage module with the commands:

```

$ sudo modprobe -r usb-storage
$ sudo modprobe usb-storage

```


In the above example, 1e74:4631 is the USB ID of my Coby MP826-8G player.  This may differ somewhat if you have a different model.  You can find the USB ID of your player with the "lsusb" command, and adjust the line above as appropriate.

I have tested on precise and lucid.  Transfer is pretty slow, but it works.

---

### Post by zzarko on 2012-03-04
> **EtienneG said:**
> I got it to work.  Basically, it needs the "usb-storage.quirks=1e74:4631:mw" kernel parameter...EtienneG, thans for this solution. I don't know how you discovered it, but it really works!

---

### Post by Mudito on 2012-06-15
My case is a little bit worse:

I have a non-identifiable MP3 and it is not  recognized in 12.04, I don't know the brand because it is one of those  made in China and re-branded in the sale country (New Zealand, in my  case). It is seen as standard USB disk drive by Win XP on the same  machine, in Ubuntu it only charge though, cannot access the contents.   Here is some output:
 *cat /proc/partitions
major minor  #blocks  name
    8        0   58605120 sda
   8        1   15431648 sda1
   8        2          1 sda2
   8        5   42194336 sda5
   8        6     976896 sda6
  11        0    1048575 sr0
 *sudo fdisk -l
 Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25472547
    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30863359    15431648+   7  HPFS/NTFS/exFAT
/dev/sda2        30865406   117209087    43171841    5  Extended
/dev/sda5        30865408   115254079    42194336   83  Linux
/dev/sda6       115255296   117209087      976896   82  Linux swap / Solaris
 *lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0930:0403 Toshiba Corp.
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 005: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mo

                 [B]
[/B]

---

### Post by Mudito on 2012-06-15
Solved using EtienneG's techinique. Mine was " 4641"  instead of " 4631", thanks!

---

### Post by SeijiSensei on 2012-06-15
Can you post a link to setting this "quirks" parameter?  I've had problems with connecting cell phones as a USB mass storage device.  Though there are bug postings at Launchpad on this subject, I've never gotten a good response from the kernel developers.

---

### Post by davposs on 2012-07-17
Big vote of thanks from me to EtienneG.

Tweak worked for me also - across two hosts - one at 11.10 and one at 12.04.
Like Mudito - mine was a 1e74:4641
Seems to be a pretty solid tweak

---

