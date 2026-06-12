---
title: "Using GRUB to install Ubuntu/Windows/etc from USB"
date: 2009-02-08
forum: General Help
---

### Post by yeaitsdark on 2009-02-08
Hey all I thought I would hit you up and ask you if you can offer me any advice to this issue I am having.

Firstly, my goal is really to have a sort of "master" install USB key just to make my life easier.

I'm just really unsure as to how to proceed. For the past few days I've been trying to do it with GRUB. Mainly because it's the only boot loader I know anything about. Also, I like that I can reconfigure parameters on boot or simply edit them at any point in the menu.lst.

One guy wrote a good piece, that I've been using as a guideline:
[http://www.askapache.com/security/install-multiple-os-without-cds.html](http://www.askapache.com/security/install-multiple-os-without-cds.html)

However not exactly what my main goal is, I'd love to have it boot into a menu like "Install Ubuntu, x86 Install Ubuntu x86-64, Install Windows Vista" Afterward, it would boot the live cd for Ubuntu, or the Vista installer, etc.

At this point with all my reading I could so easily run all these systems FROM the usb lol, but I just want a nice dynamic install usb so that when a new release comes out from Ubuntu or Gentoo etc etc I can simply change the files on the key and move on.

I have found in my searching a lot of tools for specific distros, including Ubuntu (which is btw awesome) but just being as I'm constantly reinstalling OS's on friends machines, or my own. The CD's get worn or lost etc, whereas my USB key fits in my pocket :)

If I didn't have to include Windows in my list of desired OS's I could just make myself some nice "clean install" images and just dump them to the hard disks, but you know how windows is about being moved around. So fresh install is generally a must there.

Thanks in advance. When it comes to this level of configuration, I'm no expert and I know I am surely missing some "simple" bit of information.

---

### Post by zwygart on 2009-02-10
I don't very understand what you want. To install ubuntu from LiveUSB, only click on the icon. To upgrade you need only to copy the content of the ISO in the partition where the old ubuntu is (after deleting it). Edit your menu.lst according to what is written in isolinux.cfg. 

I also tried to boot others distro where most ended with kernel panic. I don't know what I done wrong (even when I use root=/dev/sdXY as kernel option). How do you install gentoo on drive? Copy from a installed one (cross compiling)?

To simplifie loading of some distro, install syslinux on the primar partition of the distro (not the MBR). 

I installed Ubuntu from my USB many times. 
Perhaps you want to edit the init files, wich is depending on the ISO's. 
You may also boot a OS, then a virtual machine wich boot a iso that you want to install (advanced). 
It depends on the distro/OS. 
Keep on and reply.

---

### Post by yeaitsdark on 2009-02-11
Thank you for your reply. To clarify, I just want to be able to install different operating systems from the USB.

I have been successful with syslinux and booting the Ubuntu Live CD using these kernel parameters.

```

LABEL Ubuntu-x86
  menu label ^Boot Ubuntu 8.10 x86 Live Installer
  kernel /ubuntu86/casper/vmlinuz
  append ro root=/dev/sda1 file=/ubuntu86/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/ubuntu86/casper/initrd.gz quiet splash --

```

Under GRUB I can get it to work with:
```

title Ubuntu x86 Setup
kernel /ubuntu86/casper/vmlinuz
append  boot=casper integrity-check initrd=/ubuntu86/casper/initrd.gz root=/dev/ram0 rw quiet splash --

```
I have also been successful in booting Windows Vista setup by creating a dedicated partition for the Vista setup files and running: (in grub, perhaps similiar in syslinux)

```

title Vista x86_64 Setup
rootnoverify (hd0,3)
chainloader /bootmgr

```

I also have the same issue you described with some kernels:
> **zwygart said:**
> 
I also tried to boot others distro where most ended with kernel panic. I don't know what I done wrong (even when I use root=/dev/sdXY as kernel option).

I am making progress slowly. In part due to the fact I can only test "so much" running a virtual machine.

On a side note, syslinux has no problem "chaining" over to grub4dos with option:
```

LABEL GRUB
  menu label ^Boot Grub
  kernel /boot/grub/grub.exe

```

This has greatly helped me because I can change options very easily at boot time and test with grub or syslinux. I hope that helps you understand what I am doing.

Let me know what you think.

---

### Post by zwygart on 2009-02-11
I would made a multiboot USB key. Did you have done it?
Then you can install from the running OS.
Also many OS only copies files on a drive. So may be this will help you to run a script to copy files. This may be run from a minimal Linux. 

Personnally I don't use append in GRUB. 

Go a head, you will be able. I am trying arch now. I don't worked a lot with VM.

I have multiboot on my key : Puppy400, ubuntu 8.10 LiveCD, SuperGrub, UBCD, will readd SystemRescueCD and may be others. 

Only add the entries to menu.lst.

```

title live
root (hd0,5)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper
initrd /casper/initrd.gz quiet splash --

title live-install
root (hd0,5)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity
initrd /casper/initrd.gz quiet splash --

title check
root (hd0,5)
kernel /casper/vmlinuz boot=casper integrity-check 
initrd /casper/initrd.gz quiet splash --
```

---

### Post by yeaitsdark on 2009-02-11
I am using a USB drive, it makes it a lot easier to change things on the fly. 

Do you think it's necessary to create a separate partition for each "install"?

Not that it's a BIG big deal, but it would be nice to just use a /disto type directory for the most part.

I only ask because I have been able to do it just by adding the directory to menu.lst

i.e /ubuntu86/casper....

In other words, does it have any negative effect to doing it this way or is it really just better to use separate partitions?

---

### Post by zwygart on 2009-02-12
The problem with multi OS on same partition is file conflicts. I have mentionned systemRescueCD and UBCD on same partition. I could add also puppy. 

The problem appears when 2 OS uses the same path/filename without the same content. Like Ubuntu and xubuntu, I think. Normally if put 2 os not based on same OS they wouldn't have a lot of files in common. These is the major reason. 

Note that you don't need to put the entire OS in a partition. I mean you don't need syslinux and isolinux files since you putted them in GRUB. Also the kernel could have any name because you write it in GRUB. But if you have to OS with casper, or var directories, things can be wired.

You putted the content of the ISO in a directory? Interesting. What about if the OS wanted to access it's root? Did it not search at the root of the filesystem?

---

### Post by yeaitsdark on 2009-02-15
Sorry for the late reply. Yes I was booting ubuntu where all the "live" files were in /ubuntu but grub was still in /boot/grub. Then I had say /gentoo etc.

It didn't seem to have that much a problem with it. I only wonder if there's really a way to get grub to tell the kernel it's root is a directory and not a partition.

Like:
root (hd0,1) /ubuntu

Not sure how to set it up that way, I was reading the grub documentation and haven't yet figured it out correctly.

---

### Post by zwygart on 2009-02-16
If you want to change root, this may be very hard. I want to be able to change root to ram, like puppy, but my OS (ex. arch). 

You have to difference tree roots. Perhaps I'm wrong because I'm new to these things too.
The root of grub, the root of the kernel and the root of the OS.

The root of grub is designed as you said : root (hdX,Y). That is where grub search for the files (menu.lst, kernel, etc), except if you give a absolute path. It is used to load the kernel.

The root of the kernel is where the kernel search for the init. and initramfs or initrd. It is used to load the OS. This root is defined as a option root=/dev/sdXY for the kernel (grub>kernel /vmlinuz root=/dev/sda1)

The root of the OS is defined in /etc/fstab. That is where all the files will go and come from during running of the OS. That is where should be directories like etc,usr,var,proc,dev,home.

I hope this will give some glues.

---

### Post by yeaitsdark on 2009-06-21
I have since realized the problem is actually with how Windows loads. It's extremely annoying, but it's not like I really blame them. It's complicated to explain, but on the bootloader side it's actually really easy you just load the Windows PE (2.0 etc) image via memdisk and you're kinda good to go. 

The annoying part is getting the Windows PE image and such made and working in the first place. Then it all has to be formatted properly because of the way the system itself works.

At any rate, I've since gotten everything working on a PXE server, and the implementation would be very similar if being used on a USB stick. In short, you would need syslinux on the stick, WindowsPE from Microsoft's site, and a /Boot folder on the stick where you keep all the windows stuff. 

If anyone cares about this type of implementation, post and I'll go into more detail.

---

