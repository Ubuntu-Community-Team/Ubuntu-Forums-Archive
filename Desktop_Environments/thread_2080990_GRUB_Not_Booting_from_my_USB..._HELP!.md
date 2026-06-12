---
title: "GRUB Not Booting from my USB... HELP!"
date: 2012-11-05
forum: Desktop Environments
---

### Post by nenanen on 2012-11-05
Hi Geeks  

A linux newbie here.

I´ve installed Ubuntu alongside with Windows in my PC.

All OK here. I like Linux vs Windows, but I still need Windows to test some programs.


The problem is, now I cannot boot from USB or CD:


I've created a bootable USB drive from Windows with no apparent problems. 

When I set in the BIOS to boot from the USB, that part at least goes normally, but then I'm shown a grub> command prompt. 

Trying the command "boot", I get Error 8: Kernel must be loaded before booting. So, how do I continue from there?

Why this does not works normally like before installing Ubuntu in my PC?

This has happens when using a LiveCD (a bootable CD) and botting from the CD drive.

What is needed to launch the install process from the grub prompt?

Or... can I uninstall Grub 2 altogether and go just with the Windows Bootloader as before?


Thanks a lot in advance  :)

---

### Post by gordintoronto on 2012-11-05
Is this a new computer? UEFI or BIOS? Do you know if the hard drive is GPT or MBR?

I'm surprised a user named oldfred has not asked you for information. He seems to be the master of booting issues.

---

### Post by Kevin McCready on 2013-01-11
I have the same problem. I created a bootable usb disk on Microsoft Windows using Unetbootin. Then when I booted into an old old computer it seemed to boot the kernel from the USB stick but boot the operating system from the hard drive. It looked for the command from the GRUB file on the hard drive and booted that.

I guess I need to know how to alter the grub file on the hard drive to boot the operating system from the USB stick.

---

### Post by gordintoronto on 2013-01-11
I think you need to change your BIOS settings to boot from the USB.

If you run Linux from the hard drive, and plug in the USB stick, I think you can run the command: sudo update-grub
and it will add the USB drive as an option. But I could be wrong.

---

