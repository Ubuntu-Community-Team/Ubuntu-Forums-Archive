---
title: "Vostro 3460 wireless and ethernet"
date: 2013-08-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drm200 on 2013-08-25
I have a Dell Vostro 3460 with networking cards the similar as noted in your Dell 3460 certified for Ubuntu.  The machine originally had windows 7 installed and both wifi and Ethernet worked without problem.

I first installed Ubuntu ubuntu-12.04.2-desktop-amd64 on the machine.  The result was:
Wifi - Functions properly after I would manually install the Broadcom STA wireless driver after boot
Ethernet - not working.  I have the Atheros 8161/8165 card.

I then installed ubuntu-12.04.3-desktop-amd64.  The results are:
Ethernet -functions immediately after boot without problem.
Wifi - The Broadcom STA wireless driver fails to install.  So now the wifi does not function (but bluetooth seems to function).

If I revert back to 12.04.02 the Broadcom STA wireless driver will again install properly ... but the ethernet will not work.

I'm not sure where to go from here ... my linux experience is very limited ... but I'd like to see this resolved in the next version.

---

### Post by carl4926 on 2013-08-25
Please let us see

```
lspci -nnk
```Just the networking parts is sufficient

---

### Post by drm200 on 2013-08-26
Ok.  I've freshly booted .. tried to install the Broadcom STA driver ... received the "Sorry installation of the driver failed" message
and now I run lspci -nnk

Below is what I get.  I don't see the wireless card identified.  In Windows it shows up as Model Dell Wireless 1704 802.11b/g/n (2.4GHz) from Broadcom with device ID of 4365h



this@this:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)    Subsystem: Dell Device [1028:0563]
00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 5 [8086:1e18] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e57] (rev 04)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)    Subsystem: Dell Device [1028:0563]
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0de9] (rev a1)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)    Subsystem: Dell Device [1028:0016]
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)    Subsystem: Dell Device [1028:0563]
    Kernel driver in use: alx
    Kernel modules: alx

---

### Post by carl4926 on 2013-08-26
You need a wired connection and do

```
[COLOR=#000000][FONT=Droid Sans]sudo apt-get install bcmwl-kernel-source[/FONT][/COLOR]

```

When done reboot

---

### Post by drm200 on 2013-08-26
Ok .. I have run the command to install the bcmwl-kernel ... But the installation fails with the following details:

this@this:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following extra packages will be installed:
  dkms fakeroot

The following NEW packages will be installed:
  bcmwl-kernel-source
 dkms fakeroot
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.

Need to get 0 B/1,504 kB of archives.
After this operation, 4,943 kB of additional disk space will be used.

Do you want to continue [Y/n]? y

W: Duplicate sources.list entry cdrom://This/multiboot/ubuntu120464/ precise/main i386 Packages (/var/lib/apt/lists/This_multiboot_ubuntu120464_dists_precise_main_binary-i386_Packages)


W: Duplicate sources.list entry cdrom://This/multiboot/ubuntu120464/ precise/restricted i386 Packages (/var/lib/apt/lists/This_multiboot_ubuntu120464_dists_precise_restricted_binary-i386_Packages)


Selecting previously unselected package dkms.
(Reading database ... 146259 files and directories currently installed.)

Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3.1_all.deb) ...

Selecting previously unselected package bcmwl-kernel-source.
acking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_amd64.deb) ...

Processing triggers for man-db ...

Setting up dkms (2.2.0.3-1ubuntu3.1) ...

Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...

Loading new bcmwl-6.20.155.1+bdcom DKMS files...

First Installation: checking all kernels...

Building only for 3.8.0-29-generic
Building for architecture x86_64

Building initial module for 3.8.0-29-generic

ERROR (dkms apport): kernel package linux-headers-3.8.0-29-generic is not supported
Error! 
Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)

Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.

FATAL: Module wl not found.
update-initramfs is disabled since running on read-only media

Setting up fakeroot (1.18.2-1) ...

update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

W: Duplicate sources.list entry cdrom://This/multiboot/ubuntu120464/ precise/main i386 Packages (/var/lib/apt/lists/This_multiboot_ubuntu120464_dists_precise_main_binary-i386_Packages)

W: Duplicate sources.list entry cdrom://This/multiboot/ubuntu120464/ precise/restricted i386 Packages (/var/lib/apt/lists/
This_multiboot_ubuntu120464_dists_precise_restricted_binary-i386_Packages)

W: You may want to run apt-get update to correct these problems
this@this:~$

---

### Post by drm200 on 2013-09-08
Is there any experts out there that can help with this problem on my "Ubuntu certified" Dell?  Should I repost in another forum?

---

### Post by Hadaka on 2013-09-08
Hi , please do...
```
sudo apt-get update
sudo apt-get upgrade
```
boot..and see if the wireless is working.
*if not..
see.
[http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923](http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923)
while this is for 12.10 and ONLY 64 bit. It should work for you.
you will notice in your last printout..you are attempting to load -i386- 32bit.
Try the link,if it still fails, ask a mod to move your thread to WIRELESS.
thanks.

---

### Post by drm200 on 2013-09-11
I'm travelling in Asia now and do not have access to ethernet connection.  I access the internet by booting into windows and using wireless. .. so I don't know how to do the update/upgrade since wifi is not working in Ubuntu and I don't have an ethernet connection.

So then I followed your other idea in the link you provided.  So I boot windows and search for "linux-headers-generic build-essential dkms.deb".  I find this package:
"linux-headers-3.2.0-53-generic_3.2.0-53.81_amd64.deb" .. but am not sure it is correct.  Anyway I download and try to install this package.
However, the install fails for more dependencies" as you can see in the error message below:

Unpacking replacement linux-headers-3.2.0-53-generic ... dpkg: dependency problems prevent configuration of linux-headers-3.2.0-53-generic:
 linux-headers-3.2.0-53-generic depends on linux-headers-3.2.0-53; however:  Package linux-headers-3.2.0-53 is not installed.
dpkg: error processing linux-headers-3.2.0-53-generic (--install):

Is there a method I can use to identify/download while in windows all of the packages required so that I can later install after Ubuntu boot?  

thanks

.

---

### Post by varunendra on 2013-09-12
Please post the output of -
```
modprobe -c | grep -i 14e4.*4365
```

To download a package and its dependencies, you can use "apt-get install..." with --print-uris option. This options makes apt to print the download URIs of all the required packages instead of itself trying to download and install.

To do this with the sta driver, build-essential and headers, please run command (sudo is not required) -
```
apt-get install --print-uris linux-headers-generic build-essential bcmwl-kernel-source
```
If prompted with Y/N to install, go ahead with "Y". Instead of downloading, it will print the URIs of all the required packages (plus their MD5Sums in front of them) at the bottom of the output.

Copy all these URIs in a text file and use them to manually download the packages.

Copy these downloaded packages in a new empty directory on your desktop (to avoid confusion, let's name the directory packages), then open a terminal and do -
```
cd Desktop/packages
sudo dpkg -i *
```
This will install all the packages within the directory. Post back the full output of "dpkg -i" in terminal, so we can ensure everything went fine.

I've recently seen the default sta driver fail to build on newer kernels on some systems. If that happens in your case too, we may have to try another version, a newer one that is not yet included in the default repositories.

---

### Post by Nitesh_Sahay on 2013-09-13
I am completely new user getting into Ubuntu. I am facing the same problem with my dell vostro machine. When I connect wi-fi, it gives a message saying Wi-fi connected but when I open the internet browser, it says cannot load the page. When I try the wired connection, it works absolutely fine. I tried to implement the above steps as faithfully as was possible for me but it did not work.

---

### Post by drm200 on 2013-09-13
1.  After running the "modprobe -c | grep -i 14e4.*4365"  there were no results returned.  Of course "modprobe -c" without the grep filter returned pages of results.

2. Next  I ran the "apt-get install --print-uris linux-headers-generic build-essential bcmwl-kernel-source" and 16 files were identified .... 3 on my hard disk and 13 for download.  I downloaded the 13 files into a directory named "packages" and copied the other 3 files to the same directory.

I then changed to the packages directory and ran: sudo dpkg -i *

The install failed you will see below.  

this@this:/media/BU_Data/packages$ sudo dpkg -i *
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 146259 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from build-essential_11.5ubuntu2_amd64.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from dkms_2.2.0.3-1ubuntu3.1_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from dpkg-dev_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from fakeroot_1.18.2-1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from g++_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from g++-4.6_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from libalgorithm-diff-xs-perl_0.04-2build2_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from libdpkg-perl_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package libstdc++6-4.6-dev.
Unpacking libstdc++6-4.6-dev (from libstdc++6-4.6-dev_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-23.
Unpacking linux-headers-3.2.0-23 (from linux-headers-3.2.0-23_3.2.0-23.36_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-23-generic.
Unpacking linux-headers-3.2.0-23-generic (from linux-headers-3.2.0-23-generic_3.2.0-23.36_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from linux-headers-generic_3.2.0.23.25_amd64.deb) ...
Setting up dkms (2.2.0.3-1ubuntu3.1) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up linux-headers-3.2.0-23 (3.2.0-23.36) ...
Setting up linux-headers-3.2.0-23-generic (3.2.0-23.36) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Setting up linux-headers-generic (3.2.0.23.25) ...
Processing triggers for man-db ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-29-generic
Building for architecture x86_64
Building initial module for 3.8.0-29-generic
ERROR (dkms apport): kernel package linux-headers-3.8.0-29-generic is not supported
Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
FATAL: Module wl not found.
update-initramfs is disabled since running on read-only media
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2) ...
this@this:/media/BU_Data/packages$

---

### Post by varunendra on 2013-09-13
> **drm200 said:**
> 
Building initial module for 3.8.0-29-generic
ERROR (dkms apport): kernel package linux-headers-3.8.0-29-generic is not supported
**[COLOR="#FF0000"]Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)[/COLOR]**
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
**[COLOR="#FF0000"]FATAL: Module wl not found.[/COLOR]**

Okay, just like I suspected.

Please remove the current version -
```
sudo apt-get purge bcmwl-kernel-source
```

I'm not sure if a package installed with dpkg can be removed by apt-get. So if the above gives any error, (only then) please remove it with -
```
sudo dpkg --purge bcmwl-kernel-source
```

Then download the newer .deb package (bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu3_amd64.deb) from [launchpad]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504") and simply double-click to install it with Software Center.

Hope it'll install without any troubles. Let us all know how well it performs.

**PS:**
Please always use 'Code' tags to post commands and outputs. It preserves its formatting and puts it in a nice box thus making the post look cleaner, compact and easier to read.
Follow the "Using Code Tags" link in my signature to see how. You might wish to edit your above post to do it now.. :)

---

### Post by drm200 on 2013-09-13
I'm running Ubuntu from a "live USB" so I've modified your instructions slightly ... As I still do not have an available ethernet connection, I booted windows and searched/downloaded  "bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu3_amd64.deb"  I then copied this file to the "packages" folder created earlier with all the dependencies.  I erased the old file "bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb" from the "packages" folder.

The "packages" folder now contains the following files:

bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu3_amd64.deb
build-essential_11.5ubuntu2_amd64.deb
dkms_2.2.0.3-1ubuntu3.1_all.deb
dpkg-dev_1.16.1.2ubuntu7_all.deb
fakeroot_1.18.2-1_amd64.deb
g++_4.6.3-1ubuntu5_amd64.deb
g++-4.6_4.6.3-1ubuntu5_amd64.deb
libalgorithm-diff-perl_1.19.02-2_all.deb
libalgorithm-diff-xs-perl_0.04-2build2_amd64.deb
libalgorithm-merge-perl_0.08-2_all.deb
libdpkg-perl_1.16.1.2ubuntu7_all.deb
libstdc++6-4.6-dev_4.6.3-1ubuntu5_amd64.deb
libtimedate-perl_1.2000-1_all.deb
linux-headers-3.2.0-23_3.2.0-23.36_all.deb
linux-headers-3.2.0-23-generic_3.2.0-23.36_amd64.deb
linux-headers-generic_3.2.0.23.25_amd64.deb

I did a change directory to the packages folder and then ran the following command:

sudo dpkg -i *

All the packages install without error and wifi immediately becomes available and functions without problem.    The only issue is Ubuntu still pops up an icon wanting to install the old driver. If I click on it ... the system crashes. (I previously tried the "sudo apt-get purge bcmwl-kernel-source" command but there was nothing found to uninstall.) But this is not really an issue for me. I just won't click on the icon to install the old driver.

I'm marking the issue solved.

Hopefully, this problem will be resolved in the next Ubuntu release.  So I hope someone picks this up.

many thanks.

---

### Post by varunendra on 2013-09-13
> **drm200 said:**
> The only issue is Ubuntu still pops up an icon wanting to install the old driver. If I click on it ... the system crashes. (I previously tried the "sudo apt-get purge bcmwl-kernel-source" command but there was nothing found to uninstall.)

Hmm perhaps we should have tried "dpkg --purge" straightaway. I believe you can also do it now, only you'll have to install the newer one again.

But anyway, great that it finally worked, and thanks for your modified instructions. I'm sure it'll help those who are in the same situation as you (no way to connect to internet).

Thanks for the feedback ! :)

---

### Post by drm200 on 2013-09-13
Actually, I also tried the purge .. but got a message that i did not have sufficient "rights" or "privileges"  .. I don't remember the exact wording.

---

### Post by varunendra on 2013-09-13
> **drm200 said:**
> Actually, I also tried the purge .. but got a message that i did not have sufficient "rights" or "privileges"  .. I don't remember the exact wording.

Aaaarrrrghh ! I forgot "sudo". #-o

Correcting now, for others who may follow this later...

---

### Post by drm200 on 2013-09-13
Actually, your initial instruction was: 

sudo dpkg --purge bcmwl-kernel-source

and this was the instruction that I ran that resulted in insufficient rights or privileges.   

I was thinking it failed because I am using a "live USB" so maybe it can not delete the file ...

---

### Post by varunendra on 2013-09-13
> **drm200 said:**
> Actually, your initial instruction was: 

sudo dpkg --purge bcmwl-kernel-source

No it wasn't. I edited that post to add sudo after realizing my mistake. See the edit comment in the post.

Live system only fails to update the kernel/initramfs image, which are freezed. Rest of the package installation goes normally, as does their removal.

---

### Post by drm200 on 2013-09-13
When I run the purge command this is what I get:

this@this:~$ sudo dpkg --purge bcmwl-kernel-source
dpkg: warning: there's no installed package matching bcmwl-kernel-source

So I am unable to delete the old file.  Also, once I have wifi working and shut my pc and reboot ... wifi no longer works.  I need to re-install the packages to get wifi working after a PC reboot.  Once, I run the sudo dpkg -i * command again, wifi works without problem.

If i go to the directory on my USB drive where the Ubuntu files are stored, you will see that Ubuntu shows that the Ubuntu files are stored under
 a directory called "cdrom":
this@this:/cdrom/multiboot/ubuntu120464$

In fact, if I try to create/edit a text file on my live USB from within Ubuntu, it refuses with an indication that it is read only

However, if I explore the USB from within Windows, there is no directory called "cdrom".  And Windows allows me to create/edit any file on the USB I want.  So for some reason, Ubuntu believes my USB is a readonly CDRom.

Maybe the behavior is different than expected because of how I have setup the live disk.  I use a small program in windows called "yumi.exe".   It allows me to easily/quickly create a multiboot USB drive with various different program iso images. I think Yumi may be preventing the save of changes .. so that upon every start (of any of the installed programs) is like a clean start.

I'm fine with how things are working and have learned quite a bit during the exchange.

---

### Post by carl4926 on 2013-09-13
> [COLOR=#000000]Also, once I have wifi working and shut my pc and reboot ... wifi no longer works. I need to re-install the packages to get wifi working after a PC reboot. [/COLOR]Excuse me, but this sounds like a blacklisting issue.
However, unless the system is completely up to date, building source packages will be an issue.

And, for what it's worth. Broadcom have not updated their drivers in so long, it isn't even funny.

---

### Post by varunendra on 2013-09-14
> **drm200 said:**
> ...once I have wifi working and shut my pc and reboot ... wifi no longer works.  I need to re-install the packages to get wifi working after a PC reboot.  Once, I run the sudo dpkg -i * command again, wifi works without problem.
The problem is not the system, the package, the installation method or even the USB. Problem is the fact that you are doing this on a live system.

In order to load a module at startup, its information needs to be updated in initramfs - the initial boot image that loads initial modules. However, updating the kernel image or initramfs is NOT allowed on a live system. So even though the module is there, the system does not know it has to be loaded at boot time.

You can try one of two things to make it load at startup (assuming that "wl.ko" file remains in your "**/lib/modules/*<kernel version here>*/kernel/drivers/net/wireless/**" directory at next boot) :

1) add **wl** to your /etc/modules file
2) add **modprobe wl** to your /etc/rc.local file (make sure to insert this line above the 'exit 0' line. This file MUST end with "exit 0" line)

I'm pretty sure the wl.ko module should remain in the above said directory, but am not dead sure. So if it disappears, there are other ways to make it load at boot time, but probably not worth the trouble IMHO.

Some more explanation -
> So for some reason, Ubuntu believes my USB is a readonly CDRom.
The live boot is designed that way. The medium (or the partition of the medium) from which it boots, is loaded as cdrom, thus read-only.

The only 'writable' part in this partition is the 'casper-rw' file which is loaded as the filesystem that you see in the live session (the whole root (/) hierarchy, except that updating kernel and initramfs is not permitted)

> I think Yumi may be preventing the save of changes .. so that upon every start (of any of the installed programs) is like a clean start.
I use YUMI and like it. :) It is not YUMI, but the way that a live system works, like I explained above *(to be honest, I don't know every bit of how a live system works, but am pretty confident with what I shared above)*.

@ carl4926,

The blacklisting is an integral part of the installation of wl driver's .deb package. It does not matter how you installed it, with USC, Synaptic, apt-get or dpkg... if the package is .deb, the blacklisting will be part of it. You can open the .deb package with archive manager and check the "postinst" file in the "DEBIAN" directory within the .deb package. This directory controls how a package is installed (or uninstalled later)

I'm also quite certain that this /etc/modprobe.d/blacklist-bcm43.conf file is retained in the persistent part, thus is already present in the next boot. So I believe the initramfs (initrd.img...) is all that is the problem, and can not be solved in a live session. But there are workarounds to every problem. :)

---

### Post by carl4926 on 2013-09-14
> [COLOR=#000000]I'm also quite certain that this /etc/modprobe.d/blacklist-bcm43.conf file is retained in the persistent part,[/COLOR]Yes, if 'wl' is installed

> [COLOR=#000000]Problem is the fact that you are doing this on a live system.[/COLOR]Sorry - I missed that

---

### Post by drm200 on 2013-09-14
The module wl is not to be found in the "/lib/modules/<kernel version here>/kernel/drivers/net/wireless/" directory.   I do have a similar named file "wl3501_cs.ko" in that directory. 

I did find the wl.ko module in this directory: /lib/modules/3.8.0-29-generic/updates/dkms

So I went ahead and tried adding the line "wl" to /etc/modules file but it did not load the module on reboot. At first I didn't have permissions to edit the modules file .. 
so I used the command:  gksudo gedit /etc/modules

I was then able to edit/save the file.  And before reboot I reopened the module file just to confirm "wl" command was still there.

However, after reboot .. when there was no wireless, I again checked the modules file .. The "wl" line that I had added was gone.  I'm guessing that Ubuntu is erasing the command as it cannot find the wl module ...

---

### Post by varunendra on 2013-09-14
> **drm200 said:**
> I did find the wl.ko module in this directory: /lib/modules/3.8.0-29-generic/updates/dkms
That's okay, I forgot about the dkms package. It manipulates the driver to be able to maintain it, which is fine.

> However, after reboot .. when there was no wireless, I again checked the modules file .. The "wl" line that I had added was gone.  I'm guessing that Ubuntu is erasing the command as it cannot find the wl module ...

It can't erase that file by itself, but maybe it is not keeping that file either. Means it is part of the live boot, not the persistent part.

Try the adding the "modprobe wl" command in the /etc/rc.local file, although I now suspect the whole /etc directory maybe non-persistent. Did you check the /etc/modprobe.d directory? Was the /etc/modprobe.d/blacklist-bcm43.conf file retained? Or that one got deleted too?

In that case, the best we can do is to create a script and save it to your desktop or home to do the installation with a double-click or a single command anytime anywhere.

---

### Post by drm200 on 2013-09-14
Ok .. I've tried adding the "modprobe wl" command in the /etc/rc.local file.   I edit the file/save/close/reopen to verify the changes are intact.  I then reboot.  The driver does not load and after boot the rc.local file no longer has the "modprobe wl" command line that was added..

The "blacklist-bcm43.conf" file was still in the directory /etc/modprobe.d.     I did take a look at the contents of the "blacklist-bcm43.conf" file and the first line had a comment saying that this file is autogenerated and all changes will be lost.

---

### Post by varunendra on 2013-09-14
Nice ! Everything needed to make life easier is stolen away on each boot :P

What if you just do -
```
sudo modprobe wl
```
Does the wifi jump to life?

Just to (hopefully) make my next post a final and solid fix, please confirm above, plus - does the "dpkg -i *" alone (from the packages directory) make it work each time?

---

### Post by drm200 on 2013-09-14
1.  I ran the command "sudo modprobe wl" after reboot. ... It fails with an error indicating it can not find wl.   I told you earlier that I had found the "wl" in the  directory "/lib/modules/3.8.0-29-generic/updates/dkms"  That is true ... but I failed to notice that the file is not there until I run the command "sudo dpkg -i *" which installs wl ... 

2. The command "sudo dpkg -i *" after reboot has always brought the wifi to life.  Never an error so far ... Maybe 30 reboots/installs..   I've attached the log for the install.   You can see where it is looking for wl ... fails to find it with a message "No original module exists within this kernel" and then installs it in the /dkms directory.

3. I still get the icon to install the old Broadcom STA driver .. but it is not a problem.  I just don't click on it.

this@this:/media/BU_Data/Ubuntu/Ubuntu_Wifi_fix$ sudo dpkg -i *
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 146259 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu3_amd64.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from build-essential_11.5ubuntu2_amd64.deb) ...
Selecting previously unselected package dkms.
Unpacking dkms (from dkms_2.2.0.3-1ubuntu3.1_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from dpkg-dev_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from fakeroot_1.18.2-1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from g++_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from g++-4.6_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from libalgorithm-diff-xs-perl_0.04-2build2_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from libdpkg-perl_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package libstdc++6-4.6-dev.
Unpacking libstdc++6-4.6-dev (from libstdc++6-4.6-dev_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-23.
Unpacking linux-headers-3.2.0-23 (from linux-headers-3.2.0-23_3.2.0-23.36_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-23-generic.
Unpacking linux-headers-3.2.0-23-generic (from linux-headers-3.2.0-23-generic_3.2.0-23.36_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from linux-headers-generic_3.2.0.23.25_amd64.deb) ...
Setting up dkms (2.2.0.3-1ubuntu3.1) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up linux-headers-3.2.0-23 (3.2.0-23.36) ...
Setting up linux-headers-3.2.0-23-generic (3.2.0-23.36) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Setting up linux-headers-generic (3.2.0.23.25) ...
Processing triggers for man-db ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7) ...
Setting up bcmwl-kernel-source (6.30.223.30+bdcom-0ubuntu3) ...
Loading new bcmwl-6.30.223.30+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-29-generic
Building for architecture x86_64
Building initial module for 3.8.0-29-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-29-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs is disabled since running on read-only media
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2) ...
this@this:/media/BU_Data/Ubuntu/Ubuntu_Wifi_fix$

---

### Post by varunendra on 2013-09-14
Well then, the mystery of wl.ko solved. I was wondering how it is keeping the module when it can't even keep its configuration files. I bet the .conf file you saw in /etc/modprobe.d was also there only after performing "dpkg -i *".

So, we are limited to the live user's own configuration settings and thus probably can't automate things normally. By 'normally' I mean that we may be able to add a command to syslinux boot line to run an installation script automatically, but that may take more tinkering than it is worth of.

Now assuming it at least preserves changes in your Home directory and desktop, we can create an installation script, but that will have to be run manually. Which is not much different than running "dpkg -i *". But if you still wish to use that, here's the recipe -
[indent]
1) Create a folder "bcmwl" in your Home directory. Copy all the .deb files in it.

2) Open the text editor, and copy-paste the following in it -
```
#!/bin/bash
cd ~/bcmwl && sudo dpkg -i *
```

3) Save this file as "wl.sh" in the "bcmwl" directory.

4) Open a terminal and do the following -
```
chmod +x bcmwl/wl.sh
ln -s ~/bcmwl/wl.sh ~/Desktop
ln -s ~/bcmwl/wl.sh ~/
```
[/indent]
This will make the script "wl.sh" executable, and create symbolic links to it in your Home and Desktop directories. On next boot, you can either double-click > Run this file (link) from desktop, or run "./wl.sh" from terminal.

Unless we can add this script (slightly modified) to the syslinux boot line, it may not get simpler than this.

---

### Post by drm200 on 2013-09-14
One of the concepts that has been bothering me is your expectation that their is persistence with the live USB ... I've not seen any persistence.  For example:
1. If I install a program like truecrypt and then reboot ... I need to reinstall again .. it does not persist
2. If I create a textfile on the desktop and after reboot ... the file is gone
3. If I create a textfile in the home directory and after reboot ... the file is gone.

So, I've been doing some other research on the persistence issue ... The yumi configuration file is accessible in the directory multiboot\menu .. 

The yumi configuration code that starts Ubuntu is this:

  menu label ^Run Ubuntu from this USB
  kernel /multiboot/ubuntu120464/casper/vmlinuz.efi
  append cdrom-detect/try-usb=true noprompt boot=casper floppy.allowed_drive_mask=0 ignore_uuid live-media-path=/multiboot/ubuntu120464/casper/ file=/multiboot/ubuntu120464/preseed/ubuntu.seed initrd=/multiboot/ubuntu120464/casper/initrd.lz splash -- 

I can modify the yumi configuration file and it persists.  On the web some others have had problems with 12.04 and persistence .. and they claimed that a "persistent" flag needs to be added to the ubuntu commandline.  I tried adding it after the "splash --" but did not see any difference.  Maybe you have some insight on this.

---

### Post by varunendra on 2013-09-14
Wow, another revelation to me. Yes I was assuming you have persistence enabled and I was obviously wrong. :P

Some explanation you may be interested in -

Besides the flag, it also needs a "casper-rw" file (actually containing an ext2/3 file-system) or an ext2/3 partition with the lable "casper-rw". This file (or partition) is what is used for persistence. The boot line you pasted doesn't contain the 'persistent' flag, so at present your live session is obviously not persistent. Even if the pen drive has the casper-rw file somewhere.

It is the same file that becomes your (persistent) filesystem when you are booted into the live system (means you get "into" the file in live mode, and that's where changes are stored).

I haven't used YUMI for adding Ubuntu yet (only for Win7, XP, HBCD, Slax, Slitaz, Clonezilla... etc.), and haven't used it for installing another OS for a long time. So I don't even remember if it offers persistence or not (I'm in Ubuntu, I'll have to boot Win7 to test that). Please check and let me know. If it by default does not offer persistence, I'm sure we can manually add that functionality, but it would be best if YUMI can do that on demand or automatically.

And now you have gotten me interested in doing the experiments myself, maybe tomorrow morning the first thing ;)

---

### Post by drm200 on 2013-09-14
Persistence had not been an issue for me (yet) as I previously did not have wifi ... It appears that Yumi can handle persistence for one application per USB .. There is several methods to create a Casper R/W file .. there is an app at penndrive linux called Casper Creator that can create the file in 1 GB increments .. In my case, I don't think so much space is required so I have downloaded a 512 mb Casper image file from: [http://unetbootin.sourceforge.net/diskimg/](http://unetbootin.sourceforge.net/diskimg/).    

I've not tried it out yet, but believe all I need to do is copy the image file to the USB root directory and add the flag "persistent" to the yumi configuration file for Ubuntu.

I probably would need a larger Casper file if I were to plan on keeping the Ubuntu live USB up to date ... but I don't plan to do that with this live USB ... I had tried to install truecrypt using apt-get update .... and the update files crashed  .. I don't remember the exact error message but it appears that the wireless files we are installing will break the  Ubuntu update process.  I have a specific use for this live USB and don't really need to do Ubunto updates once I have the basic Ubuntu functions working reliably. (and I'm hopeful that the next LTS release would have fixed the wireless issue).  I have no problem installing truecrypt as long as I don't do an "update" at the same time.

---

### Post by varunendra on 2013-09-15
Go ahead, try it. [Instructions]("http://unetbootin.sourceforge.net/diskimg/readme.txt") are also on the same page, although you have already understood them correctly. After making it persistent, you shouldn't need those funny workarounds at all. Just install the driver once and enjoy as long as you wish to keep the live system (or the persistence).

Be forewarned though, if you are going to use it frequently, it is quickly going to give you "/tmp out of space" error, even if you don't store many things in the persistent area. This is one of the few downsides of it - it gradually gets full.

To avoid that, you may choose to just copy the casper-rw file, but not add the "persistent" flag permanently. When you really need persistence, manually add it during the boot time by editing the boot line. I use this method on one of my pen drives to boot faster, because loading all the stuff (programs, drivers) I have in the persistent area makes its booting a lot slower.

---

### Post by drm200 on 2013-09-15
Ok .... I copied the casper r/w file to the root directory .. added the "persistent"flag to the configuration file ... boot Ubuntu .... install wireless, install truecrypt add a text file to the desktop and reboot ... On reboot the text file was still there on the desktop .. truecrypt was there and wireless works ... so everything looks good and is "persistent".

just one small note ... prior to having it setup for persistence the wireless install log completed with these last lines:

DKMS: install completed.
update-initramfs is disabled since running on read-only media
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2) ...
this@this:/media/BU_Data/Ubuntu/Ubuntu_Wifi_fix$ 

Now with persistence it tries to "update-initramfs" and fails.   I'm not sure if this is serious or not .. I've not seen any obvious problems resulting from the failure yet.

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
cp: cannot create regular file `/cdrom/casper/initrd.gz.new': No such file or directory
dpkg: error processing initramfs-tools (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
this@this:/media/BU_Data/Ubuntu/Ubuntu_Wifi_fix$

---

### Post by drm200 on 2013-09-15
the "Errors were encountered while processing: initramfs-tools" seems to be a common problem with 12.04 ... lots of info on the web ... So I'll try to chase it down.

thanks for all your help.

---

### Post by varunendra on 2013-09-15
> **drm200 said:**
> Now with persistence it tries to "update-initramfs" and fails.   I'm not sure if this is serious or not .. I've not seen any obvious problems resulting from the failure yet.

Refer to my previous comment -
> **varunendra said:**
> 
In order to load a module at startup, its information needs to be updated in initramfs - the initial boot image that loads initial modules. However, updating the kernel image or initramfs is NOT allowed on a live system.

I should have remembered that driver installation is persistent (I've myself written a few long posts about this and other properties, and why this makes it less versatile), but it's so long since I used a persistent live that I totally forgot it.

Anyway, like I mentioned above, it is normal and nothing serious. However, the installation of the wl driver blacklists brcmsmac and bcma drivers. So if you tried to use the live session on such a system that needs it, you'll have to manually unload wl and load the desired one. Either this, or just remove the "persistent" flag during boot time. Rest will be automatic (default).

---

