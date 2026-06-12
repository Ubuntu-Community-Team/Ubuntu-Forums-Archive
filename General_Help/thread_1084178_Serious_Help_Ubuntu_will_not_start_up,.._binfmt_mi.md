---
title: "Serious Help Ubuntu will not start up,.. binfmt_misc"
date: 2009-03-01
forum: General Help
---

### Post by shateredsoul on 2009-03-01
So I really messed up my machine.. at first the usb drives wouldn't work.  So I restarted it.. now it gets stuck on the load up screen with the following info.

*Enabling additional executable binary formats binfmt-support
FATAL: Module binfmt_misc not found.
update-finfmts: warning: Couldn't load the minfmt_misc module.

*Checking battery state...
/dev/sda
 setting Advanced Power Management level to 0xfe (254)

and that's all i see (plus some other stuff that started up before that)

Is there anyway to undo what I did?

this is what I did to mess my up my ubuntu :

> chmod 644 usbcore.ko
sudo cp usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot 

I downloaded a file called usbcore.ko from [http://www.scott-wallace.net/misc/usbcore.ko_2.6.27-7-generic_131072-mod.tar.gz]("http://www.scott-wallace.net/misc/usbcore.ko_2.6.27-7-generic_131072-mod.tar.gz") 

It restarted, the usb drives stopped working.  I tried "sudo depmod +ae" for some reason.. to see if I could undo what i did and it said something along the lines of "no such command".  I then restarted my machine and received the screen I described (all black, only white text)

I tried turning my computer off and on.. nothing.

before restarting I ran  dmesg |tail -n 20

this is what I received

[ 18.807523] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 19.457777] ACPI: WMI: Mapper loaded
[ 20.511358] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[ 20.586370] apm: BIOS not found.
[ 20.792407] ppdev: user-space parallel port driver
[ 24.308095] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 24.308107] vboxdrv: Successfully done.
[ 24.308112] vboxdrv: Found 1 processor cores.
[ 24.310940] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[ 24.310951] vboxdrv: Successfully loaded version 2.1.2 (interface 0x000a0009).
[ 30.627402] [drm] Initialized drm 1.1.0 20060810
[ 30.632783] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 30.632791] pci 0000:00:02.0: setting latency timer to 64
[ 30.633848] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 30.697317] NET: Registered protocol family 17
[ 58.440927] ieee80211_crypt: registered algorithm 'WEP'
[ 64.381049] NET: Registered protocol family 10
[ 64.382647] lo: Disabled Privacy Extensions
[ 64.384422] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 74.492026] eth1: no IPv6 routers present




---

### Post by shateredsoul on 2009-03-01
I somehow was able to access a screen that's pretty much the same thing as the terminal (except my whole screen looks like this).  Is there anyway to go back to the original kernel from this screen? Or to fix whatever I need to fix?

---

### Post by shateredsoul on 2009-03-01
I was able to log in by pressing escape, and choosing the 2.6.27-7 generic
instead of 2.6.27-11 generic.

I think if I replace the usbcore.ko everything will be fixed. Anyideas on how to do that?

---

### Post by shateredsoul on 2009-03-01
I'm running the following.. if this is absolutely the wrong thing to do let me know please.  I am new and don't now how to do anything about fixing anything.

=/

> sudo apt-get build-dep linux-source-2.6.27
sudo apt-get install linux-source-2.6.27 build-essential
tar -jxvf /usr/src/linux-source-2.6.27.tar.bz2
cd linux-source-2.6.27/drivers/usb/core
perl -pi.bak -e 's/16384/131072/' devio.c
make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
strip --strip-debug usbcore.ko
sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u

---

### Post by shateredsoul on 2009-03-01
now it says

Missingmodules (cat /pro/modules/esjls/dev

Alert! /dev/disk/by-uuid/ e90035b7-8120-4de9-b098-cc76c615ef7 does not exist.  Dropping to a shell.

*sigh*

can't anyone help?

---

### Post by shateredsoul on 2009-03-01
Okay, now I did this:

> sudo rm /boot/initrd.img-2.6.27-11-generic /boot/vmlinuz-2.6.27-11-generic
sudo apt-get purge linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic
sudo apt-get install linux-headers-2.6.27-11-generic linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic

Hopefully it works... be back on reboot

---

### Post by shateredsoul on 2009-03-01
Nope.. i'm still boooting with 2.6.27-7 generic. 

When I start up 2.6.27-11 generic it gives me 

[1010.100064] USB 3-1: device descriptor read/64, error -110

I thought virtual box might be the problem since it mentioned the vbox kernel.. so i opened virtual box.  It did not start. Told me something about kernel and to enter, "omar@laptop:~$ sudo /etc/init.d/vboxdrv setup"

I did so, and now virtual box works. Weird thing is that my usb drives are recognized through windows xp in virtual box but not in ubuntu.  So.. it probably is a problem with the usbcore kernel.  I wish I knew how to just replace the kernel for the usb.  Anyone?

---

### Post by shateredsoul on 2009-03-01
sudo /etc/init.d/vboxdrv setup

that fixed it.. it was the virtual box kernel that was messing things up

If that doesn't work try starting up virtual box, if it isn't working then it may be the problem

---

