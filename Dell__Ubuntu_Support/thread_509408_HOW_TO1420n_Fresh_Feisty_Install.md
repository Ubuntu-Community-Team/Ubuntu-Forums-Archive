---
title: "HOW TO:1420n Fresh Feisty Install"
date: 2007-07-25
forum: Dell  Ubuntu Support
---

### Post by specker on 2007-07-25
After the recent purchase of a Dell 1420n notebook I felt it was only appropriate to wipe the hard drive clean and start from scratch.  Needless to say I encountered some issues doing a fresh install of Feisty.  Here is my process to get everything working again.  What works:
Wireless AND Wired
Intel Video
Compiz
CDROM recognition
Sound 
Modem

1. Packages Partion
When you install Feisty from the alternate cd xorg will break.  So we need to install some packages from the command line.  However, I was unable to get wireless internet working from the command line.  So I used the PCLinuxOS live cd (it boots fine) to download the following packages and copy them to a new parition.  MEPIS also works. You will want to make a partition on your hard drive to hold these new packages.  The partition only needs to be about 60mb.  After you install Ubuntu from the alt-install cd you will need to access these files on that new partition.  

Download and copy these to your new partition:

[linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb")
[linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.28_i386.deb]("http://ubuntu.oss-hcm.gov.vn/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.28_i386.deb")
[linux-image-generic_2.6.20.16.28.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.20.16.28.1_i386.deb")
[linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb")
[linux-headers-2.6.20-16-generic_2.6.20-16.29_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16-generic_2.6.20-16.29_i386.deb")
[linux-headers-2.6.20-16_2.6.20-16.29_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16_2.6.20-16.29_i386.deb")
[xserver-xorg-video-intel_2.1.1-0ubuntu2_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.1.1-0ubuntu2_i386.deb")

If you don't have a Feisty alternate install cd you will want to get that now.  Exit PCLinuxOS.

2. Install Ubuntu using the alternate install cd as normal but be sure to add a mount point for your new partition, so it is easily available later. Do not install Ubuntu on to the partition you saved those previous files to.  It will erase them.  That's bad!  When prompted during the install choose manual partitioning.  Set a mount point for the new partition and choose automatic partitioning for the rest of the free space on your drive.  

3. X Is Broken
After the install you should reboot to a broken X.  Get yourself to the command line and install all those packages you just downloaded.  I installed them in this order:
```
sudo dpkg -i linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
sudo dpkg -i linux-image-generic_2.6.20.16.28.1_i386.deb
sudo dpkg -i linux-headers-2.6.20-16_2.6.20-16.29_i386.deb
sudo dpkg -i linux-headers-2.6.20-16-generic_2.6.20-16.29_i386.deb
sudo dpkg -i linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.28_i386.deb
sudo dpkg -i linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb

```I reboot here, not sure if you have to.  When X breaks again remove the old i810 package:
```
sudo apt-get remove xserver-xorg-video-i810
```Install the new intel package:
```
sudo dpkg -i xserver-xorg-video-intel_2.1.1-0ubuntu2_i386.deb
```Now:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```Choose intel and hit OK.  Then choose 1280x800.
Reboot:
```
sudo shutdown -r now
```It should reboot to the login screen.

4. Wireless Internet
Wireless should be working now so do some updates:
```
sudo apt-get update
sudo apt-get upgrade

```5.  CDROM Recognition
```
sudo gedit /etc/initramfs-tools/modules
```Add "piix" no quotes, save and exit.
Then:
```
sudo update-initramfs -u
```Reboot and the CDROM should be recognized.

6.  Sound
Create /etc/modprobe.d/1420-sound and add:

```
options snd-hda-intel model=3stack 
```Create /etc/acpi/suspend.d/86-1420-sound.sh and add:

 ```
#!/bin/sh
 killall mixer_applet2
 modprobe -r snd_hda_intel
```Create /etc/acpi/resume.d/66-1420-sound.sh and add:

 ```
#!/bin/sh
 modprobe  snd_hda_intel
```Add to /etc/rc.local:

 ```
modlist=`lsmod | grep snd_hda`
 [ -z "$modlist" ] && modprobe snd_hda_intel

```Reboot and you should hear something.

7.  Modem (untested)
Download [hsfmodem_7.60.00.06oem_i386.deb]("http://ftp.us.dell.com/comm/hsfmodem_7.60.00.06oem_i386.deb")
```
sudo dpkg -i hsfmodem_7.60.00.06oem_i386.deb
```
8.  Compiz
This will fix issues with the desktop-effects and screensaver.  I haven't gotten up the guts to test it on compiz-fusion.
Enable the Feisty proposed updates from System->Administration->Software Sources->Updates
```
sudo apt-get update
sudo apt-get upgrade
```Updates some mesa packages.


9.  Totem/Compiz Fix
Video doesn't seem to want to play in totem with desktop-effects activated.  Here is the workaround.
```
gstreamer-properties
```Select Video and change Default Output Plugin to X Window System (No Xv).

10.  Wired Internet Connection
Check this [thread]("http://ubuntuforums.org/showthread.php?t=511974&highlight=upgrade+feisty+to+gutsy+kernel").
Download his script and run it.  It will set you up with the Gutsy kernel.  Wired then works out of the box.

You should be up and running at this point.  Let me know how it works for you.  I have done this numerous times now and I get consistently good results.  

Credit where credit is due:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Factory_Installation_Details](http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Factory_Installation_Details)
[http://ubuntuforums.org/showthread.php?t=494943&highlight=intel+x3100](http://ubuntuforums.org/showthread.php?t=494943&highlight=intel+x3100)
[https://bugs.launchpad.net/xorg-server/+bug/111257](https://bugs.launchpad.net/xorg-server/+bug/111257)

---

### Post by notwen on 2007-07-25
Assuming you were able to get regular Compiz working, would you guess that Beryl would be functional as well?  I was concerned when I saw lots of 1420n owners having issues w/ their Intel GFX. I prefer Beryl's config window more than gconf-editor to change settings in Compiz.  My 1420n should arrive mid August hopefully. =]

---

### Post by specker on 2007-07-25
To be honest I don't know because I haven't tried it.  My guess would be yes, it would work.  Those updated mesa packages in the proposed updates did the trick for the basic feisty compiz.

---

### Post by Shay Stephens on 2007-07-25
> Choose intel and hit OK. At this point two/thirds of the time my screen flashes and goes blank. Don't worry just reboot.
After the reboot you should see the login screen. At this point I login and run:
Code:

sudo dpkg-reconfigure -phigh xserver-xorg

Choose intel again and 1280x800 resolution.
Reboot again just to make sure everything is working.

I have a question.  I am trying to get a Dell 1800MP projector working with the 1420N and the projector just says "out of range".  So I tried your instructions here and now the projector works (yay), however, my LCD screen now looks like the color depth is 65k colors instead of 16 million colors.  Also the resolution options have changed to:
1024x768
1400x1050
1280x1024
1152x864
832x624
800x600
640x480
1400x1400

When I check the xorg.conf file this is what is listed
1280x1024
1280x800
1024x768
800x600
640x480

Anyone have any idea how to get 1280x800 and a 16 million color depth?  It is already listed in the xorg.conf file but the options listed at first is all I see in the screen resolution preferences app.

---

### Post by specker on 2007-07-25
What is the default depth set to in your xorg.conf?  Should be at 24, I believe.  Here is a copy of the Screen section of my xorg.conf file.  I guess your could see if there are any differences.
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Hope it helps!

---

### Post by rickyjones on 2007-07-25
Does suspend and hibernate work with this as well? I'm considering the 1420N for my next laptop.

Thanks,

-Richard

---

### Post by specker on 2007-07-25
Yes.  Suspend and Hibernate seem to work just fine.

---

### Post by rickyjones on 2007-07-25
> **specker said:**
> Yes.  Suspend and Hibernate seem to work just fine.

Thank you for the update! Suspend/Hibernate are a requirement of mine for using a laptop - I definitely appreciate the work that Dell and Ubuntu are putting into this venture.

-Richard

---

### Post by specker on 2007-07-25
Overall I'm pretty happy with the system.  The fresh install process right now is a bit of a pain but I would hope most of that will be taken care of in Gutsy.

---

### Post by LMP900 on 2007-07-25
> **specker said:**
> Yes.  Suspend and Hibernate seem to work just fine.

Thank you for confirming this. :)

I cannot wait until my 1420N arrives. Threads such as this one will definitely come in handy when I run into issues. I will certainly try to contribute as much as I can once I sort everything out.

---

### Post by gaojiemin on 2007-07-26
I also have a 1420 with Intel video, and I've followed your initial directions with the exception that it's a 64bit install (so all the files end in amd64.deb instead of i186.deb). The first step works fine, yet when I try to run the xserver package I get the following error.
> 
(Reading database ... 103538 files and directories currently installed.)
Unpacking xserver-xorg-video-intel (from xserver-xorg-video-intel_2.1.0-1ubuntu1_amd64.deb) ...
dpkg: error processing xserver-xorg-video-intel_2.1.0-1ubuntu1_amd64.deb (--install):
 trying to overwrite `/usr/lib/libI810XvMC.so.1.0.0', which is also in package xserver-xorg-video-i810
Errors were encountered while processing:
 xserver-xorg-video-intel_2.1.0-1ubuntu1_amd64.deb

Any idea what this means or how to get around this? I can get xserver working fine with vesa drivers, but would really like the extra screen resolution.

---

### Post by specker on 2007-07-26
Yes thank you.  I left a step out.  Darn it.  Before installing the xserver-xorg-video-intel package you must:
```
sudo apt-get remove xserver-xorg-video-i810
```

Then install the new xserver package. 
SInce you already tried to install the intel package you might want to run this first:
```
sudo apt-get install -f
```
 Sorry about that.  The line got cut out for some reason.

---

### Post by apswartz on 2007-07-26
Did you have any issues with your touchpad not being recognized (or scrolling). It doesn't work on my new 1420n.

---

### Post by specker on 2007-07-26
No I haven't had any issues with the touch pad.  Did it show up from Dell not working?  Or did it just happen randomly.

---

### Post by apswartz on 2007-07-26
It showed up not working.

---

### Post by specker on 2007-07-26
Hmm. Interesting.  My touch pad has been working consistently even when I was running the Dell factory install.  I wish I could help you but I don't have the slightest idea.  I checked in the bios to see if there was a switch in there but couldn't see anything obvious.  I'll keep looking around and see if I can find something.  It seems like there is a way to lock the touchpad.  But I can't remember.

---

### Post by specker on 2007-07-26
apswartz: Do you have a section in your /etc/X11/xorg.conf that looks like this?
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

---

### Post by gaojiemin on 2007-07-26
> **specker said:**
> Yes thank you.  I left a step out.  Darn it.  Before installing the xserver-xorg-video-intel package you must:
```
sudo apt-get remove xserver-xorg-video-i810
```

Then install the new xserver package. 
SInce you already tried to install the intel package you might want to run this first:
```
sudo apt-get install -f
```
 Sorry about that.  The line got cut out for some reason.

I did some digging around and figured that out, but then I got another error that said I needed an updated xserver-xorg-core package. So I ditched that idea and tried out the method listed on Dell's linux wiki ([[COLOR="Blue"]http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Misc_Intel_Video_Issues[/COLOR]]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Misc_Intel_Video_Issues")). What they don't tell you there is that 915resolution_0.5.3-0ubuntu1_i386.deb requires an updated libc6 (2.6-2 seemed to do the trick) [[COLOR="Blue"]http://packages.debian.org/testing/libdevel/libc6-dev[/COLOR]]("http://packages.debian.org/testing/libdevel/libc6-dev"), which in turn requires an updated Tzdata. That seems to have gotten the i810 driver working, and after running sudo dpkg-reconfigure xserver-xorg (or whatever) and rebooting several times I even have the 1280x800 resolution. Next step: wireless!

As an aside, since installing the those six packages listed at the start of your guide, I have two versions of ubuntu listed in the grub boot menu, 2.15 and 2.16 (I think). Did this happen on your system too? And thanks a bunch for the guide, at the very least so far it's definitely gotten me on the right track.

---

### Post by specker on 2007-07-26
That's interesting about the xserver-xorg-core.  I didn't run into that issue.  I might try another reinstall just to make sure I didn't omit another step.:confused:
I also have those two kernel versions in my grub menu.  That's normal. Just make sure you are booting to the new one.  The wireless for me worked right off the bat, I didn't have to do anything other than connect to my network.  Let me know if you are having an issue with that.  
Once the intel video issues are solved life gets a lot better.

Cheers

---

### Post by bakketti on 2007-07-27
What about the ethernet card? That is my only piece of hardware that isnt working.

Are we waiting on the updated tg3 driver from Dell?

---

### Post by specker on 2007-07-27
Yes, that is exactly what I'm waiting for.  As of yet I haven't been able to find it anywhere.  Check this for more info: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/121030]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/121030")
If you can find that update post back.

---

### Post by timseal on 2007-07-27
Are you saying that the ethernet card doesn't work in the 1420N?

---

### Post by specker on 2007-07-27
From the factory yes.  If you do a fresh install, no.  There is a fix out there but I have not been able to find the package as of yet.

---

### Post by timseal on 2007-07-27
OK, so hopefully the module will be in Gutsy then?

---

### Post by specker on 2007-07-27
As we speak I'm trying a dist-upgrade to Gutsy.  We will see how this goes?

---

### Post by gaojiemin on 2007-07-27
My wireless is not working. Ubuntu seems to recognize the hardware, though it doesn't show up in network settings. Below is some terminal output.
> sudo lspci -v

09:00.0 Ethernet controller: Broadcom Corporation Unknown device 1713 (rev 02)
        Subsystem: Dell Unknown device 01f3
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fe5f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1020
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fe8ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

 sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:fe8ff000-fe8fffff irq:17
  *-network
       description: Ethernet interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fc:64:7b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=full latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:fe5f0000-fe5fffff irq:17

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions

I remember reading somewhere that occasionally there's a problem with the processor not connecting to the right pci bus, but I can't find that again. Could that be the issue? As you can see above it reads "pci@0c.00.0", when it should be at 12 according to Windows.

---

### Post by specker on 2007-07-27
I don't know mine has always just worked.  Are you still running the factory install?

As a side note I tried to install gutsy via update-manager,live cd and alternate cd with absolutely no luck.  So I'm back to feisty.

---

### Post by timseal on 2007-07-27
> **specker said:**
> I don't know mine has always just worked.  Are you still running the factory install?

As a side note I tried to install gutsy via update-manager,live cd and alternate cd with absolutely no luck.  So I'm back to feisty.

I would hope that when Gutsy is released, the Dell drivers will be in it.  They are releasing the source, right?

---

### Post by specker on 2007-07-27
I would hope when gutsy is released you'll be able to pop in the live cd and everything installs with out a hitch.  We will see what happens.  The  two major issues I'm running into right now with gutsy:
1. /bin/sh: can't access tty; job control turned off
Live cd does not boot and the "modprobe piix" fix doesn't work.
2. Alternate install cd hangs about half way through installing packages.  Screen flickers and turns a multitude of colors.  Very abstract.

---

### Post by timseal on 2007-07-27
> **gaojiemin said:**
> My wireless is not working. Ubuntu seems to recognize the hardware, though it doesn't show up in network settings. Below is some terminal output.


I remember reading somewhere that occasionally there's a problem with the processor not connecting to the right pci bus, but I can't find that again. Could that be the issue? As you can see above it reads "pci@0c.00.0", when it should be at 12 according to Windows.

I know it sounds dumb, but have you checked to see if the wireless is switched on?  (Somebody else did that in another thread[http://ubuntuforums.org/showthread.php?t=510218]("http://ubuntuforums.org/showthread.php?t=510218"))

---

### Post by gaojiemin on 2007-07-27
Yeah, I'm an idiot. That was the problem. Thought the circle was on the other side.

---

### Post by scarboni on 2007-07-27
For those of you who need to reinstall the OS but don't have to alter the Dell partition scheme please realize that the factory image can be reinstalled via the GRUB menu.  With this you don't have to worry about patching the drivers back into it since it will run the same way as when you got it.

To activate it press ESCape immediately following the Dell logo to initiate the GRUB menu.  You will then see an option to restore to factory defaults there.

---

### Post by specker on 2007-07-27
> **scarboni said:**
> For those of you who need to reinstall the OS but don't have to alter the Dell partition scheme please realize that the factory image can be reinstalled via the GRUB menu.  With this you don't have to worry about patching the drivers back into it since it will run the same way as when you got it.

To activate it press ESCape immediately following the Dell logo to initiate the GRUB menu.  You will then see an option to restore to factory defaults there.

Yes, a valid point to reaffirm.  The how to is based on me being an idiot, wiping the hard drive clean and trying to get it all back up to speed.

---

### Post by sciurus on 2007-07-27
The scripts used by dell to fix an install are at [http://ubuntuforums.org/attachment.php?attachmentid=38858&d=1185154517](http://ubuntuforums.org/attachment.php?attachmentid=38858&d=1185154517)

---

### Post by specker on 2007-07-27
Where did you find that at?  From the reinstall partion?

---

### Post by sciurus on 2007-07-28
Yes, that's some of the data from the reinstall partition. The basic operations are
reformat, untar ubuntu, chroot to it, change some configuration files, install some new or updated software.

---

### Post by ivanlo2 on 2007-07-28
AH! Exactly the place I was looking for.  I wiped everything clean from my1420N  hard drive and have been unable to reinstall it.  I'm a complete newb so I will try to follow your instructions as best as I can.  Will the next release of Ubuntu have these Dell drivers?  When I try to install via the Live CD get a can't access tty0, job control turned off error.  Same if I try to install pcbsd.  When I try the alternative CD X server is broken.  I imagine there are plenty of other users in the same situation.

---

### Post by ivanlo2 on 2007-07-28
Wait, so would the file posted a few threads above this one simplify the solution I'm looking for?  How would I use that file to fix the Ubuntu install? Thanks.

---

### Post by specker on 2007-07-28
Only if you know what your doing.  I'd stick to the how to if your new.

---

### Post by ivanlo2 on 2007-07-28
Ok. Downloading PCLINUXOS now.  

I have a few questions before I begin. 

1. What kind of partition should I create?  Can I do it from inside PCLINUXOS? I have a gparted CD right here next to me if not.  Also what file type should I create the partition?

2. When I'm supposed to install from the Ubuntu alternate CD where and how should I create a mountpoint?

Thanks.

As an aside, when I create a swap partition how big do you think I should make it?  I have 2gigs of Ram?

---

### Post by specker on 2007-07-28
Yes, there is a partition manager application in there.  I think it is hidden in the system preferences/settings.  I had to hunt around for it but eventually found it.  I think it is under the hardware tab as create, resize and manage partitions.  I made the partition an ext3 type at the end of my hard drive.  Wireless internet works right off the bat in PCLinuxOS so just download those packages and save them to that new partition.  
During the alternate install it will ask you about partitioning.  DO NOT INSTALL UBUNTU TO THE NEW PARTITION THAT YOU COPIED THOSE PACKAGES TO.  You'll overwrite them and then be back at square one.  Choose the manual partitioning option and then select a mount point for your new partition (the one with the download files on it).  Then with the rest of the space on your drive select "partition space automatically."  Let me know how it goes.  Good luck.

---

### Post by ivanlo2 on 2007-07-30
Sorry double post

---

### Post by ivanlo2 on 2007-07-30
Sorry I'm stuck on the partition table.  I know I have to create a new partition without deleting the Packages partition but what do you mean mount point?  What do I do to the new partition to "mount" the Packages partition?  Thanks.

Oh btw.  There is a wiki link on the linux.dell.com site that if you click on laptops and then the 1720n model it has a link to a list of the packages added to the Dell Ubuntu factory image. 

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages)

Thought you might like to see that for future reference.

---

### Post by jmnormand on 2007-07-30
when you install ubuntu form the alt cd, choose manual partitioning.  here you can choose mount points for all your existing partitions and set up ubuntu partitions.  basically you want to set up / (root) a swap or two and /home if you want it to be separate from the root.  then choose a name of the partition with the package files, or you can simply set this up as /home just make sure it is set to not format.  your root and swap partitions should be formated before installing.  then when you login to the command line all your package files with be in /home or what ever you called your partition.  alternately if you are dual booting you can us a fat 32 (dont think ntfs works out of the box) partition and do all the downloading and such in windows.  then just do the manual partitioning as before.

---

### Post by bichenoubi on 2007-07-31
I just came accross this thread and wondering what is the whole point to sweep everything just to reinstall it all right away. Because, well, you were talking about a pre-installed Ubuntu Dell, not one with Windows.
I don't own that laptop, so maybe I'm missing something.

---

### Post by specker on 2007-07-31
Cleaning out your hard drive is NOT a good idea right now because of the many issues that exist getting Feisty back installed.  However, the only way to fix these various install issues is to identify them and understand them.  I would wager a guess that most people using Ubuntu Installed it themselves on a fresh partition.  Not a preinstall.  In a perfect world you should be able to boot the live cd and install without any major problems.  Unfortunately we are not at that point with the 1420n and Feisty.  Fresh installs aren't for everyone but somebody has got to do it.

---

### Post by tube013 on 2007-08-01
Can anyone post the dell debs (like the dkms and tg3-dkms_3.72.1_all.deb) that I presume are on the dell restore position..

For us gung-ho formaters!

thanks!

---

### Post by ssmohan on 2007-08-01
Greetings,

 Is there a how-to for using dkms to get the tg3 driver installed on an inspiron 1420 ?  I am trying to get the Broadcom 5906M ethernet card working.   The following two links suggest that the package tg3-dkms_3.72.1_all.deb should work, but I cannot find it:


[url]http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/tg3_driver_does_not_recognize_network_controller
[url]http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages

  I am doing a triple boot (Vista/Centos4.5/Ubuntu7.04) on a Dell Insprion 1420 with T7500/2GB/160GB/DVDRW/webcam/bluetooth.  Since neither the Broadcom 5906M ethernet card nor the Broadcom 1390 wireless card worked 'out of the box' using an Ubuntu 7.04 alternate install, I used a Fast Ethernet USB 2.0 Adapter (Airlink ASOHOUSB $15) to connect to the intenet  for package upgrades (to get the video working).

So far I have done the following:

- use gparted to partition the 160GB 7200 rpm drive
- install vista on /dev/sda1
- install centos 4.5 on /dev/sda2 (vesa video is only 1024x768, ethernet does not function nor does wireless)
- install 7.04 on /dev/sda3 using the alternate install disc (X crashes, ethernet does not function nor does wireless).
- extended partition on /dev/sda4 with ext3 /linuxShare at /dev/sda5, swap at /dev/sda6, ext3 /linuxBackup at /dev/sda7, and a vfat /sharedDrive at /dev/sda8.

- reboot to 7.04 with the Fast Ethernet USB 2.0 Adapter connected (shows up as eth2) and did the following from the command line

- sudo apt-get update
- sudo apt-get upgrade
- upgraded linux image  to2.6.20.16 (from 2.6.20.15) 

- replaced xorg-xserver-video-i810 with xorg-xserver-video-intel to get the graphics working (works nicely at 1440x900).

- after rebooting to 7.04, the laptop is finally usable.  I am now trying to get the ethernet working via dkms/tg3 but I cannot find the right how-to for that.

Thank you for your help,
Mohan

---

### Post by sciurus on 2007-08-01
Here are the packages Dell provides on the 1420N's recovery partition.

[ct356](http://www.megaupload.com/?d=F8HNT98A)
[dt092](http://www.megaupload.com/?d=03PGEZCL)
[ju048](http://www.megaupload.com/?d=U4LU8WOK)
[main](http://www.megaupload.com/?d=1IK44Z26)
[dkms-dep](http://www.megaupload.com/?d=S2PZPTO6)

---

### Post by tube013 on 2007-08-01
Thanks!  final piece of the puzzle is the tg3 dkms file.

Now just have to get to a wired network to test it.

---

### Post by ivanlo2 on 2007-08-03
I'm kind of stuck.  I set the partition with the packages with the /home mount point so then I restart Ubuntu.  Now when I try to install the packages via the command lines I get install errors.

dpkg: error processing linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb (--install):  cannot access archive: No such file or directory
Error where encountered while processing:
linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb

---

### Post by ivanlo2 on 2007-08-03
I will load PClinuxOs again to make sure my partition is still there and that the partition is still set to /home and that the packages are still there.

---

### Post by ivanlo2 on 2007-08-03
Well checked on PCLINUXOS the packages are on media/sda2

so if anyone can help me out on what I should try next I would greatly appreciate it.  Thanks in advance.

---

### Post by tube013 on 2007-08-03
> **ivanlo2 said:**
> Well checked on PCLINUXOS the packages are on media/sda2

so if anyone can help me out on what I should try next I would greatly appreciate it.  Thanks in advance.

I'm not sure what your partition table looks like at this point.. but you can boot into ubuntu.. and check where things are mounted by just running the mount command.

If /dev/sda2 isn't mounted anywhere...

cd /tmp
mkdir disk
sudo mount /dev/sda2 disk
cd disk

and you should have access to the packages.

---

### Post by everettattebury on 2007-08-03
I'm supposed to be getting my 1420n on August 20, and I plan to do some experimenting with it as well, trying out different distros, maybe making an encrypted partition with truecrypt, etc.

I'm thinking it would be best to install Mondo Rescue and back the whole thing up to dvd before I start though.

---

### Post by jmnormand on 2007-08-04
just a note i had problems getting the xserver-xorg-video-intel package installed with fiesty even after removing the i810 package and an update/upgrade.  was getting compatability issues with libc6.  however with the wireless connected i could run an

apt-get install xserver-xorg-video-intel 

its working fine, though no 3d.  < with the latest update 3d now seems to work...

---

### Post by sayhar on 2007-08-05
I followed all the directions, and it still doesn't work. Trying to dpkg xserver-xorg-vvideo-intel_2.1.0-1ubuntu1_i386

is what brought up errors for me.

---

### Post by ivanlo2 on 2007-08-05
I can't install the packages either.  I'm crossing my fingers for Gutsy Gibbon.

---

### Post by tube013 on 2007-08-05
there is a version linked to in another thread.. I don't have a link handy but it's about desktop effects on Intel 3100 graphics..  It was back ported and has the right depends, and installed okay for me.

after a little searching... here it is:
[http://ubuntuforums.org/showthread.php?t=494943&highlight=graphics+intel+effects](http://ubuntuforums.org/showthread.php?t=494943&highlight=graphics+intel+effects)

---

### Post by obliquetoid on 2007-08-06
Hi,

This is a bit off-topic, what kind of temperatures the 1420n has running on a Dell install of Ubuntu? Output of `acpi -V` would be appreciated. 

Thanks in advance.

---

### Post by mpgarate on 2007-08-06
it sounds like alot of trouble for a ubuntu supported system. I bought a dell open-source desktop for freedos, and just installed ubuntu on that. everything works on a fresh install, except my screen resolution is not detected.

---

### Post by ticklecricket on 2007-08-07
> **obliquetoid said:**
> Hi,

This is a bit off-topic, what kind of temperatures the 1420n has running on a Dell install of Ubuntu? Output of `acpi -V` would be appreciated. 

Thanks in advance.

Thermal 1: ok, 33.0 degrees C


Yeah, I'm really upset that I can't do a fresh install. I bought a new laptop with a *64 bit* processor and I'm stuck with a *32 bit* OS.

---

### Post by WAB on 2007-08-07
here there is a mirror to these files (all in one rar file)

[http://rapidshare.com/files/47509532/Addons_ubuntu_dell.rar](http://rapidshare.com/files/47509532/Addons_ubuntu_dell.rar)

---

### Post by WAB on 2007-08-07
[QUOTE=sciurus;3117500]Here are the packages Dell provides on the 1420N's recovery partition.

[http://rapidshare.com/files/47509532/Addons_ubuntu_dell.rar](http://rapidshare.com/files/47509532/Addons_ubuntu_dell.rar)

---

### Post by ssmohan on 2007-08-07
> **obliquetoid said:**
> Hi,

This is a bit off-topic, what kind of temperatures the 1420n has running on a Dell install of Ubuntu? Output of `acpi -V` would be appreciated. 

Thanks in advance.

Greetings,  
  On an inspiron 1420 with T7500/2GB (667Mhz)/160GB(7200 rpm)/intel 965GM X3100 / DVD+/-RW/ 1390 wireless / 1440x900 glossy:

64.0 degrees C when running intensive simulations
37.0 degrees C wihen browsing the web

Cheers,
Mohan

---

### Post by aeo24 on 2007-08-08
Great guide lots of help the only thing i can get working is my Ethernet card but thats fine i never use it anyways(yet!).

---

### Post by xspeed9190 on 2007-08-08
Ok so i have a 1520 with an Nvidia 8600gt.
I made the separate partition in windows and i installed ubuntu i tried all the instructions however i think that it can not find where they are.  I made a 100mb partition and the only things on it are the files that were stated to download.  when i type in the sudo dpkg -i XXXXXXX it just says can not find file.  Im really new to linux so i dont know how to find a directory or even see where it is looking can somone explain it for people who have no idea. I mean i got to the comand line i was playing with apt-get a little bit but still

Thanks in advance
Nick

---

### Post by daveyiv on 2007-08-09
has anyone actually been able to get the ethernet to work? I haven't had any luck, I installed dkms and that new tg3 deb file that came from the dell recovery partiton. Anyone?

---

### Post by ivanlo2 on 2007-08-09
I tried installing 7.10 from Tribe 4 live CD and it was a no go.  What are the chances the 7.10 final will have integrated these drivers?

---

### Post by specker on 2007-08-09
> **ivanlo2 said:**
> I tried installing 7.10 from Tribe 4 live CD and it was a no go.  What are the chances the 7.10 final will have integrated these drivers?

What problems did you have on the install?  I was thinking of trying it, but I don't want to waste my time if it is a lost cause.  Did you try the alternate cd?

---

### Post by weird_c00kie on 2007-08-09
Just wanted to say a big "THANK YOU!" for this thread. After the initial disappointment of not being able to install and run Ubuntu on my 1420 straight away, this guide was my salvation.

Infinite thanks to specker and everyone else who contributed :D

---

### Post by carminez on 2007-08-09
> **xspeed9190 said:**
> Ok so i have a 1520 with an Nvidia 8600gt.
I made the separate partition in windows and i installed ubuntu i tried all the instructions however i think that it can not find where they are.  I made a 100mb partition and the only things on it are the files that were stated to download.  when i type in the sudo dpkg -i XXXXXXX it just says can not find file.  Im really new to linux so i dont know how to find a directory or even see where it is looking can somone explain it for people who have no idea. I mean i got to the comand line i was playing with apt-get a little bit but still

Thanks in advance
Nick

Use this thread for info on the 1520...

[http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

---

### Post by ivanlo2 on 2007-08-10
> **specker said:**
> What problems did you have on the install?  I was thinking of trying it, but I don't want to waste my time if it is a lost cause.  Did you try the alternate cd?

Same errors as before.  Can't access tty.  I'm downloading the alternate CD now.   Will try that tomorrow sometime.

---

### Post by ubermenschx on 2007-08-10
[CENTER][SIZE="3"][SIZE="3"][FONT="Book Antiqua"]This all sounds great but couldnt someone just make an ISO Image of their drive and post it for anyone with a 1420 or 1420n?[/FONT][/SIZE][/SIZE][/CENTER]

---

### Post by rickyjones on 2007-08-10
@ubermenschx: Please don't post in such large letters - it is usually regarded as rude.

-Richard

---

### Post by ubermenschx on 2007-08-10
my bad. It just seems like a simple solution.

---

### Post by rickyjones on 2007-08-10
> **ubermenschx said:**
> my bad. It just seems like a simple solution.

I agree that having a kind samaritan with a fully working system make an image of it would be a nice solution. :). I wonder if there is a utility in linux similar to sysprep in Windows that will strip out sensitive machine specific information so that on the next boot you can give it a new name, users, etc... Hmmm.

-Richard

---

### Post by sciurus on 2007-08-10
> **ubermenschx said:**
> This all sounds great but couldnt someone just make an ISO Image of their drive and post it for anyone with a 1420 or 1420n?

If you have one of these dells, you already have such an image. Why is there a need to distribute it online?

---

### Post by ivanlo2 on 2007-08-10
For those people who accidentally or purposefully wipe their drives like me.  Also when upgrading HDD, etc.  

The Ubuntu disk included with the laptop is 7.04 without the Dell drivers.

It would indeed be awesome for someone to post an image with the drivers on it.

---

### Post by ubermenschx on 2007-08-11
for the peeps with the Vista version 1420. This machine wont install very easily. An image would make this process a no brainer.

---

### Post by specker on 2007-08-11
I finally found an extremely easy way to get your wired connection working.  Download [this guys script]("http://ubuntuforums.org/showthread.php?t=511974&highlight=upgrade+feisty+to+gutsy+kernel") and run it.  It will give you the Gutsy development kernel.  Your wired connection will work out of the box now.  Thanks to walkerk.  Excellent.

---

### Post by jmnormand on 2007-08-11
have a g4l image of a default root with everything working, but the partitioning would be an issue.  not sure how flexible a restored image would be, specially since root, /boot and /home are different partitions on my drive.

---

### Post by everettattebury on 2007-08-12
> **ubermenschx said:**
> [FONT="Book Antiqua"]This all sounds great but couldnt someone just make an ISO Image of their drive and post it for anyone with a 1420 or 1420n?[/FONT]

My 1420N is supposed to arrive in the next 3 to 5 days.  I will make a Mondo Rescue archive of it, convert it to iso's, and post a link as soon as I am able. 

There is a page at [http://www.linuxjournal.com/article/6808](http://www.linuxjournal.com/article/6808) that explains how to use Mondo Rescue to clone systems.

---

### Post by LeonI on 2007-08-13
After a couple of days trying to install Feisty on my new Vista loaded Inspiron 1420 I managed to come up with a simple method to do it using only the Live CD.

1) Boot from the Live CD and press F6 to add extra options to the booting sequence. (You might want to boot in safe graphics mode depending on your graphics card).

2) Add "break=top" at the end of the options line and press enter.

3) You'll get the BusyBox console with an error: "/bin/sh: can't access tty; job control turned off" . Type in the following: 
```
modprobe piix
exit
```

4) The Live CD will now boot you to Ubuntu :D You can install from here regularly.

5) When you reboot you'll be prompted with the BusyBox console once again with the same error. So just do the same again:
```
modprobe piix
exit
```

6) Edit the file /boot/grub/menu.lst to remove wherever it says "break=top"

And that should do it :D:D You should now be able to boot normally.

---

### Post by RancidLM on 2007-08-13
My wireless worked on the fresh ubuntu install using the restricted Intel drivers.. but my wired internet doesn't work...  plz help :)
(my laptop is the 1420 model)

---

### Post by specker on 2007-08-13
> **RancidLM said:**
> My wireless worked on the fresh ubuntu install using the restricted Intel drivers.. but my wired internet doesn't work...  plz help :)
(my laptop is the 1420 model)
Look 4 posts up. ^

---

### Post by jmnormand on 2007-08-13
to make everything easier on myself, and some of you i hope, ive put together this tar.gz: (only for the intel graphics 1420n may work for other models with intel as well)

[http://www.lentecs.com/files/1420-install.tar.gz](http://www.lentecs.com/files/1420-install.tar.gz)

after running through the alt install cd you should be able to get to the command line and cd to the /1420-install directory and run ./1420-install.sh (this must be run from inside the 1420-install dir)

choose all default options and the system will reboot.  after reboot go back to the 1420-install directory and run ./1420-install2.sh and again choose default options.

when the graphics driver menu appears choose intel.  If your system hangs after a min or so do a hard restart (this is quite common unfortunately), if not simply choose 1280x800.

if you have to restart simply run:

sudo dpkg-reconfigure -phigh xserver-xorg

and again choose intel and 1280x800 then restart

also if 1420-install2.sh gives errors when runing update then you need to do some more work to configure your wireless network and rerun it.  ill be working on adding the wired network fix to this once i get that figured out, everything else should be working.

one last note if you cant figure out how to get the tar.gz unziped and on your system, simply use the pclinuxos live cd and either a usb drive or a sd card.  this is the easiest if you dont know your way around the command-line.

---

### Post by ivanlo2 on 2007-08-14
> **everettattebury said:**
> My 1420N is supposed to arrive in the next 3 to 5 days.  I will make a Mondo Rescue archive of it, convert it to iso's, and post a link as soon as I am able. 

There is a page at [http://www.linuxjournal.com/article/6808](http://www.linuxjournal.com/article/6808) that explains how to use Mondo Rescue to clone systems.

Eagerly waiting.

---

### Post by double051 on 2007-08-14
So let's say I have a 1420 with an nVidia 8400M instead of the Intel X3100... am I SOL?

---

### Post by jmnormand on 2007-08-14
you can get it working but hell if i know how...  also not sure if it has full support for 3d and the likes.

---

### Post by ivanlo2 on 2007-08-14
nvidia support is good on linux if not always on the edge.  I'm sure these will be in Gutsy.

---

### Post by LeonI on 2007-08-14
> **double051 said:**
> So let's say I have a 1420 with an nVidia 8400M instead of the Intel X3100... am I SOL?

I have the nVidia Go 8400 in my Inspiron and it's working allright. Even with Beryl. :D

I'm using the upgraded kernel though, so i had to install the nVidia driver (using Envy) with the Gutsy repos enabled.

---

### Post by hippomofatumas on 2007-08-17
ok well going back to the beginning of this post, i managed to get as far as installing the new xserver intel stuff but it didnt work. then i tried apt-get installing the  packages someone said were needed. but that didnt work. so i am now attempting Leon's tar.gz method of an all-in-one solution. lets hope it works.

its interesting that the computer that can come with ubuntu (i got the windows version, it was cheaper and i wanted webcam) is really hard to get ubuntu on yourself lol.

---

### Post by hippomofatumas on 2007-08-17
ok i really need some help. it gets confusing for me looking at all these posts replying and fixing various things.

i need step by step instructions to get ubuntu installed w/ video and wired internet working. i dont even have a wireless router right now, so i can fiddle with that later. webcam not important right now. touchpad is lol.

i hope i dont sound ignorant ive gone over and over this thread and so many others, done everything to the letter, and nothing has fully worked. i got pretty far with the initial instructions here.

im glad i tried the alternate cd cause i had been trying to get opensuse to work. eek. new territory for me. it installed but inernet and video were a no-go. and their forums are nothing compared to this

: )

go ubuntu!

ps- please help me and all those reading by laying out a nice big step by step to get it all working. : )

---

### Post by derhanfi on 2007-08-18
so i can't use the "sudo -f install" because no drive is available. what can i do? next to it, i can't install the intel driver.
won't work.=(

---

### Post by derhanfi on 2007-08-18
oh =(
in the xorg.conf file i choose intel, then 1280*800. Then my screen switches between dark black and brighter black, during the wifi led is blinking; the screen turns black and thats it.
what could i do? (i followed all the steps of the indroducing comment in this thread).

thanks for help

---

### Post by kinobe on 2007-08-18
First off, thanks for the guide. Really helpful. 

I have a 1420 and a GeForce 8400M GS, so I tried following the guide up to the intel drivers point. I'm trying to install the nvidia drivers found here [http://www.nvidia.com/object/linux_display_ia32_100.14.09.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.09.html"), but I get the error "No precompiled kernel interface was found to match your kernel." 

It offers to download it via FTP, but since my Fa port isn't working yet, that option is a no go. The installer then tries to build it, but the next error I get is "You do not appear to have libc header files installed on your system. Please install your distribution's libc development package". 

And that's where I'm stuck, but I'll try to surf around for a solution, namely how to install the libc dev package.

If you guys have any opinions, I'd greatly appreciate it. Thanks.

---

### Post by specker on 2007-08-19
The xserver-xorg-video download location changed so I updated the link.  Anyone having issues with that package try the new link.
Also, for the brave Gutsy will install.  Some of the Feisty issues are solved.  However, some new ones exist.

---

### Post by RancidLM on 2007-08-21
> **double051 said:**
> So let's say I have a 1420 with an nVidia 8400M instead of the Intel X3100... am I SOL?

you need to use Envy to install the 8400m drivers.. i am using the save vid card on my 1420
 you can get this app that will auto install the latest nvidia drivers from 
[URL="http://albertomilone.com/nvidia_scripts1.html"]
http://albertomilone.com/nvidia_scripts1.html[/URL]

---

### Post by RancidLM on 2007-08-21
Has any one figured out how to get the integrated webcam working in linux? it would be nice to get  a /dev/video

thnx!

---

### Post by bz0b on 2007-08-21
Hey when i try and load the ubuntu installer cd i get an error it gets stuck at the busybox screen. what is that?

---

### Post by specker on 2007-08-21
> **bz0b said:**
> Hey when i try and load the ubuntu installer cd i get an error it gets stuck at the busybox screen. what is that?
You want to use the alternate install cd rather than the live cd.  It is one way to fix that problem.

---

### Post by hippomofatumas on 2007-08-21
i managed to get the alternate install cd to install, and got all of the packages specker said to install installed except the intel xserver package. so i got the 915resolution and the new i810 package installed and x worked, but only in 1024x768, not 1280x800. however i still dont have working wireless or wired internet. 

is there an easy way to get stuff working?

---

### Post by MrSootentai on 2007-08-22
I got everything working properly except my wireless. Can anybody help me out here?
Maybe just an alternative to this install method.

---

### Post by bz0b on 2007-08-22
So when you were reffering to gutsy being pretty stable, which install were you reffering to desktop or alternate?

---

### Post by SoftCompTools on 2007-08-22
I got perfectly working my Dell Ubuntu, tomcat, sql server 2000.

Found some [good ubuntu articles]("http://www.softcomptools.com/blog")

---

### Post by ssmohan on 2007-08-23
> **hippomofatumas said:**
> i managed to get the alternate install cd to install, and got all of the packages specker said to install installed except the intel xserver package. so i got the 915resolution and the new i810 package installed and x worked, but only in 1024x768, not 1280x800. however i still dont have working wireless or wired internet. 

is there an easy way to get stuff working?

Greetings,

For wireless:
  If you have the broadcom 1390 wireless card (like I do), then follow the instructions in :
[http://sudan.ubuntuforums.com/showthread.php?t=297092]("http://sudan.ubuntuforums.com/showthread.php?t=297092")

After completing step 5, reboot and install wifi-radar
sudo apt-get install wifi-radar
Then use wifi-radar to scan and connec to wireless networks.

For wired:
 Use the files kindly provided by WAB (post#64 in this thread) via this link:
[http://rapidshare.com/files/47509532...buntu_dell.rar]("http://rapidshare.com/files/47509532...buntu_dell.rar")
Only version 3.72 of the tg3 driver (the one provided via the above link) seems to work for the Broadcom 5906 ethernet device.  I originally tried to download the version on Broadcom's website (version 3.71b), but that did now work.

All the best,
Mohan

---

### Post by ssmohan on 2007-08-23
> **MrSootentai said:**
> I got everything working properly except my wireless. Can anybody help me out here?
Maybe just an alternative to this install method.

Greetings,

For wireless:
If you have the broadcom 1390 wireless card (like I do), then follow the instructions in :
[http://ubuntuforums.org/showthread.php?t=297092&page=3]("http://ubuntuforums.org/showthread.php?t=297092&page=3")
After completing step 5, reboot and install wifi-radar
sudo apt-get install wifi-radar
Then use wifi-radar to scan and connec to wireless networks.

The thread above worked for me on the inspiron 1420.  I used ndiswrapper version 1.46 with the 2.6.20-16-generic kernel, and utils version 1.9.

All the best,
Mohan

---

### Post by MikeRussell on 2007-08-23
> **ssmohan said:**
> Greetings,

For wireless:
If you have the broadcom 1390 wireless card (like I do), then follow the instructions in :
[http://ubuntuforums.org/showthread.php?t=297092&page=3]("http://ubuntuforums.org/showthread.php?t=297092&page=3")
After completing step 5, reboot and install wifi-radar
sudo apt-get install wifi-radar
Then use wifi-radar to scan and connec to wireless networks.

The thread above worked for me on the inspiron 1420.  I used ndiswrapper version 1.46 with the 2.6.20-16-generic kernel, and utils version 1.9.

All the best,
Mohan
Yeah...
   The problem is that when using the 1390 wireless card, it is not recognized (even in PCLinuxOS).  Therefore, using the instructions in 

[http://ubuntuforums.org/showthread.php?t=297092&page=3](http://ubuntuforums.org/showthread.php?t=297092&page=3)

are useless, as you need to be connected in order to install build-essential, etc.  Because wired connections don't work either, there is no way to connect to the internet to apt-get and such - kind of a catch 22.  If anyone has a way around this, please post.  Thanks!
Mike

---

### Post by ssmohan on 2007-08-23
> **MikeRussell said:**
> Yeah...
   The problem is that when using the 1390 wireless card, it is not recognized (even in PCLinuxOS).  Therefore, using the instructions in 

[http://ubuntuforums.org/showthread.php?t=297092&page=3](http://ubuntuforums.org/showthread.php?t=297092&page=3)

are useless, as you need to be connected in order to install build-essential, etc.  Because wired connections don't work either, there is no way to connect to the internet to apt-get and such - kind of a catch 22.  If anyone has a way around this, please post.  Thanks!
Mike

I understand the frustration.  My first 7.04 install on the inspiron 1420 went the same way.  I kept trying to to download all the needed deb packages on another computer and then moving them over to the 1420 using a USB stick, but that became inconvenient.

On my second install, I inserted a 10/100 USB adapter in one of the usb ports, and then started the alternate CD install and got things running quickly as I was able to use apt-get to install all the required packages (via the USB ethernet adapter).  

I used a Trendnet TU-ETC100C ($10).  Since this is a USB 1.1 device (not USB 2.0), this worked "out of the box" even when I installed Dapper 6.06 on another partition of the inspiron 1420 using the alternate CD installation.  Another one that worked on 7.04 (but not 6.06) was an Airlink USB 2.0 10/100 ethernet adapter (which goes on sale at Fry's for $3 regularly).

Please note that I had to resort to the above workarounds as at that time, the kind 1420N owners  had not posted the packages and  automated scripts that came with the 1420N.    Looks like this thread now has many posts with all the packages and the relevant scripts so there should be no need to use apt-get via the network to get things running.

All the best,
Mohan

---

### Post by MrSootentai on 2007-08-23
I am reinstalling my Ubuntu and I have no idea why everytime I try to log in it gives me an 'Incorrect Password' message.
I know the correct username and I know the correct password.
Anybody know what's up?

---

### Post by bz0b on 2007-08-26
Just boot into recovory mode and reset the password

---

### Post by MikeRussell on 2007-08-26
Does anyone have suspend/resume working properly with the Nvidia drivers installed?  I've tried a variety of acpi settings, but X never seems to resume...   If so, please help with some suggestions.  Thanks!

Mike

---

### Post by rustalot on 2007-08-30
I have a 1420, but because Dell doesn't sell Ubuntu where I live (Canada) I got the Vista version. I tried to make sure things would be compatible (e.g. I selected the Intel wireless, which automagically worked out of the box :) ), and following your instructions, everything works, except for the sound. My soundcard is listed in the Windows Device Manager as "SigmaTel High Definition Audio CODEC". Is there a way to make it work?

Also, after installing the Gutsy kernel, it won't let me install any of the compilers. :(

Very helpful thread though.

---

### Post by notwen on 2007-08-30
> **copper23 said:**
> Hey, I just would like to add a comment to inform the general pubic of a great site I found for all e-book, wholesaler & Distributor listings, and web development services I've seen. Its [http://www.thebusinesskey.com]("http://www.thebusinesskey.com") I actually just signed up as of recently and joined their advertising program where they pay you to advertise for them.  Basically you provide proof of the advertising you've done and they send you a check.  They have awesome skills in web development, check them out for yourself.  Once again its [http://www.thebusinesskey.com]("http://www.thebusinesskey.com")

Thankyou,
      Copper23

Was this thread just hijacked w/ a spam troll?  Ive seen the new thread spam, but hijacking threads now?  Have you no morals?!?!?!

---

### Post by specker on 2007-08-30
> **rustalot said:**
> I have a 1420, but because Dell doesn't sell Ubuntu where I live (Canada) I got the Vista version. I tried to make sure things would be compatible (e.g. I selected the Intel wireless, which automagically worked out of the box :) ), and following your instructions, everything works, except for the sound. My soundcard is listed in the Windows Device Manager as "SigmaTel High Definition Audio CODEC". Is there a way to make it work?

Also, after installing the Gutsy kernel, it won't let me install any of the compilers. :(

Very helpful thread though.

You might want to try running Gutsy.  I know it isn't a good idea to solely use a development release, but I have found it to be quite stable even when compared to Feisty after all the tweaking.  Most everything works well right out of the box.  Sound has been an issue but there is an easy fix for that (it might have been fixed in a recent update even).

---

### Post by rustalot on 2007-08-30
I upgraded to Gutsy, but the sound still doesn't work. The thing is, though, when I upgraded, I still had those files for the fix for the Intel sound, so I removed them, but that didn't help. Is there a way to re-run the hardware detection / configuration script for the audio? I think it might have thought it was the Intel sound and so loaded the wrong driver for it.

---

### Post by specker on 2007-08-31
> **rustalot said:**
> I upgraded to Gutsy, but the sound still doesn't work. The thing is, though, when I upgraded, I still had those files for the fix for the Intel sound, so I removed them, but that didn't help. Is there a way to re-run the hardware detection / configuration script for the audio? I think it might have thought it was the Intel sound and so loaded the wrong driver for it.

Yes, I had the same issue. Those old fixes mess it all up.  You have to do a clean install.   I just did a fresh reinstall today and the sound issue has been fixed.  Install Tribe 5 and do ALL the updates.  The latest update of linux-ubuntu-modules seemed to fix sound.  Everything works basically flawlessly, as far as I can tell.  No need for any more serious tweaking!

---

### Post by hippomofatumas on 2007-09-01
i just booted up the alternate install cd of gutsy tribe 5, and its working great. during the install process, when it said configuring xserver, the screen went all funny colors, but i just waited till it ejected the cd and rebooted and all was well. everything is working pretty well. after setting my static ip for wired internet and doing all of the updates, my system was running almost completely. wired and wireless, touchpad with scrolling function, 1280x800 resolution, compiz or whatever is working fine, sound, the works. only things ive found is that the status symbol of your wifi signal strength stays at zero even though if you click on it the bar is at 100%, and im currently using generic vesa drivers. do i need to change to intel drivers? i figure i might as well, so how do i go about this?

oh yeah i cant get the webcam to work either, can anyone help with that?

--im so glad i got ubuntu working, sabayon was a nightmare, and up until tribe 5 i had had no luck, but im home again! go ubuntu!

---

### Post by kybishop on 2007-09-01
which gutsy cd should be used, 32 bit or 64 bit?

also should I use the alternative gutsy install cd, or will it work with the normal cd

---

### Post by specker on 2007-09-01
It currently works with both live and alternate cd's.  At the boot screen you should enter vga=771 into the boot options it solves the funky screen issue.

---

### Post by blackhowling on 2007-09-02
got an out of the box ubuntu dell and want to dual boot with xp anyone got some advice on how to do that?

---

### Post by hippomofatumas on 2007-09-02
i was incorrect in my last post. my wireless doesnt work at all. it detects networks but cant connect. im in the process of trying to make the iwlwifi driver work. poo. its not going well.

heres the howto im trying: [http://ubuntuforums.org/showthread.php?p=3298674&posted=1#post3298674](http://ubuntuforums.org/showthread.php?p=3298674&posted=1#post3298674)

---

### Post by rustalot on 2007-09-05
Sooo... I tried a fresh install of Gutsy T5. It had a few... quirks. The first (kinda dissapointing) thing is that the sound still doesn't work, which was the reason I was doing this. During the process of installing, I lost all my music (oh noes!), which is annoying b/c I didn't get any benefit from reinstalling. The installer went funky ( I didn't know about the 'vga=771' or whatever) and so my GRUB was messed up and didn't recognize the Vista (but I added an entry myself with the help of my friend who's 'good with computers'). I get an errormsg every time I login saying 'kbluetooth could not start' or something similar, even though I have no bluetooth. I tried Compiz, but it's really messed up.

Other than that things are going well.
PS: I haven't actually tried the wireless yet, as I don't have a wifi network, but it seems to work. It's the Intel 3945.

---

### Post by frogotronic on 2007-09-06
> **specker said:**
> Yes.  Suspend and Hibernate seem to work just fine.


Are you using the OpenGL drivers for the Intel card?  In other words, are you getting proper 3D accerlation from the hardware.  The reason I ask is because nVIDIA cards have problems with Hibernate & Suspend when using the nVIDA drivers, but not the "nv" drivers.

Can you run try typing (from the terminal):

>glxgears

And run it for a while and then post the FPS rate?

Thanks very much

---

### Post by specker on 2007-09-06
> **cement_head said:**
> Are you using the OpenGL drivers for the Intel card?  In other words, are you getting proper 3D accerlation from the hardware.  The reason I ask is because nVIDIA cards have problems with Hibernate & Suspend when using the nVIDA drivers, but not the "nv" drivers.

Can you run try typing (from the terminal):

>glxgears

And run it for a while and then post the FPS rate?

Thanks very much
Yep I'm getting 3D acceleration.  glxgears runs fine with 1074 fps.  In fact I have glxgears running inside the compiz desktop cube.

---

### Post by frogotronic on 2007-09-06
Great.  This has been a HUGE thorn in my side on my old Dell i8100 laptop.  The Hibernate won't work.  Good to know that this i1420N does work.

- CH

---

### Post by primarykey on 2007-09-07
> **LeonI said:**
> After a couple of days trying to install Feisty on my new Vista loaded Inspiron 1420 I managed to come up with a simple method to do it using only the Live CD.

1) Boot from the Live CD and press F6 to add extra options to the booting sequence. (You might want to boot in safe graphics mode depending on your graphics card).

2) Add "break=top" at the end of the options line and press enter.

3) You'll get the BusyBox console with an error: "/bin/sh: can't access tty; job control turned off" . Type in the following: 
```
modprobe piix
exit
```

4) The Live CD will now boot you to Ubuntu :D You can install from here regularly.

5) When you reboot you'll be prompted with the BusyBox console once again with the same error. So just do the same again:
```
modprobe piix
exit
```

6) Edit the file /boot/grub/menu.lst to remove wherever it says "break=top"

And that should do it :D:D You should now be able to boot normally.

Thanks LeonI. You found a very good and practical solution for feisty install. Thanks again for your help...

---

### Post by frogotronic on 2007-09-07
> **specker said:**
> Yep I'm getting 3D acceleration.  glxgears runs fine with 1074 fps.  In fact I have glxgears running inside the compiz desktop cube.

Thought of one more question:

Can you use twinview/dual head?  i.e. hook the laptop upto a projector and use it for presentations?

If so, does the intel video card have a control panel like the ATI control panel or the nVIDIA X server settings panel?

Thanks (again)

---

### Post by specker on 2007-09-07
> **cement_head said:**
> Thought of one more question:

Can you use twinview/dual head?  i.e. hook the laptop upto a projector and use it for presentations?

If so, does the intel video card have a control panel like the ATI control panel or the nVIDIA X server settings panel?

Thanks (again)
I don't know.  I haven't had the opportunity to try it.

---

### Post by atulgoyal52 on 2007-09-09
HI.. I'm new to Linux. I recently buy inspiron 1420. I understand the whole mechanism. But I would like to dual boot vista and ubuntu. Is it possible when installing through alternate ubuntu cd.

---

### Post by frogotronic on 2007-09-09
A friend of mine did this on an Acer.  I'll assume you have VISTA factory installed?

If so, just repartition the hard drive to free up some space from  the "DATA drive" part of VISTA.  Then install UBUNTU onto that new partition. VISTA has its own disk partitioner which should work really well for this.

Just make sure you write down the drive sizes so you make sure you install UBUNTU onto the desired partition.

- CH

---

### Post by LMP900 on 2007-09-11
Excellent news for Inspiron 1420 and 530 owners: [**Dell "Remastered" Ubuntu 7.04 ISOs Available for Download**]("http://direct2dell.com/one2one/archive/2007/09/10/29517.aspx")

This is a good move in Dell's part and will help those looking for a (presumably) trouble-free Ubuntu 7.04 fresh install.

---

### Post by Benanov on 2007-09-13
Ugh, Linuxant drivers!

Looks like other than that the drivers are really just updated versions, along with a lot of restricted modules.

What doesn't work without the restricted drivers?

---

### Post by notwen on 2007-09-13
> **Benanov said:**
> Ugh, Linuxant drivers!

Looks like other than that the drivers are really just updated versions, along with a lot of restricted modules.

What doesn't work without the restricted drivers?

Looks like it's generally either the Nvidia or Intel chipset, the 1420n also has conexant modem needing restricted drivers.  Link [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Desktops_and_Notebooks_with_Ubuntu_Desktop_Edition_7.04"), simply select the Dell model and it will show you it's restricted drivers.

---

### Post by atulgoyal52 on 2007-09-17
Hey Gud news.. I just installed ububtu 7.04 from the alternate cd for specifically this model..[http://direct2dell.com/one2one/archive/2007/09/10/29517.aspx](http://direct2dell.com/one2one/archive/2007/09/10/29517.aspx)  this is working fine on my system.
:guitar:

---

### Post by notwen on 2007-09-17
> **atulgoyal52 said:**
> Hey Gud news.. I just installed ububtu 7.04 from the alternate cd for specifically this model..[http://direct2dell.com/one2one/archive/2007/09/10/29517.aspx](http://direct2dell.com/one2one/archive/2007/09/10/29517.aspx)  this is working fine on my system.
:guitar:

Did you install it on  a 1420n or a 530n?  And did it resolve the track pad's scrolling ability as well?  I was curious if it resolved the additional bugs that have been fixed on launchpad alongside installing dell's additional packages.

---

### Post by uber_nerd11 on 2007-09-20
I tried to follow the beginning of the how to, but it appears that the links to the bottom four or so .debs are broken...

---

### Post by 7182818 on 2007-09-23
> **uber_nerd11 said:**
> I tried to follow the beginning of the how to, but it appears that the links to the bottom four or so .debs are broken...

Yea i had the same problem too... the files aren't on the server anymore but there are very similar ones (updated ones i think?) ill try and post the link below...

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.31_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.31_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16-generic_2.6.20-16.31_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16-generic_2.6.20-16.31_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16_2.6.20-16.31_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-16_2.6.20-16.31_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.1.1-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.1.1-0ubuntu3_i386.deb)

alright so those are the 4 ones I downloaded and I installed them as well as the first two... dunno if thats bad or not but hopefully it will do.. 

I got past the first six steps then removed the xserver i810 but now I can't figure out what to do... I'm getting the error that says the 
"dpkg: dependency problems prevent configuration of xserver-xorg-video-intel ... xserver-xorg-video-intel depends on libc6 (>= 2.6-1); however: version of libc6 on system is 2.5-0ubuntu14." followed by "xserver-xorg-video-intel depends on xserver-xorg-core (>=2:1.2.2.0-3ubuntu8."

So i tried downloading and installing the libc6_2.6-1+b1_i386.deb file but it says the error about how it conflicts with tzdata...

so i upated tzdata from version 2007e-5 to 2007b-1 and still no change so I tried to install libc6_2.6.1-5_i386.deb package and still same problem... so Im kinda stuck :(  if any one can offer me some guidance I would appreciate it (I am a serious newbie but I REALLY want to try ubuntu on my laptop!)  O and just fyi its actually kubuntu I was trying to install... don't know if that makes a difference... Thanks a bunch for your help and also for making this HOW-TO :)

---

### Post by Zeedok on 2007-09-26
Can anyone answer this question (I can't see it specifically answered anywhere):

Will the drivers etc from the Dell remastered disc be integrated into the official Ubuntu releases? Perhaps with a delay while the Dell guys catch up?

If I was to buy a Dell laptop tomorrow which would be the best strategy:
 1. Install from official Ubuntu disc and accept that some things may not 'just work' OR
 2. Install from the Dell remastered disc (making sure everything works) then update the system to the official releases?

Anyone?

---

### Post by atulgoyal52 on 2007-09-26
I installed ubuntu feisty on my inspiron 1420 from the specific alternate cd for this model mentioned above in posts..
It worked well..before i got stucked in a problem while tried to change desktop appearence..
Now after rebooting it hangs at the first screen. And nothing but mouse pointer can be moved.
PLZ help me to cure this..:(

---

### Post by Exile29 on 2007-09-26
Did you happen to enable Desktop Effects?
My 1420n did the same thing. 
Try rebooting a few times and try to turn off the Effects.

---

### Post by atulgoyal52 on 2007-09-26
yeah. exactly.. 
but i try a lot of times.. but everytime it hangs either to first screen or black screen..
Can u tell me approx how many times u tried..

---

### Post by Exile29 on 2007-09-26
> **atulgoyal52 said:**
> yeah. exactly.. 
but i try a lot of times.. but everytime it hangs either to first screen or black screen..
Can u tell me approx how many times u tried..

It had to be about three or four times. 
Another quick fix (just so you can get back to using your laptop) would be to login to a recovery session and at the prompt type in > SUDO ADDUSER user_ID_here Admin 
Then just login to the new user account.

---

### Post by atulgoyal52 on 2007-09-26
It is working in root mode..
but still not able to make that off..
Hey.. can it be possible to make it off from root mode??

---

### Post by Exile29 on 2007-09-26
> **atulgoyal52 said:**
> It is working in root mode..
but still not able to make that off..
Hey.. can it be possible to make it off from root mode??

I don't know where it is located, but there has to be a config file somewhere. As long as you're root, you can edit that file in any account.
The trick is, finding the right file and knowing what to remove. Unfortunately, I have no idea what it is. :confused:

If you find out, post it here please. I'd like to know as well.

---

### Post by Exile29 on 2007-09-26
Hey, looks like someone else figured it out. Check this thread... 
[http://ubuntuforums.org/showthread.php?t=532360&highlight=disable+desktop+effects](http://ubuntuforums.org/showthread.php?t=532360&highlight=disable+desktop+effects)

---

### Post by VTlinuxnoob on 2007-09-30
Edited to remove cross post.

---

