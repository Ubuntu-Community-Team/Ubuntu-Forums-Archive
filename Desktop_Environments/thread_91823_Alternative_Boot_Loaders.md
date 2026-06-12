---
title: "Alternative Boot Loaders?"
date: 2005-11-18
forum: Desktop Environments
---

### Post by migo on 2005-11-18
I installed Ubuntu with LILO, but unlike the one included in RedHat 4.2, there's no option for multiboot with it, so I can't access my windows partition. The GRUB loader doesn't let me set it so Windows boots by default, which is why I decided to try LILO instead. What's a decent boot loader I could install instead that would let me set Windows as the default OS?

---

### Post by hanspb on 2005-11-18
You can get Grub to boot Windows by default. Just open /etc/grub/grub.conf and change the line 

default=0

to

default=x

where x is the entry for Windows. On my system it is 4. I have 3 different entries for Ubuntu, one separator and then Windows. Counting starts at 0.

Disclaimer:
This is taken out of memory, I am at work now, far away from my Ubuntu, so I can't check anything in detail.

---

### Post by abou on 2005-11-18
GRUB is the one you want to use.  As far as I know, LILO only boots Linux systems and not a Linux/Windows dual boot.

---

### Post by slux on 2005-11-18
[QUOTE=abou]GRUB is the one you want to use.  As far as I know, LILO only boots Linux systems and not a Linux/Windows dual boot.[/QUOTE]

Sure it does. Read up on lilo.conf if you want to set up dual boot using lilo. Grub is just the most preferred solution these days as it comes with some other benefits compared to Lilo.

---

### Post by hanspb on 2005-11-18
I tried Lilo once, but I never got it to work at all. With Grub I have never had a single problem, I am dual booting with Win XP.

---

### Post by migo on 2005-11-18
I tried the method hanspb posted, but grub doesn't excist in etc. Is there a search command?

---

### Post by colly3 on 2005-11-18
you can  edit the grub-loader with the sudo command in a terminal.

sudo gedit /boot/grub/menu.lst

and then change the default 0 to x (x=windows entry) to change the boot-priority.

---

### Post by migo on 2005-11-18
Thanks

---

