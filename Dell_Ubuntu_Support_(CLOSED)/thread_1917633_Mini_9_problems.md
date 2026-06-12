---
title: "Mini 9 problems"
date: 2012-01-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fnjoe99 on 2012-01-30
I bought a Mini 9 when they first appeared as a netbook for the family to use for emails and internet access.  It has been good value for nearly 3 years but there have been a couple of recent problems which I haven't been able to sort out with my very limited knowledge.

- the first occurred after I was invited to download a new version of Firefox.  The download appeared to run without errors, but the Firefox icon disappeared and has never been seen since.  Fortunately I discovered that we can get to the browser through the Gnome window so this has been annoying but not showstopping.

- a more serious problem has arrived with another invitation to update a product - this time Flash Player.  Again the update appeared to work but since then Firefox crashes quite frequently when browsing (crash=just shuts itself down).  It does not happen on every site or even always on specific sites (for example Youtube will work sometimes and not others).  On some sites it will not happen immediately but after navigating to another page.

I'm wondering if the later versions of these products are now incompatible with the original version of Unbuntu on my Mini 9, and whether they would disappear if I could install the latest version - although I have no idea how to do this.  Can anyone tell me whether updating Ubuntu would be worthwhile and, if so, whether there is an idiot's guide to how to do it?  Thanks in anticipation

---

### Post by ugm6hr on 2012-01-30
From memory, the Mini 9 came with Ubuntu 8.04 - hich is no longer supported.
Hence, I'm surprised it is offering any updates at all. But I'd definitely suggest you upgrade (re-install) a new version of Ubuntu.
The first question is: which model did you get?
In the USA, it was sold with 512MB RAM and 4GB HD (SSD) as the base spec - do you know which you got?
You can check with the commands (copy & paste these and the output back here)
```
free -m
sudo fdisk -l
```
The relevance of these numbers is that the base models (particularly 4GB HD) may be tricky to install the latest versions - although options remain.
PS: I have a 1GB RAM, 8GB HD Mini 9 that runs Linux Mint 12 - based on Ubuntu 11.10 - (almost) flawlessly.

---

### Post by fnjoe99 on 2012-01-30
free -m

             total       used       free     shared    buffers     cached
Mem:          1000        525        475          0         27        216
-/+ buffers/cache:        280        719
Swap:            0          0          0


sudo fdisk -1

janet@janet:~$ sudo fdisk -1
[sudo] password for janet: 
Sorry, try again.
[sudo] password for janet: 
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
janet@janet:~$ fdisk -v
fdisk (util-linux-ng 2.13.1)

Thanks for responding

---

### Post by ugm6hr on 2012-01-31
You have 1GB RAM - which is good.
But you typed the fdisk command incorrectly - try cut / paste:
```
sudo fdisk -l
```
It's a little "L" at the end, not a "1"

---

### Post by fnjoe99 on 2012-01-31
> Disk /dev/sda: 7682 MB, 7682605056 bytes
> 255 heads, 63 sectors/track, 934 cylinders
> Units = cylinders of 16065 * 512 = 8225280 bytes
> Disk identifier: 0x80d78fd6
> 
>    Device Boot      Start         End      Blocks   Id  System
> /dev/sda1               1           4       32098+  de  Dell Utility
> /dev/sda2   *           5         933     7462192+  83  Linux

---

### Post by ugm6hr on 2012-02-03
So - in fact you have an identical model to mine... 1GB RAM, 8GB SSD HD.
I would definitely suggest installing a new version.
It's pretty straightforward. In fact, the trickiest decision is which version to install.
The newer versions of Ubuntu have a new interface called "Unity" - which is very similar to the original Dell supplied (but not identical). Also - the fluendo codecs (required for playing mp3 / videos etc) are not included by default if you re-install. There is a way to save and restore them - documented somewhere in these forums - but I can't recall how. I never bothered - and just use the free codecs available.
I currently have Linux Mint 12 installed on mine (Gnome 3 interface with Ubuntu 11.10 backbone). I have previously had Ubuntu 10.04 on it - which worked fine too.
This may all seem complicated - if you are not bothered, and just want an easy install to allow internet / email - then the simplest option may be to install the same Linux Mint 12 I have - so that at least I'll be able to support you through the install.
To do so - you will need to download it:
[http://www.linuxmint.com/edition.php?id=94](http://www.linuxmint.com/edition.php?id=94)
And you need a blank 2GB USB stick - and another computer with Windows or a more modern version of Ubuntu to copy it on - instructions available in "2" on this page:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by fnjoe99 on 2012-02-04
Great thanks.  I now have a USB stick with Linux Mint 12 CD version (no codecs) ready to install.  Presumably I just need to reboot the Dell with the stick in place?  Are there any things I need to watch out for?

---

### Post by ugm6hr on 2012-02-04
> **fnjoe99 said:**
> Great thanks.  I now have a USB stick with Linux Mint 12 CD version (no codecs) ready to install.  Presumably I just need to reboot the Dell with the stick in place?  Are there any things I need to watch out for?
No - it's pretty simple.
[LIST=1]
[*]Backup any data / settings you need to keep
[*]Turn off Mini 9
[*]Plug the USB stick in
[*]Turn on Mini 9 - press 0 key (or maybe Del key) repeatedly as it boots to enter the boot menu
[*]Select USB from list
[*]It boots into an error (for some bizarre reason) - Don't panic!
[*]You have to type a command here to boot into Mint... I can't remember what it is right now - but try:
menu
boot
linux
help
(in that order - I'd have to turn off, find my boot USB and experiment to remind myself - but "help" should list all the available options - and one of them should look sensible)
[*]I just installed using the presets - which makes things easy. I can't recall anything too tricky here. 
[*]The default desktop has 2 panels - which is a pain on the Mini 9 - so I just removed the "mint menu" and the lower panel. I also set the upper panel to auto-hide. I can have a look through my settings to remind myself how I set up my desktop - but it's all tunred on and off from the advanced settings (extensions) options.
[/LIST]
Hope that helps - just post back with problems. I'll have a think about what else caused me a headache.
See this after installation: [http://ubuntuforums.org/showthread.php?t=1916674](http://ubuntuforums.org/showthread.php?t=1916674)

---

### Post by JC Cheloven on 2012-02-04
> **ugm6hr said:**
> 
(...)
[*]Turn on Mini 9 - press Del key repeatedly as it boots to enter the boot menu

On mines (I have 2 mini9's myself and bought yet another couple as gifts) it's the zero key ("0"). I'm in spain though. Specs are otherwise identical.

I've tried many OSes in these. For me, Ubuntu 10.10 Maverick Meerkat is the best fit for this machine. It will not be supported for much longer though... Lubuntu 11.04 and 11.10 play also nicely, but suffer from that battery drain kernel issue.

---

### Post by ugm6hr on 2012-02-04
> **JC Cheloven said:**
> it's the zero key ("0"). I'm in spain though. Specs are otherwise identical.
I think you might be right - I was doing this from memory - original edited.

> **JC Cheloven said:**
> I've tried many OSes in these. For me, Ubuntu 10.10 Maverick Meerkat is the best fit for this machine. It will not be supported for much longer though... Lubuntu 11.04 and 11.10 play also nicely, but suffer from that battery drain kernel issue.
What issue? I haven't noticed any problem - although battery life has never been good on any OS on the device.

As for my Gnome 3 desktop settings (in "Advanced Settings"):
I have turned off all options in "Desktop" tab
I have turned off Menu, Monitor Status and Bottom Panel Shell Extensions and turned on Autohide.
I think this makes a cleaner desktop (in fact - the desktop is completely blank on booting - you have to move mouse to top / top-left to reveal panel.

---

### Post by JC Cheloven on 2012-02-04
> **ugm6hr said:**
> 
What issue? I haven't noticed any problem - although battery life has never been good on any OS on the device.

From V3.x on, there is an [issue with the linux kernel]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131"), using [more power]("http://ubuntuforums.org/showthread.php?t=1822629") than previous versions. It has been largely [commented]("http://www.phoronix.com/scan.php?page=news_item&px=OTU2MA") in the net, and I quite noticed it in the mini9's. 

[There]("http://danielj.se/2011/11/16/how-to-fix-powerbattery-problem-with-linux-kernel-3-x-on-ubuntu-11-10/") [might]("http://www.pcworld.com/businesscenter/article/244277/new_kernel_patch_slashes_linuxs_power_appetite.html") be solutions available soon. Hopefully 12.04 will include some nice one. I'd rather not using something as [jupiter]("http://www.jupiterapplet.org/") (mono based...). BTW, I tried it and did very little improvement for me.

Cheers

---

### Post by fnjoe99 on 2012-02-05
Just waiting for the family to clear off the Mini 9 so I can do the re-install.  Meanwhile, you mentioned codecs.  Are these offered when a media product finds it needs them when running?  Or do I need to find them and download them myself?  If so, are there essential / most often needed lists anywhere?  Thanks for the continued help.

---

### Post by JC Cheloven on 2012-02-05
Common proprietary codecs you may want are for mp3, flash, and perhaps dvd playback. Some fonts, for compatibilty with documents/sites may also be desirable. Assuming you'll use maverick, this single line will do it all:

```
sudo wget http://www.medibuntu.org/sources.list.d/maverick.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
``` 

If you install a different ubuntu version, change the word 'maverick' as apropriate.
Note: you'll be adding a repository called 'medibuntu', which (I think) has nothing to do with ubuntu, and contains all proprietary stuff that can't be packaged with the distribution. It is perfectly legal for the final user to install it, though.

---

### Post by ugm6hr on 2012-02-06
> **fnjoe99 said:**
> Just waiting for the family to clear off the Mini 9 so I can do the re-install.  Meanwhile, you mentioned codecs.  Are these offered when a media product finds it needs them when running?  Or do I need to find them and download them myself?  If so, are there essential / most often needed lists anywhere?  Thanks for the continued help.

That was why the earlier link was to the Linux Mint DVD - which includes all standard codecs. I think you downloaded the CD version - which I believe excludes codecs (and perhaps some other applications). I presumed that was a deliberate choice on your part - apologies for not making that clearer.

But yes - you can add them later. And Ubuntu (and Mint) do try and download them as required - but I find it a cumbersome thing to have to do at intervals.

PS: Mint 12 is 11.10 (oneiric) based (instead of maverick).

---

### Post by fnjoe99 on 2012-02-07
Recreated the Boot USB using the DVD version of Mint 12.  The 0 key on startup brought up a list to select from incl. USB so that was straightforward (no error, and no apparent need for a command).  The installation seems to have completed although it was left with the identitity picture window with a progress bar with the cryptic message "Ready when you are" - continue didn't seem to do anything, so closed the window.  

I'm left with some initial problems though:

1.  When I shut down and restart without the USB, Mint fails to start.  Rebooting with the USB in place works ok (I selected Start L Mint, not Start L Mint Compatibility Mode - is that right?).  How can I close down with a stable system for restart without the USB stick?

2. Most serious:  I have no network connection.  The Wireless settings page says "firmware missing" - does that mean a Dell driver is required?  How would I install that if so?  I have tried a wired connection but although the Mini9 tries to connect, it fails and eventually disconnects itself.

3. Some windows (e.g Appearance under System Settings) are too long for the Mini9 screen and don't have a side bar or allow scroll down - is there a setting to overcome this?

Next I'm going to try to restore documents and emails from the backup I took - help on the above would be gratefully received.

---

### Post by fnjoe99 on 2012-02-07
And I'm struggling with the restore too.  I have my back up on a USB hard disk.  It was created by the backup function in Evolution evolution-backup.tar.gz  Evolution seems to have been replaced by Thunderbird in Linux Mint.  I guess I will need to install Evolution when I have network access, restore and then migrate - or is there an easy way to restore direct to Thunderbird?

---

### Post by ugm6hr on 2012-02-07
I'll try and address your issues in turn:

1. This is just wrong. I suspect your install has not completed correctly. Not really sure how - but it sounds like perhaps Grub (the "bootloader" which starts the operating system) may have installed on the USB instead of the Mini's HD. To help clarify - what exactly happens when you start up without USB plugged in? 

2. Yes - I always forget that the Broadcom requires installation of firmware. However, I don't recall having a problem connecting with an ethernet cable. We may have to do some diagnostics. Perhaps more evidence of a failed installation?
Once wired is working, I think the following still gets wifi up and running (with a reboot as well):
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```
Just checked - the LAN card is definitely supported out of the box: [http://www.ubuntu.com/certification/catalog/component/pci:8136:10EC-NETWORK](http://www.ubuntu.com/certification/catalog/component/pci:8136:10EC-NETWORK)
You can check if yours is identical to mine with the command
```
lshw -class network
```


3. This was a problem with the original Ubuntu version too... Use Alt+Left click anywhere on window with mouse to drag windows around (past window borders).

4. I am no expert - I have never used Evolution - but yes, I see no problem in installing Evolution on Mint 12. You can obviously uninstall any apps you don't want / need.

In summary - I think there was a problem with your installation - since I did not have these issues with identical hardware. Simple thing to check (a common problem with downloads):
md5sum [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Should be ee3d6e2ca498bc7685b7f17cdb5f2eea

If there is any suspicion - try using a Torrent to update your iso file - it will check for errors and auto-correct.

---

### Post by fnjoe99 on 2012-02-08
1. Does seem that the installation didn't complete.  On booting without the USB I get the Ubuntu logo then:

libudev: udev_monitor_new_from_netlink_fd: error getting socket: Invalid argument
mountall.mountall.c: 3666: Assertion failed in main: udev_monitor = udev_monitor_new_from_netlink (udev,"udev")
General error mounting filesystems.

2. Wired now working when connected straight into the router rather than the signal booster.

mint@mint ~ $ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:e7:2d:1b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.5 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0610000-f0610fff memory:f0600000-f060ffff memory:f0620000-f063ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:24:d2:2a:ca:83
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
mint@mint ~ $ 


I'm struggling with how to md5sum on the usb so I think I'll clear it, re-load and re-install

---

### Post by fnjoe99 on 2012-02-08
Progress!  Reinstall worked and your code has set up wireless access.  Thanks again

Working on recovering backed up emails now.

---

### Post by fnjoe99 on 2012-02-08
Have seen battery power problem your described and have tried to use the dconfig-editor route to change the values as suggested but the config editor is empty (ie nothing is shown for org or any other headings in the LH panel.  Any suggestions on how to access the rest of the hierarchy?

---

### Post by ugm6hr on 2012-02-08
I didn't use dconf-editor - just copy / paste the following commands into Terminal:
```
gsettings set org.gnome.settings-daemon.plugins.power percentage-critical 10
gsettings set org.gnome.settings-daemon.plugins.power percentage-action 9
gsettings set org.gnome.settings-daemon.plugins.power use-time-for-policy false
```
I (perhaps foolishly) just copied them blindly from the source quoted - but it seems obvious what each does. I think it is the final command that is most important to fix the bug - and the others merely ensure your Mini will still power-off if the battery is low.

---

### Post by fnjoe99 on 2012-02-09
Well I think I can mark this thread as solved.  Mint seems stable and the family are getting to grips with the new look.  We gave up trying to recover the backed up Evolution mail and have viewed it as a good clearout opportunity.

Thanks once again for all the advice and support - great to know how much help is available!

---

### Post by ugm6hr on 2012-02-09
No problems. Glad things are resolved... Mint 12 / Gnome 3 are not perfect - but they are actually pretty good on a netbook.
As I said - removing the bottom panel and auto-hiding the top are good space savers. Chrome is also much more space efficient than Firefox.

Any problems - just post back here. Glad your problems are resolved. Consider a new upgrade / reinstall in about a year or so - by which time 12.04 (and derivatives) should be pretty stable, and then offer 4-5 years of support.

---

### Post by fnjoe99 on 2012-02-11
New problem!   Mobile  phone will no longer connect via USB (in order to upload photos etc. from its folders).  Mini 9 does recognise that it's connected.  USB stick and USB hard disk work fine.

---

### Post by ugm6hr on 2012-02-11
> **fnjoe99 said:**
> New problem!   Mobile  phone will no longer connect via USB (in order to upload photos etc. from its folders).  Mini 9 does recognise that it's connected.  USB stick and USB hard disk work fine.

I think you'd be better off starting a new thread for this one.
Feel free to post the link to the new thread here, and I'll take a look.
Be sure to include more detail:
What mobile phone?
Did that phone work with 8.04?
Has it worked with Linux Mint 12 at all?
How do you know it does "recognise that it's connected"?
Ad the output from following command with phone plugged in and again when removed (put in code # markers).
```
lsusb -vv
```

---

### Post by fnjoe99 on 2012-02-12
Thanks for the suggestions:


New thread: t=1924185 Phone connection to Mini 9 / Mint 12



PS Not sure what your last point about # markers means or how to do it

---

### Post by bobarry on 2012-05-15
So you have Linux Mint 12 running with the Gnome interface - NO Unity required?
Is it easy to setup?  I cannot for the life of me get used to the Unity confusion.

bo

---

### Post by ugm6hr on 2012-05-16
> **bobarry said:**
> So you have Linux Mint 12 running with the Gnome interface - NO Unity required?
Is it easy to setup?  I cannot for the life of me get used to the Unity confusion.

bo

Yes - to all questions... Just follow the advice in this thread to replicate!
Although I've now moved on to 12.04 with Unity 2D myself. Unity is growing on me...

---

