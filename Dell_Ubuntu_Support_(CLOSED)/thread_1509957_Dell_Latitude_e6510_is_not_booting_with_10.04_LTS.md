---
title: "Dell Latitude e6510 is not booting with 10.04 LTS"
date: 2010-06-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ramsrambo on 2010-06-14
My notebook config is core i7 720 with turbo boost, Intel 57 chipset 4gb ram and nvidia 3100 nvs onboard, multi touch, bluetooth, intel centrino 6200 wifi and 500gb HDD

I tried installing 64bit 10.04 LTS desktop on my notebook. But the machine is not even booting.

Any suggestions ?

---

### Post by ramsrambo on 2010-06-15
I tried booting thru MS virtual machine and I got an error messgage 
" The Kernel requires x86-64 cpu, but only detected i686 CPU
unable to boot - please use a kernel appropriate to your cpu"

Any help to resolve this ?

---

### Post by HardLuck on 2010-06-15
I had the same problem on a similar 64-bit E6510 configuration (core i5, 4gb ram, nvidia  NVS3100M, bluetooth, intel centrino 6200 wifi and 320gb HDD).

Basically I used the information here to get through the initial install from the CD.  [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Upon reboot it would, of course, go to blank screen even though the installation from the CD was complete.  I tried researching the issue and it may be a problem with some combination of kernel, video card, screen resolution and driver, although there were no clear answers.

I finally tried some of the suggestions here:  [https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)

It seems this machine does not like the open-source "noveau" driver for the Nvidia card, which is the one Ubuntu 10.04 installs initially by default.  I used the suggestions under the section titled "Disabling Noveau" when rebooting, specifically [I]During boot hold down the shift key to get to the grub menu.  Press the  'e' key to edit the boot command, and go down to the "kernel" line.  Add  "nouveau.modeset=0" to the end of the line containing "quiet splash",  then press Ctrl+x to boot.  Nouveau will be disabled for this boot.

[/I]The system came up in a lower-resolution mode.  I then used System>Administration>Update Manager to update the system and I used System>Administration>Hardware Drivers to change to the proprietary "nvidia" driver.  Everything seemed to work fine on reboot.

BTW, I fooled around with a couple of other distributions on this machine and it didn't seem to like them much either.  There is another open source driver, "nv" I think, and I couldn't get it to work either in the other distributions.

Cheers.

---

### Post by carltonh on 2010-06-24
The same problem exists on this laptop with 32 bit. Fortunately, the same workaround through Grub solves it.   ...So after installing and updating the Nvidia proprietary driver, I just have to get wireless working on it too.

---

### Post by ramsrambo on 2010-07-14
None of these work.

I tried the MS virtual PC and here is the msg I got

"This kernel requires an x86-64 CPU, but only detected an i686 CPU. 
Unable to boot - Please use a kernel appropriate for your CPU"

---

### Post by mörgæs on 2010-07-14
How does the 32 bit version work?

---

### Post by TrekON on 2010-07-21
> **mörgæs said:**
> How does the 32 bit version work?

I had the same problem on my 32-bit system (E6510 i5). The 9.04 booted fine. The wireless and ethernet cards are not recognized even in 9.04 though so some more effort is called for.

---

### Post by dbuell on 2010-07-25
If anybody is still looking for a more permanent solution than changing the grub boot line on each restart or attempting changes through grub I have found a seemingly solid solution for my e6510.

[https://wiki.edubuntu.org/X/Troubleshooting/Nouveau](https://wiki.edubuntu.org/X/Troubleshooting/Nouveau) Is where I found this.

```
echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u
```

Oh and thanks HardLuck, updating and installing the nvidia drivers didn't seem to make ubuntu boot properly for me but your post certainly got me working in a hurry.

---

### Post by ramsrambo on 2010-07-28
Well I tried everything under the sun in fact I tried to boot this machine with microsoft Virtual PC (virtualizaton SW) this is the error msg I got
------------
This kernel requires an x86-64 CPU, but only detected an i686 CPU. 
Unable to boot - Please use a kernel appropriate for your CPU

--------------

---

### Post by dbuell on 2010-07-29
> **ramsrambo said:**
> Well I tried everything under the sun in fact I tried to boot this machine with microsoft Virtual PC (virtualizaton SW) this is the error msg I got
------------
This kernel requires an x86-64 CPU, but only detected an i686 CPU. 
Unable to boot - Please use a kernel appropriate for your CPU

--------------
Booting it in a VPC can bring more variables into the mix. From what I have read, Microsoft Virtual PC only supports 32-bit guests.

---

### Post by ajmctaggart on 2010-08-18
I realize I may be a bit late but I'm running the latest kernel of 10.04, with ALL repositories enabled (backports, proposed, etc).

I definitely had issues initially, using the workaround of ```
nomodeset
``` in my grub configuration.

It's very important, though, to follow the order here:

1.  get into low graphics mode by adding nomodeset to grub.
2.  Once in, update to the latest and greatest kernel and perform all other updates FIRST.
3.  THEN add Nvidia driver from Restricted Drivers (ignore Broadcom for now, I know it's tempting)
4.  Reboot- again this time, you'll need to run nomodeset in grub.
5.  Open a Terminal and enter
```
sudo nvidia-xconfig
```
reboot again.
6.  you'll want to remove the splash screen and use a verbose booting...sometimes, there is still a place when booting that your machine will apparently stop...you can hit any key to continue booting.  This will however only be apparent by verbose boot...hence me removing the splash option in grub.

I know this sounds basic, but order did help me...good luck!

---

### Post by daz23 on 2010-08-18
The just released Ubuntu 10.04.1 LTS has the same issue with the Nouveau driver on a e6510 (core i7, 4gb ram, nvidia NVS3100M, and SSD) laptop.

The steps in this thread fixed it. Here's a summary:

Pre-Install:

1.Boot from the CD and hit any key to get to the menu screen.
2.At the install screen press "F6", "Esc", and delete "quiet" and "splash" from the command line. 
3.Add "nomodeset" at the end of the line.
4.Press "Ctrl" and "X" to boot.
5.Install Ubuntu

Post-Install:

1.During boot hold down the shift key to get to the grub menu.
2.Press the 'e' key to edit the boot command
3.Use arrow keys to move to end of line, and delete "quiet" and "splash" from the command line.
4.Add "nouveau.modeset=0" at the end of the line.
5.Press "Ctrl" and "X" to boot.
6.Go to System - Hardware Drivers and install the Nvidia proprietary drivers.
7.If you don't want to install the proprietary drivers, then you will need to disable Nouveau this way:
```

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u
```
8.Reboot

---

### Post by semmypurewal on 2010-08-24
**EDIT**: Editing the xorg.conf file as described below did not work for some people.  If you can get that far and it's not working for you, try booting into recovery mode and at the root prompt reconfigure X as follows:

```

X -configure
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
cp /root/xorg.conf.new /etc/X11/xorg.conf

```

Note this will only work if X is not running, so the easiest way to do this is to use the recovery mode option from the grub menu.  The first line creates a new xorg.conf file at /root/xorg.conf.new.  The second line backs up the old xorg.conf file.  The third line copies the new xorg.conf file to the old one.  If anyone can get this to work, please let me know and I'll update the instructions.
**END EDIT**

My Dell E6510 (i5) has the intel video card.  These instructions worked for me with the 32-bit installation.  The basic idea is to configure your machine to run the backported maverick kernel (this could lead to instability, but I've been running it for a couple of weeks now with no problems).

1. Boot the live environment with the following kernel parameters:

```
i915.modeset=0 xforcevesa
```

2. Do the standard install.  This will set up your environment with the vesa drivers.  After that you'll only need the following kernel parameter to boot your installed environment:

```
i915.modeset=0
```

3. Next, install the backported maverick kernel:

```
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update && sudo apt-get install linux-lts-backport-maverick
```

4. Last but not least, change the following line in your /etc/X11/xorg.conf file from

```
Driver "vesa"
```

to

```
Driver "intel"
```

5. Your machine should now reboot normally with no kernel parameters.


Getting wireless working with the backported kernel is a bit tricky, but here's how I did it (there may be an easier way):

1.  Make sure you have the kernel-headers for your kernel installed:

```
sudo apt-get install linux-headers-`uname -r`
```

2.  Next install the source for the wireless driver:

```
sudo apt-get install bcmwl-kernel-source
```

You'll likely get an error, but we'll fix that in the next few steps.

3. In /usr/src/bcmwl-5.60.48.36+bcom/src/wl/include/linuxver.h

change the line that says

```
#include <linux/autoconf.h>
```

to

```
#include <generated/autoconf.h>
```

4. Next get the patch wl_linux.c.diff from here [http://bugs.gentoo.org/248450](http://bugs.gentoo.org/248450)

5. Apply the patch by going to the 'src/wl/sys' folder and execute

```
sudo patch < [location_of_the_diff_file]
```

In my case the patch was in my Downloads folder so I executed ```
sudo patch < ~/Downloads/wl_linux.c.diff
```

6. Finally, reconfigure the package:

```
dpkg-reconfigure bcmwl-kernel-source
```

This should build and install the driver.  Now when you reboot, you should have wireless.

---

### Post by ramsrambo on 2010-09-06
Hi,

I need some one to make me understand how while booting from live cd support NVS nvidia graphics card ?

Core i7 cpu needs external grpx card without which you cannot display. So while ubuntu booting I think it is failing to address this problem.

Anyway to overcome this ?

---

### Post by joculi on 2010-09-08
The pre-install steps below worked for me:

> **daz23 said:**
> The just released Ubuntu 10.04.1 LTS has the same issue with the Nouveau driver on a e6510 (core i7, 4gb ram, nvidia NVS3100M, and SSD) laptop.

The steps in this thread fixed it. Here's a summary:

Pre-Install:

1.Boot from the CD and hit any key to get to the menu screen.
2.At the install screen press "F6", "Esc", and delete "quiet" and "splash" from the command line. 
3.Add "nomodeset" at the end of the line.
4.Press "Ctrl" and "X" to boot.
5.Install Ubuntu



But after install, I was unable to get to the grub menu by holding down the shift key...

> **daz23 said:**
> 
Post-Install:

1.During boot hold down the shift key to get to the grub menu.
2.Press the 'e' key to edit the boot command
3.Use arrow keys to move to end of line, and delete "quiet" and "splash" from the command line.
4.Add "nouveau.modeset=0" at the end of the line.



I ended up having to boot using the live CD and mount my harddrive partition where ubuntu is installed.  My partition happened to be /dev/sda7.  Yours may be different.

1.  boot from live CD
2.  sudo mkdir /media/sda7
3.  sudo mount /dev/sda7 /media/sda7

This is where it gets tricky. Normally, you edit grub by editing /etc/default/grub and then run update-grub.  That did not work when booted from the live CD.  So I directly edited grub.cfg.  backup your grub.cfg first in case of disaster.

4.  cp /media/sda7/boot/grub/grub.cfg /media/sda7/home/<your username>/
5.  vi /media/sda7/boot/grub/grub.cfg
6.  find the line with "quiet splash" and add nouveau.modeset=0
7.  save the file
8.  reboot from the harddrive (not the live CD)

The other steps listed in posts above about setting up the nvidia driver are also necessary.

---

### Post by dfhoughton on 2010-09-23
I posted this in another thread, but just to be thorough, here it is again.

The GRUB menu gave me a lot of trouble but I finally figured out how to get it.

[LIST]
[*]You need to press shift, not escape, to get the GRUB menu with GRUB 2. This change in convention threw me off for a while.
[*]The BIOS, I find, is a little flaky. If you press shift too soon it will throw a rod and die. Wait for the underscore cursor to appear. But don't wait too long! (See next point.)
[*]Getting the GRUB menu is like blowing up the Death Star. You have a small window of opportunity and you can't use instruments. You have to use the Force to find that window. Holding shift doesn't work. Press the shift key manically and you are likely to get the menu.
[/LIST]

---

### Post by vevel on 2010-09-28
> **daz23 said:**
> The just released Ubuntu 10.04.1 LTS has the same issue with the Nouveau driver on a e6510 (core i7, 4gb ram, nvidia NVS3100M, and SSD) laptop.

The steps in this thread fixed it. Here's a summary:

Pre-Install:

1.Boot from the CD and hit any key to get to the menu screen.
2.At the install screen press "F6", "Esc", and delete "quiet" and "splash" from the command line. 
3.Add "nomodeset" at the end of the line.
4.Press "Ctrl" and "X" to boot.
5.Install Ubuntu

Post-Install:

1.During boot hold down the shift key to get to the grub menu.
2.Press the 'e' key to edit the boot command
3.Use arrow keys to move to end of line, and delete "quiet" and "splash" from the command line.
4.Add "nouveau.modeset=0" at the end of the line.
5.Press "Ctrl" and "X" to boot.
6.Go to System - Hardware Drivers and install the Nvidia proprietary drivers.
[...]
8.Reboot

Thanks -- this was all I needed to get my system running.

---

