---
title: "Booting with GRUB from multiple xorg.conf files"
date: 2006-05-14
forum: Desktop Environments
---

### Post by slfd2525 on 2006-05-14
Ok, here's my dilemma..

I have one desktop pc, I use it at home and I take it to work with me as well so I can download updates and apps etc etc.  At work, my monitor does not support a high refresh rate, so I have to change the xorg.conf file.  Is it possible to have grub point to two xorg.conf files like xorg.conf.home and xorg.conf.work so I can have the more detailed monitor settings at home? Then I can just select work and home from grub...

Thanks in advance

---

### Post by Ramses de Norre on 2006-05-14
Grub doesn't pick your xorg.conf, X does.
Best solution seems to me to make the xorg.conf.work and the xorg.conf.home and make ubuntu boot without starting X.
Then you've got to copy one of them (the one you want to use for your session) to xorg.conf and start X after that.
You'll need to do this on every boot up..

---

### Post by catlett on 2006-05-14
Just a thought. Why don't you install xfce or kde alongside of gnome. Make (for an example) gnome be your "home" window manager with x set up like you want and then have xfce be your "work" window manager with it's x variation.. Then when you start up you can pick which session you want from the login screen.

---

