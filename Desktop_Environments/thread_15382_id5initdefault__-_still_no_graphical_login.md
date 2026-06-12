---
title: "id:5:initdefault:  - still no graphical login??"
date: 2005-02-14
forum: Desktop Environments
---

### Post by F Cocquyt on 2005-02-14
Hi,

I've recently had to reinstall my gnome packages. I removed them by accident while playing around with apt-get (yes, I'am a linux newbie  ](*,) ). I 've managed to re-install them all but now I don't have a graphical login. I already changed my default line in /etc/inittab file to id:5:initdefault: but it still won't boot to a graphical login interface. When i logon on the CLI I can get the graphical environment working with the startx command, but what do I have to change to make this permanent?

Regards,
F.

---

### Post by F Cocquyt on 2005-02-14
I've found it.  \\:D/  
After messing around with .xinitrc and different inittab values nothing changed.
I discovered that gdm (GNOME display manager) wasn't installed ](*,) . After installing gdm problem was solved.  As I said before, I am a Linux newbie.

---

