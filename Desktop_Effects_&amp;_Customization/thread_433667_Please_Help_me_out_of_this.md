---
title: "Please Help me out of this"
date: 2007-05-05
forum: Desktop Effects &amp; Customization
---

### Post by san2004 on 2007-05-05
Hi Guys, 
I installed fiesty on an old PC yesterday (256 MB RAM). Installation was smooth. The machine rebooted and everything was fine.  Then I tried to enable the desktop effects. Immediately the screen went white with no panels. I tried rebooting but it did not help. GDM is not working anymore. Now I can enter through recovery mode only.
Can anyone help to disable the desktop effects iwthoue reinstalling again.

Thanks in advance.

Sanjoy

---

### Post by Fireblend on 2007-05-05
Did you checked startup commands?

---

### Post by joiningtheherd on 2007-05-05
First, did this happen after enabling a flag or setting from within already installed software, or after installing *new* software?  If it was after *new* software I'd use the debian package manager ap-get or aptitude to uninstall it.  I'm a Gentoo user, who has decided on Ubuntu for the family, and my laptops (save on compile time) so I'm not to familiar with all of the Ubuntu/Debian bells and whistles yet, but try:

```

sudo aptitude purge package_you_installed

```

where package_you_installed is the new software packages separated by spaces.
failing that we'll talk about what you enabled ... and how exactly you produced this error. worse comes to worse you take half an hour and reinstall, and you've learned a valuable lesson about backing up the important files like ```
/etc/X11/xorg.conf
```. ;-)

If it can be done ... it can be undone.

---

### Post by dentaku65 on 2007-05-05
try

```
sudo apt-get remove desktop-effects
```

and reboot the machine

---

### Post by san2004 on 2007-05-06
Thanks a lot guys.

> **dentaku65 said:**
> try

```
sudo apt-get remove desktop-effects
```

and reboot the machine

This did the trick.

Thanks again.
Sanjoy

---

