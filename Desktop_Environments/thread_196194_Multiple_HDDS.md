---
title: "Multiple HDDS"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Vipersfate on 2006-06-13
I had no clue where this would go on the forums, but I have MS Windows on my 80GB WD and Ubuntu on my 40GB Seagate. They are both installed natively. Is there a program or a utility that can be accessed at startup to determine which os I want to boot into. Something that can be booted from a USB? I want to keep the drives both up for file transfers. Thanks in Advance

---

### Post by mlind on 2006-06-13
That's what GRUB bootloader and LILO are for. Ubuntu uses GRUB for default.
I guess you can install it on USB drive too.

You should have GRUB installed, if you didn't somehow discard it while 
installing Ubuntu. It could be hidden by default, so you need to press ESC
when your computer is booting and past RAM count.

Adding other operating systems, like Windows on GRUB boot menu is a
trivial task.

---

### Post by Vipersfate on 2006-06-13
I knwo those items, i'm just wondering if they can be used off a USB Drive. to the google! Thanks for giving me the idea of doing that!

---

### Post by Vipersfate on 2006-06-13
how would I go about installing grub on a usb drive? Im currently in Ubuntu, and it recognizes the flash drive.

---

### Post by mlind on 2006-06-13
[QUOTE=Vipersfate]how would I go about installing grub on a usb drive? Im currently in Ubuntu, and it recognizes the flash drive.[/QUOTE]

This could help [http://www.freesoftwaremagazine.com/articles/grub_intro/](http://www.freesoftwaremagazine.com/articles/grub_intro/)

---

### Post by Vipersfate on 2006-06-13
That seems like it would work, but I'm nowhere near that level of competency with Linux thanks anyway

---

### Post by mlind on 2006-06-13
[QUOTE=Vipersfate]That seems like it would work, but I'm nowhere near that level of competency with Linux thanks anyway[/QUOTE]

Yeah, looks bit complicated. How about **grub-floppy** script ? Does it work on USB
device like it does with floppies?

---

### Post by Vipersfate on 2006-06-14
I will try that tomorrow when I get off work and post results on it. Thanks!

---

