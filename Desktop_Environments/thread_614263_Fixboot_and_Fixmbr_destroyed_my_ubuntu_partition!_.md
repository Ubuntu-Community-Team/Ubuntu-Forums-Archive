---
title: "Fixboot and Fixmbr destroyed my ubuntu partition! HELP"
date: 2007-11-15
forum: Desktop Environments
---

### Post by reflexion on 2007-11-15
Hi,

My hard drive from my other computer was corrupted. So I putted in my Ubuntu pc to run chkdsk, fixboot and fixmbr (because I was not even able to load windows cd).

When I got it working, I was not able to reenter into my ubuntu partition (because the mbr was broken)

So I loaded the live cd and ran 
[INDENT]
grub
root /dev/sda1
setup /dev/sda1
etc
[/INDENT]

This solved my grub problem. But now, when I try to enter ubuntu, it hangs at the very beginning for about 8 minutes. Then, it goes into some kind of recovery console.

I tryed booting in recovery mode, but it hangs at this command:
[INDENT]
[28.308611]   sa 1:0:1:0 Attached scsi generic sg3 type 0[/INDENT]

It pauses for 8 minutes or so and then gives me:
[INDENT]
[INDENT][INDENT]Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev[/INDENT][/INDENT]
ALERT! /dev/disk/by-uuid/d5f6265c-a4cc-4369-aa51-6a78c59df8b7 does not exist Dropping to a shell!

BusyBox 1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)

(initramfs) [Flashing line for cmd][/INDENT]


Help please!!

---

### Post by Prospero2006 on 2007-11-16
In /boot/grub/menu.list, you'll see something like this:

root=uuid/d5f6265c-a4cc-4369-aa51-6a78c59df8b7

I think you can change it to root=/dev/sda

That might work. 
Pros

---

### Post by reflexion on 2007-11-16
I tryed to change it in the /boot/grub/menu.lst file.

I changed root=uuid/d5f6265c-a4cc-4369-aa51-6a78c59df8b7 -ro -something

to root=/dev/sda1 (I removed the -ro and other thing)


It still did not worked.

---

### Post by reflexion on 2007-11-16
SOLVED!

You were right, I needed to replace "uuid/d5f6265c-a4cc-4369-aa51-6a78c59df8b7" by /dev/sda1, but to KEEP -ro -etc


Thanks!

---

