---
title: "Suspend - Hibernate not working - Advanced Linux User Needed"
date: 2011-08-19
forum: Desktop Environments
---

### Post by dwlima on 2011-08-19
SOLVED 

MSI X58-Pro E
Intel i7 920@2.67GHz
NVidia GTX570 loaded with Nvidia linux driver (closed out session X and uninstalled Nouveau kernal driver).

I have 2 hard drives
1) Windows 7 Ultimate. Suspend and Hibernate work fine.
2) Ubuntu 11.04. Suspend and hibernate do not work. Initially I found that the USB ports were disabled, so I issued the "echo **** > /proc/acpi/wakeup" commands. Now, the PC seems to wake up, but no signal is sent to the screen. Also, the mouse and keyboard lights do not work. I find it odd that the keyboard initiated some type of working behavior on the desktop (lights and fan turn on), but caps and num lock do not light.

In the bios, I have ACPI Function Enabled. ACPI Standby State is S3, and Resume From S3 By USB Device Enabled.

I have spent many hours on this and cannot remain with Linux (just switched over from MSFT) if I cannot put the desktop to sleep. I am at a loss. I have to continually re-boot my pc if I put it to sleep.

Please help.
David

---

### Post by OpenSage on 2011-09-21
> **dwlima said:**
> MSI X58-Pro E
Intel i7 920@2.67GHz
NVidia GTX570 loaded with Nvidia linux driver (closed out session X and uninstalled Nouveau kernal driver).

I have 2 hard drives
1) Windows 7 Ultimate. Suspend and Hibernate work fine.
2) Ubuntu 11.04. Suspend and hibernate do not work. Initially I found that the USB ports were disabled, so I issued the "echo **** > /proc/acpi/wakeup" commands. Now, the PC seems to wake up, but no signal is sent to the screen. Also, the mouse and keyboard lights do not work. I find it odd that the keyboard initiated some type of working behavior on the desktop (lights and fan turn on), but caps and num lock do not light.

In the bios, I have ACPI Function Enabled. ACPI Standby State is S3, and Resume From S3 By USB Device Enabled.

I have spent many hours on this and cannot remain with Linux (just switched over from MSFT) if I cannot put the desktop to sleep. I am at a loss. I have to continually re-boot my pc if I put it to sleep.

Please help.
David







I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time (although I never hibernate, so don't know if it will fix that). Hope this helps some people.\\:D/

---

### Post by dwlima on 2011-09-21
Thank you for your reply. I tried it to no avail. I tried the suspend from the menu and pm-suspend to make sure. I just get the big blinking underline cursor on the top-left screen. If you or anyone has any ideas, I would love to test them. For now, I just keep the PC running 24/7.

---

### Post by dwlima on 2011-09-29
I finally figured it out and some of these steps may help other suspend/resume issues others' are having. 

I updated my kernel to version 3.0.4
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.4-oneiric/)

1) sudo dpkg -i [linux-headers-3.0.4-030004_3.0.4-030004.201108301138_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.4-oneiric/linux-headers-3.0.4-030004_3.0.4-030004.201108301138_all.deb")
2) in order to "sudo dpkg -i [linux-headers-3.0.4-030004-generic_3.0.4-030004.201108301138_i386.deb"]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.4-oneiric/linux-headers-3.0.4-030004-generic_3.0.4-030004.201108301138_i386.deb") I first had to update my ATI driver and ran "ati-driver-installer-11-9-x86.x86_64.run" with the --force option
3) Next, before installing "sudo dpkg -i linux-image-3.0.4-030004-generic_3.0.4-030004.201108301138_i386.deb" I had to remove the ethernet module to avoid the r8169 error. I did this by using rmmod r8169 (or modprobe -r r8169). U can use lsmod to see what modules are installed.
4) I rebooted to load the newer kernel (use uname -r) to see current kernel.
5) I could not get display to work so I went here: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
6) I loaded the older kernel (2.6.38) and then:
$ sudo sh /usr/share/ati/fglrx-uninstall.sh $ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx $ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon $ sudo apt-get install xserver-xorg-video-ati $ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core $ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
7) I re-booted and loaded the new kernel and voila - suspend now works. 

What a nightmare that was.
DWLima

(SOLVED)

---

