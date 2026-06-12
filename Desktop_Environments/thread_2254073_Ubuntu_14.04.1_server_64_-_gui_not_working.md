---
title: "Ubuntu 14.04.1 server 64 - gui not working"
date: 2014-11-24
forum: Desktop Environments
---

### Post by am.julash on 2014-11-24
Hi, I have ubuntu 14.04.1 (64bit) server on iwStack cloud.

I have installed gui but when I try to start gui using 'startx' gui dont work and showing fatal error: 'no screens found' after 'Loading extension GLX' line. I have attached image. I have searched online but did not found anything that might help me.

Please help me about what I am doing wrong.

The gui I installed is minimal gnome core desktop: [COLOR=#000000][FONT=Consolas]sudo apt-get install xorg gnome-core gnome-system-tools gnome-app-install[/FONT][/COLOR]

Thanks
Julash

[ATTACH=CONFIG]258186[/ATTACH]

---

### Post by ibjsb4 on 2014-11-25
I have not ran this configuration, but looks doable to me.  Also looks like a display manager was installed (gdm).  So makes me wonder why it didn't boot to GUI login.  Try pointing startx to the desktop.

[https://wiki.archlinux.org/index.php/xinitrc#Override_xinitrc_from_command_line](https://wiki.archlinux.org/index.php/xinitrc#Override_xinitrc_from_command_line)

---

### Post by Dragonbite on 2014-11-25
This is something I am thinking of setting up my server with, so I have to type 'startx' to start a Gui.

Could it be related to the init runlevel? Not sure what it is actually called, but I know there are different run levels and only some of them enable running a GUI while others are text-only.  Does this make sense or ring any bells?

---

### Post by ibjsb4 on 2014-11-25
@ Dragonbite

Your post made me wonder if 'nomodeset' is needed.  I have not needed to use it, but I wonder if it could apply.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

