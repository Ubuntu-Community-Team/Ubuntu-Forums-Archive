---
title: "Ubuntu startup hangs at grub prompt"
date: 2009-03-13
forum: General Help
---

### Post by freewheelinguy on 2009-03-13
I have a duel boot system "(winXP,Ubuntu) and windows boots fine.  When I try to boot ubuntu it stops at the grub prompt.  I have no idea what to enter in order to proceed.  I did try some commands but that just gets me back to the OS choice menu.
Any help would be greatly appreciated.  I have been using Ubuntu 8.1 for several months now.  This problem orginated yesterday when system was froze and had to unplug laptop to get it to start back up.  

Len

---

### Post by taurus on 2009-03-13
Did you install Ubuntu through wubi?

---

### Post by freewheelinguy on 2009-03-13
yes, I have the program on a cd or dvd.

---

### Post by taurus on 2009-03-13
> 
[SIZE="4"][COLOR="SandyBrown"]Any gotcha?[/COLOR][/SIZE]

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by freewheelinguy on 2009-03-13
Thanks for responding, but does this mean I am SOL or is there something I can do other than re-installing?

Len

---

