---
title: "GRUB trouble"
date: 2009-03-24
forum: General Help
---

### Post by lariosa42 on 2009-03-24
Hello all,

I just received a handy-me down computer from a fellow student who just graduated (they moved, and I don't have any contact information).  Before the gave it to me, they wiped their files off it but left an install of Ubuntu 7.04 on it.  I don't know the password, so I can't log in.  I tried bootup off the 8.04 live CD, but it doesn't seem to recognize it.  Next, I tried rebooting and hitting ESC when the GRUB loader came up.  I was able to choose "recovery mode," but I get the message
```

Give root password for maintenance
(Or type Control-D to continue)

```
If I type Control-D, it goes to the Ubuntu login screen, which is not helpful, since I don't have the password.  If I just hit enter, it asks me for the root password again.  (From looking around on the forums, it seems GRUB might be password protected, but I haven't found a good way to fix this.)

I'm not sure what to do not.  I would be happy to just completely wipe the drive and put a fresh version of Ubuntu on it, but I don't know how to do that.  Any help would be appreciated!  =)

---

### Post by lariosa42 on 2009-03-24
A quick update:

I tried booting of a USB drive (thanks Ubunutu 8.10!), but still no luck.  It doesn't seem to recognize the USB drive.

---

### Post by louieb on 2009-03-24
Haven't seen Ubuntu ask for a password when booting into recovery mode. Are you sure its Ubuntu. 

Anyway What are the specs of the computer?
 Sounds like your best bet is a fresh install. Exactly what happens when you tried to boot the 8.04 live CD. 
Heres some hints on how to get the cd to boot_. _[BootFromCD - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BootFromCD")

---

### Post by lariosa42 on 2009-03-24
Hello,

Thanks for the reply.  Yes, I'm sure it is Ubuntu.  

Based off the link you sent, I was able to get into the BIOS setup menu, but it also requires in order to edit anything.  The "Boot off CD" option is not enabled, so this is most likely why it is not recognizing the Live CD (similar problem for the USB drive).  

I don't know much about the computer, as it was a hand-me-down.  From what I can tell (from the BIOS menu) it's a Dell Precision 330 (BIOS version A08), running a Pentium 4, 1.70 GHz.

This is interesting:  It says the "System Password" is not enabled and the "Password Status" is unlocked, but that the "Setup Password" is enabled.

---

### Post by louieb on 2009-03-24
Looks like you got a little research ahead of you. I googled it - looks like it should run Ubuntu nicely. 
Also did a Google search on **Dell Precision 330 reset setup password ** 
Found links to the user guide and the technical manual. 

Did not look close but usually to clear the setup password you can remove the CMOS battery or switch a jumper on the mother board. Should be something in the technical guide to show what to do.  Just looked a little closer it looks like the board has a password jumper. 
[http://support.dell.com/support/edocs/systems/ws330/en/sm/sysbrdcm.htm](http://support.dell.com/support/edocs/systems/ws330/en/sm/sysbrdcm.htm)

---

