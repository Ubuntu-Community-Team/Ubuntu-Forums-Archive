---
title: "recompiling the kernel"
date: 2005-06-24
forum: Desktop Environments
---

### Post by glasscleaner on 2005-06-24
hello...

i try a shearch on the forum and found nothing interresting about HOW TO RECOMPILE THE KERNEL and/or any other informations about that.


can i find this somewhere?

thanks

---

### Post by intangible on 2005-06-24
May I ask why you want to compile a custom kernel?   Most of the time, there is no need to, I have only _had_ to for one computer in that last 3 years of using linux.

But here is a starter for you anyway: [http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)

Good Luck :D

---

### Post by VenomousGecko on 2005-06-24
Honestly the readme that you get from the kernel tarball at kernel.org is great.

It really isn't that hard as long as you know your hardware.  You must know what you have and then you can use either make menuconfig, make xconfig, etc to go in and customize your make file.  Then a make, make install, and then a minor adjustment to GRUB and you should be on your way.

Just be sure to leave your existing kernel image intact and do NOT remove its entry from GRUB.  Odds are you will have to work on it a bit before you get the hang of it and you will want to boot into the ubuntu stock kernel.

Hope that helped.

---

### Post by stray on 2005-06-25
How does this differ from an "apt-get dist-upgrade"?

---

### Post by Xian on 2005-06-25
[QUOTE=stray]How does this differ from an "apt-get dist-upgrade"?[/QUOTE]
This would provide you with a newer versioned _pre-compiled_ kernel if one was available. But they are talking about customizing what hardware support and so forth is in their kernel by configuring it manually and then compiling the code locally on their own machines.

---

