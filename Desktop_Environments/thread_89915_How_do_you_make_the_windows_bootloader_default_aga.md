---
title: "How do you make the windows bootloader default again?"
date: 2005-11-13
forum: Desktop Environments
---

### Post by bptba93 on 2005-11-13
I was wondering how to get rid of grub and go back to the windows bootloader?why? because i'm gonna try the new thing going around on the internet Mac OSX Tiger x86.

---

### Post by aysiu on 2005-11-13
[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

---

### Post by bptba93 on 2005-11-13
any program you suggest to do this?
or can you do this in linux?

---

### Post by aysiu on 2005-11-13
You can't give Windows back the boot loader from Linux using Linux.
You need a Windows recovery/installer CD.
See the link I gave for more details.

---

### Post by bptba93 on 2005-11-13
well i don't know how to install the recovery console because i don't have a windows xp cd just a toshiba recovery cd and please don't tell me i'll have to use it

---

### Post by Jonne on 2005-11-13
I think the same tools are available on the awesome win 98 boot diskette, which is the best piece of software to come out of Redmond in ages ;).

---

### Post by dbott67 on 2005-11-13
Do you want to get rid of Ubuntu as well or just use the Windows Bootloader to control the various installed OSes.

To remove grub from the MBR, boot from your XP CD and select 'R' (for repair) and then drop to a command prompt.  At the prompt, type **fixmbr** (or **fdisk /mbr**).

This will basically overwrite the Master Boot Record (and prevent you from getting into Ubuntu, unless you have grub installed on a floppy disk or bootable Cd, etc.

You may want to backup/printout your **/boot/grub/menu.lst** file before beginning.

-Dave

EDIT: oops... too slow typing again! :)

---

### Post by manicka on 2005-11-13
The recovery cd may have an option to boot into a recovery console

---

### Post by bptba93 on 2005-11-13
actually i found a xp cd i can use but it's a copy and it won't boot and i tried to install the recovery console and windows said i can't install it

---

### Post by bptba93 on 2005-11-13
the toshiba recovery doesn't have a recovery console option

---

### Post by Qrk on 2005-11-13
You might find more help on an XP forum.

---

### Post by dbott67 on 2005-11-13
Does your system have a floppy drive?  If so, make a bootable floppy disk in Windows XP (right-click A: drive in my computer & select 'Format' and check the "Make bootable" box).

Search your computer for a couple of programs (probably in C:\Windows or C:\Windows\System32):

- FDISK or
- FIXMBR

Copy those to the floppy disk.

Set your BIOS to boot from floppy and then run either one of the programs.

-Dave

---

### Post by bptba93 on 2005-11-13
no it's kind of a new laptop so it don't have a floppy lol
fixmbr is installed when recovery console is installed

---

### Post by bptba93 on 2005-11-13
fdisk won't let you reinstall the windows bootloader

---

### Post by Jonne on 2005-11-13
I don't think the windows bootloader can load Linux, btw. Can't you find any tutorials to make mac os X work with Grub?

---

### Post by bptba93 on 2005-11-13
can some one just post the fixmbr file?

---

### Post by bptba93 on 2005-11-13
i want to get rid of ubuntu along with grub

---

### Post by bptba93 on 2005-11-13
well i'm getting tired of not being able to do any of this stuff people are offering so i guess i'll just reinstall windows xp

---

### Post by aysiu on 2005-11-13
It sounds as if your best option, then, is to back up all your files and use the Toshiba recovery CD to reinstall Windows.

---

### Post by Jonne on 2005-11-13
you sure are impatient ;).

there are bootcd's available that might fix your problem.

(BART's PE bootcd, i think it's called)

---

### Post by bptba93 on 2005-11-13
i know i am. well here i go

---

### Post by bptba93 on 2005-11-13
well guess what happened it didn't work ubuntu and grub is still there!!!:mad:

---

### Post by Qrk on 2005-11-13
Reformat your whole disk first. You can use the Ubuntu Cd for that.

---

### Post by bvc on 2005-11-13
other info
[http://mandrivausers.org/index.php?showtopic=11887&hl=](http://mandrivausers.org/index.php?showtopic=11887&hl=)
[http://mandrivausers.org/index.php?showtopic=16804&hl=bootloader](http://mandrivausers.org/index.php?showtopic=16804&hl=bootloader)

---

