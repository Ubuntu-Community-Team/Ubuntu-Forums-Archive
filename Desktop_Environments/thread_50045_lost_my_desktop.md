---
title: "lost my desktop"
date: 2005-07-18
forum: Desktop Environments
---

### Post by Dummies102 on 2005-07-18
Hello, I have an odd problem that I unfortunatly don't know how to solve. I was in the process of upgrading my monitor when I accidently unplugged the computer. After I got everything plugged back in, I started the computer and the graphical desktop would not start. I don't get any X errors, it just boots directly to a text based logon.

I thought the monitor might have prevented x from loading so I edited /etc/X11/xorg.conf to match my new settings, but I still can't boot up.

I've been using gnome, and I don't know what other relavent information I can give. Thanks for any help.

---

### Post by mad_scientist03 on 2005-07-18
[QUOTE=Dummies102]After I got everything plugged back in, I started the computer and the graphical desktop would not start. I don't get any X errors, it just boots directly to a text based logon.[/QUOTE]

The first thing I would do is login, and at the terminal type "startx". If the X server is broken, then you will asked to look at "/var/log/Xorg.0.log" for more details. To reconfigure your X server with the new monitor, you can type "dpkg-reconfigure xserver-xorg". You can most likely just accept the defaults as they're given to you. At the end, if the X server does not start automatically, you can again type "startx". I would imagine you will get a graphical display of some sort, and the rest is tweaking the "/etc/X11/xorg.conf" file to get things exactly as you'd like them, if you're picky.

---

### Post by jesse on 2005-07-18
Have you tried entering your user name and password to log in and then typing "startx"?

If that gets you into x you may then need to reinstall gdm.

---

