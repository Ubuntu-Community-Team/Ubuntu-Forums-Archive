---
title: "x server &amp; nVidia drivers"
date: 2009-03-21
forum: General Help
---

### Post by Beyecixramd on 2009-03-21
hello, i just tried to install the latest drivers for my graphic card *[http://www.nvidia.com/object/unix.html*](http://www.nvidia.com/object/unix.html*) , the 180.29 version.

well, i managed to kill the X server, and install it in the tty1 console.

when i restarted, i saw the ubuntu low graphics mode dialog. I choose create new configuration, then i restarted.

when it booted, i had the same problem as in the Live CD without the safe graphics mode enabled> the screen turns black, and i can hear the gdm ready sound, but i cant do anything in the x server, of course, the ttys are still working.

then, seeing it wasnt working, i tried to install the drivers via EnvyNG, the same way i did the first time i installed linux mint. So i choose the previous driver in which the X server was running perfectly.

then again, the ubuntu low graphics mode dialog appeared, this time i choose run in low graphics mode. it says to wait 1 minute, i wait but nothing happens, and the X server seems to be frozen, so i restart via tty

after all this, i get tired and i try to get the error logs, i uploaded them with mintUpload in the LiveCD im currently typing this, [http://files.mint-space.com/getfile,20090321225311,error.tar.html](http://files.mint-space.com/getfile,20090321225311,error.tar.html)

now what...? thanks  [IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

---

### Post by Nano_ext3 on 2009-03-21
See my blog on [Using EnvyNG]("http://thelinuxcauldron.wordpress.com/2009/03/17/how-to-session-installing-your-nvidia-or-ati-card/")

Cheers!

_Nano

---

### Post by Beyecixramd on 2009-03-22
thank you for the reply, the problem is i cant install the nvidia driver via envyNG... well, i can install it, the problem is the x server runs in low graphics mode... i tried to uninstall it, and reinstall the latest version, not working....

---

