---
title: "My screen goes black when I log out."
date: 2009-02-26
forum: General Help
---

### Post by Jlb181 on 2009-02-26
Here's what I've done.  I installed Ubuntu 8.10 (and all current updates) onto a 250 GB USB hard drive so I can use it at work.  I've been using the flash drive but I need more space.  Anyway. . . it went like this.  I could boot up to the log in screen, enter name and password then the computer would hang.  After a few minutes of searching I found a fix.  I added "vesa" to the xorg.conf.  Now I can log on and use the system.  However, I created a few more accounts and when I logged off my account the screen went black.  Now I am stuck.  Any buddy familiar with this?  The system is still running, I just can't see anything.  I don't know any information for the computer at work, it's an HP with a pentium celeron CPU, maybe 512 MB RAM and a 40 GB hard drive.  

After the screen goes black, I hit the power button and the system shuts down, apparently properly.  I had this same problem with the flash drive but I didn't worry about it because it wasn't big enough for multiple users.

---

### Post by ddrichardson on 2009-02-27
Can you use virtual terminals (ctrl-alt-f2)? HP often also need noapic added to the grub boot line too - there ACPI implementation is a bit of a hack.

---

### Post by Jlb181 on 2009-03-02
> **ddrichardson said:**
> Can you use virtual terminals (ctrl-alt-f2)? HP often also need noapic added to the grub boot line too - there ACPI implementation is a bit of a hack.


Thanks I will try this!

---

### Post by Jlb181 on 2009-03-05
Everything is working -sometimes- I can log in and out of accounts then suddenly it will stop working.  If I use ctrl-alt-F2 I can get to a prompt so the system is still working, I just loose my graphics.  Now it is only accasionally.  Used to be always.  So I am thinking the noacpi worked, but I am wondering if there is a certain place in the command line it should be.  Suggestions?

Thanks
Jeff

---

### Post by ddrichardson on 2009-03-05
The noapic option should be at the end of your kernel line in /boot/menu/grub.lst

---

