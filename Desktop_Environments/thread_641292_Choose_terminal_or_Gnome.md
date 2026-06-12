---
title: "Choose terminal or Gnome"
date: 2007-12-15
forum: Desktop Environments
---

### Post by cazz on 2007-12-15
Hi

Is it possible to choose if I like to run in terminal or run GNOME when I start my computer?

Like a menu that I can pick if I want to run terminal or GNOME.

---

### Post by jken146 on 2007-12-15
I think there might be somethin in the Sessions options before you log in that does that.  I don't see why you'd need it though, as you can Ctrl+Alt+F1 to F6 (F7 brings back the X session).

---

### Post by banewman on 2007-12-15
At boot time there is an option for "recovery" that is command line only. :)

---

### Post by Xbehave on 2007-12-15
> **banewman said:**
> At boot time there is an option for "recovery" that is command line only. :)
woooh! recovery launches single mode which logs you in as root, this is NOT the way to get to a terminal. 
single mode is a security hole which means a default ubuntu install is less secure than windows to local attacks (not a problem as it takes 2 lines in grub to fix and leaving it on by default would cause to many problems)

there is a menu at the login screen (well in kdm anyway i assume gdm is similar)
best way of doing it IMHO tho is to always boot to terminal then typing startx (this avoids the laoding time of GDM)

---

### Post by cazz on 2007-12-15
Thanks :)

---

### Post by camcorderdoctor on 2007-12-15
I There Command To Go From Command Line To Desktop Mode - If So What Is It?

---

### Post by Digital Ninja on 2007-12-15
> **Xbehave said:**
> 
single mode is a security hole which means a default ubuntu install is less secure than windows to local attacks (not a problem as it takes 2 lines in grub to fix and leaving it on by default would cause to many problems)

And what do those two lines look like?

---

### Post by Xbehave on 2007-12-15
the command to go from command line to desktop is startx

to secure your system youd be best of reading around, just opening up /boot/grub/menu.lst will give you the basics
> ## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editi$
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password <password or md5 of it here>

then either (edit lines as this is automagic stuff so adding them will just break stuff)
> # lockalternative=true
or
> # alternative=false

this means to boot to your recoverymode you/your attacker need a password
*note getting/changing the password can be done by anylive cd (so you may want to lock your boot order)
**reseting bios can usually be done physically so you may wish to encrypt your root partition

***you may not be paraniod so simply setting your password puts you on par with a windows system

---

