---
title: "Screen Resolution"
date: 2007-05-03
forum: Desktop Environments
---

### Post by TFildes on 2007-05-03
I ran this in (sudo dpkg-reconfigure -phigh xserver-xorg) termianal and added 1280x1024 which my monitor supports but now on a reboot all I get is a Fatal Error and a black screen at my desktop. How do I get back to Ubuntu splash screen????

---

### Post by dcstar on 2007-05-03
> **TFildes said:**
> I ran this in (sudo dpkg-reconfigure -phigh xserver-xorg) termianal and added 1280x1024 which my monitor supports but now on a reboot all I get is a Fatal Error and a black screen at my desktop. How do I get back to Ubuntu splash screen????

CTRL-ALT-F1, log in and then:
```
cd /etc/X11
ls xorg*
sudo mv xorg.conf xorg.conf.save
sudo cp** xorg.conf.whatever-date-is-most-recent** xorg.conf
sudo /etc/init.d/gdm restart
```
You will have to find the xorg.conf that was saved (your previous working one) when they are listed by the ls command.

---

