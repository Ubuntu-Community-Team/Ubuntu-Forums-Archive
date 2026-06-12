---
title: "Dell Inspiron 910 (Mini 9) GRUB Menu Access"
date: 2009-04-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by novafluxx on 2009-04-02
I was trying to support a person this evening, and her daughter had forgotten her password, and could not perform any administrative functions (they were trying to use update manager). I am under the impressions that the Mini 9 has a restore partition, and can be accessed through the GRUB menu.

The issue is this: Dell appears to set the GRUB timeout to 0 by default, and the person was unable to access it in order to perform the factory image restore.

This system is a netbook, and does not have an optical drive. After working with this person for an hour, I ended up asking her to purchase a 4GB+ flash drive, so we can download the iso image from Dell's Linux wiki, and perform a reinstall that way.

Any suggestions? She cannot edit the config file due to, you guessed it, not having root access/password. How does one access the GRUB menu if the timeout is set to zero seconds?

---

### Post by mocoloco on 2009-04-02
All I can think of is if you can boot from an external device like a USB drive or exteral optical drive you can use a Live distro and get to a prompt to fix grub.

This is one of a few annoyances I have with what Dell has done on it's Ubuntu machines (wife just got a mini 12).  Why would they do that?

---

### Post by novafluxx on 2009-04-02
They do it, to prevent the user from accessing it and messing it up by editing the options and making the system unbootable.

In my capacity to help her, I cannot have her use a LiveCD. I can recommend it, but she wouldn't have understood, and I couldn't have walked her through it. Hope you understand my limitations. ;)

---

### Post by anjilslaire on 2009-04-02
The Mini 9 comes with a restore DVD with the Dell version of 8.04. You should be able to use that to restore th system by loading it onto a usb flash drive. 
Of course, editing the Grub may be about as difficult to walk a person through as doing a restore via usb if you're not on location.

---

### Post by mocoloco on 2009-04-02
Yes but the restore DVD only has one option, wipe the whole machine and start fresh.  Not cool.  Maybe contact Dell and see if they have a solution in mind?  You could poke around in their forums but I've found them to be pretty cruddy.

---

### Post by novafluxx on 2009-04-02
> **mocoloco said:**
> Yes but the restore DVD only has one option, wipe the whole machine and start fresh.  Not cool.  Maybe contact Dell and see if they have a solution in mind?  You could poke around in their forums but I've found them to be pretty cruddy.

Her system did NOT come with an optical drive, nor did it come with the Ubuntu reinstallation disc (or they've lost it)

Contacting Dell won't help, I know this for a fact.

---

### Post by anjilslaire on 2009-04-02
All Mini 9's preloaded with Ubuntu come with a Dell restore disc even though the system has no optical drive, so it must have been lost.

A lot of people here have loaded regular 8.10 on it instead. It works great.

---

### Post by ugm6hr on 2009-04-03
I have heard that if you just press Escape repeatedly just after the Dell logo opening screen, you can enter the GRUB menu (with a bit of luck).  It does have a recovery / root login option (the same as regular ubuntu).

Obviously, the 0 timeout is a bit ridiculous (i have changed mine), but it is not strictly 0 seconds, according to other reports from users here.

---

### Post by novafluxx on 2009-04-03
Thanks! I'm just going to have her reinstall from the iso available at linux.dell.com wiki.

I appreciate the help, I'll recommend she set it to 2 or 3 seconds after the reinstall, just so if she needs to access it in the future for any reason.

---

### Post by brianchidester on 2009-04-03
The Dell Mini 9 does not have a recovery partition because of the option to ship with a 4 GB ssd.

---

### Post by jeffbmartinez on 2009-04-12
My girlfriend forgot her password... found a working non-reinstall solution here:

[http://blogs.gnome.org/mneptok/2008/11/11/reset-your-password-with-recovery-mode-on-the-dell-mini-9-netbook/](http://blogs.gnome.org/mneptok/2008/11/11/reset-your-password-with-recovery-mode-on-the-dell-mini-9-netbook/)

Basically you *can* access grub even with a 0 second timeout, it just takes a few tries to get the timing right.

Good luck!

---

