---
title: "The login messenger is gone! =("
date: 2006-09-22
forum: Desktop Environments
---

### Post by UltraSonicSite on 2006-09-22
Edit: Login **Manager**

I was just installing a city type game when synaptec tried to resume the failed installation of "Non-Free flash plugin" or something like that. The flash plugin did not install correctly so I ignored it, the game works fine. All of a sudden when I rebooted my computer, everything loads up perfectely! EXCEPT that all that comes out when done booting  is a console screen  (tty1) asking for a username and password. I'm currently using lynx. Btw, Startx comes out with a font type error or   something. Help pweeeeeease!!

---

### Post by UltraSonicSite on 2006-09-22
Any help?

---

### Post by Delkster on 2006-09-22
Seeing a copy of your X.org log file (/var/log/Xorg.0.log) might be helpful. If the X.org configuration has broken, though, you may be able to repair it at least to the extent of getting it usable again by running:
```
sudo dpkg-reconfigure xserver-xorg
```

Unless the fixed package (which has been made) is already available in the repositories, installation of flashplugin-nonfree will currently fail. You could also try to command "sudo apt-get --purge remove flashplugin-nonfree" or something like that to get rid of the (possibly) partially installed package for now until a fixed version is available.

---

### Post by UltraSonicSite on 2006-09-22
The x-server is fine, it's the login manager that's gone haywire. Whyyy ubuntuu?!

---

### Post by UltraSonicSite on 2006-09-22
> **UltraSonicSite said:**
> The x-server is fine, it's the login manager that's gone haywire. Whyyy ubuntuu?!
So how do I reinstall the login manager?

---

### Post by UltraSonicSite on 2006-09-22
Am I missing some information you guys need to know to help?

---

### Post by carlos1969 on 2006-09-22
so does your computer boot directly and bypasses the login manager?

can you go to system administration and see if you have the auto login manager box checked?


for me I always have it checked, I don't like having to do username and password everytime I boot up.

---

### Post by UltraSonicSite on 2006-09-23
no it never loads any sort of gui, just after the ubuntu boot screen is done a black screen with the text "Username: & Password:"

Which I assume is the console.

---

### Post by UltraSonicSite on 2006-09-23
Any help

---

