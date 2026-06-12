---
title: "Wireless and others."
date: 2010-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rsellzey on 2010-11-23
Hello all, I have just installed ubuntu's 10.10 version alongside Windows 7 to make a dual boot system. I am having trouble starting my wireless as it says permission denied, and I can't edit the config file. Any and all help is appreciated. I'll try to answer any other questions that you might need to know.

---

### Post by ugm6hr on 2010-11-23
The more information you give us, the easier it will be to understand what's going on.
Look at the Wifi help? link below, and try and provide as much of the detail as suggested.
Also - how did you install Ubutnu - from within Windows as if it was a program, or did you boot directly from an Ubuntu CD, bypassing Windows?
It is not necessary to "start" your wifi at all - please explain what you mean by that, and describe the exact process you go through to get the error.
Obviously, this may seem tedious, but the likelihood is there is a simple solution, but it's very hard to help without knowing what you've done so far.

---

### Post by Jeddd7 on 2010-11-23
go to system-Administration-Additional Drivers,
install drivers first and wifi will now connect!

---

### Post by rsellzey on 2010-11-23
I installed ubuntu on a flash drive, and then restarted the computer and did a boot from usb. Then, I chose to install it. I shrunk the win. 7 partition and created a new one for ubuntu. Everything went fine and I can boot into ubuntu using the grub. I was going to change it to put win. 7 as my first option, and it said permission denied when i try to write what i have changed. So, I go and check my privileges and I see that I have administrative privileges. Then, I was going to connect to the internet to look up some possible fixes to that problem, when then I figure out that I can't connect on my wireless (built in). I switched over to windows to look up some commands to turn on the card, found it and then i use the code and it said permission denied again.

Thanks for the help.

---

### Post by rjaymo on 2010-11-23
I just finished going thru looking at google info wireless installs. what worked for me is 3 step.
first u do need a hard lan connected. Add software: wifiradar then
  1. go to software installation area again install b43-fwcutter
     and firmware-b43-installer

then u can setup wireless connections via wifiradar is easy.

dont know if this would help. laptops have different types of cards.
ray

---

### Post by ugm6hr on 2010-11-24
You have installed as a true dual-boot (not with Wubi).
Instructions to edit Grub2 (the program which controls which is the default operating system): [https://help.ubuntu.com/community/Grub2#Configuring GRUB 2](https://help.ubuntu.com/community/Grub2#Configuring GRUB 2)
In order to do so, it is easiest to use the Terminal:
```
sudo cp /etc/default/grub /etc/default/grub_backup
gksudo gedit /etc/default/grub
```
The 1st command will create a backup of the original. The second will allow you to edit (and save) the original. It will ask for your password - type it in when asked and press enter (it may not show what you type for security reasons)
You want to add/edit a line (where **** is replaced by the line that represents Windows 7):
```
GRUB_DEFAULT="****"
```
> **rsellzey said:**
> Then, I was going to connect to the internet to look up some possible fixes to that problem, when then I figure out that I can't connect on my wireless (built in). I switched over to windows to look up some commands to turn on the card, found it and then i use the code and it said permission denied again.
What commands did you use? And how did you find them? Generally, you need to install a "driver" for wifi, rather than turning it on. We need the output from the following commands to work out what wifi card you have:
```
lspci
lshw -class network
```
Do you have a wired cable you could use temporarily? As rjaymo says, some cards require a driver to be downloaded, and it is much easier if you can do that from within Ubuntu with a wired ethernet connection.

---

### Post by rsellzey on 2010-11-27
Thanks Ugm6r, I have the grub doing what I want.

Now about the wireless, I did the additional drivers and here is what I got:
Broadcom B43 Wireless Driver
Broadcom STA Wireless Driver.

---

### Post by ugm6hr on 2010-11-27
I'd suggest the STA driver as 1st choice for most:
```
sudo apt-get --reinstall install bcmwl-kernel-source
```
You need to be plugged in with a wire to do this.

---

### Post by rsellzey on 2010-11-30
Thanks. Now I'm going to try and figure out wifi radar. Thanks for everyone's help. :p

---

### Post by ugm6hr on 2010-11-30
Network Manager is very good.... Why wifi radar?

---

### Post by fallofshadows on 2010-11-30
I figured this would be the best place to post my own question, seeing as it's pretty much the same topic.

I have a dell inspiron 1545, running ubuntu 10.10 64 bit. It can't detect any wireless networks, but works fine on ethernet cable.

lspci: Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

When I try installing the bundle I need via Synaptic Package Manager:E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1

Further detail of the error: not supported low-power chip with PCI id 14e4:4315! Aborting.

Does anyone have a step-by-step solution? I'm loving ubuntu right now, but this is a pain.

By the way, please be very detailed in any sort of response, especially if it involves the terminal. I'm kindof new to ubuntu, and the terminal scares me a bit haha.

Thanks!

---

### Post by ugm6hr on 2010-12-01
> **fallofshadows said:**
> lspci: Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

When I try installing the bundle I need via Synaptic Package Manager:E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1

Did you try...
```
sudo apt-get --reinstall install bcmwl-kernel-source

```
Make sure you have plugged into a wired ethernet connection at the time.

---

### Post by fallofshadows on 2010-12-01
Sorry for the big response, but here's what the terminal tells me: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.60.48.36+bdcom
Kernel:  2.6.32-24-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-24-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$

---

### Post by ugm6hr on 2010-12-02
How have you installed Ubuntu 10.10?
Is it "properly" installed on your hard drive, or installed as if using from a USB stick? Did you install from within Windows?

I suspect this may contain the solution:
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023)

---

### Post by fallofshadows on 2010-12-02
Its a proper install from a usb, created a new partition. My problem has been solved though! There is a driver on the package manager that is specifically for my chip, and I finally found it due to an old forum thread :D

---

### Post by rsellzey on 2010-12-26
Sorry for being gone for so long but, I'm back and I still can't enable my wifi. What else do you need to know?

Also, what package did you download fallofshadows?

---

### Post by ugm6hr on 2010-12-27
As before....
> **ugm6hr said:**
> 
```
lspci
lshw -class network
```


Also - I would suggest returning to the Ubuntu default (i.e. Network manager - not Wifi Radar).

---

### Post by rsellzey on 2010-12-27
[B]lspci:
[/B]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)

[B]lshw -class network:
[/B]*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:aa:4b:a4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:49:5b:c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:fa000000-fa003fff

---

### Post by ugm6hr on 2010-12-28
> **rsellzey said:**
> 
  *-network **DISABLED**
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:49:5b:c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:fa000000-fa003fff
The problem is it's turned off.
I can confirm you have the identical wifi card to mine (mini 9). It works fine with Network Manager in 10.10, if installed from default setup as I described.
You have installed the driver correctly (wl0).
Is there a hardware / software / BIOS switch to turn the device on / off?

---

### Post by rsellzey on 2010-12-28
I have a switch on the side of my laptop, and I usually keep it on. I checked the bios and it says it was enabled, probably from having the switch on.

Also, when I click on the wifi symbol on the menu bar the "enable wireless" is grayed out.

---

### Post by ugm6hr on 2010-12-29
Only other thing I can think of is section 9 of the Wifi help? link below.
Did you have Windows on the computer before?

---

### Post by rsellzey on 2010-12-29
Yes, Windows was on here before installing Ubuntu 10.10.

---

### Post by rsellzey on 2011-01-01
I have done some snooping. Under /sys/class/net all I have is eth0  eth1  lo. According to another post I'm suppose to have wlan0 in there. Do I need to create it?

---

