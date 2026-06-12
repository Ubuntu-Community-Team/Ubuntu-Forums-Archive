---
title: "Modifying gnome-shell look and behavior"
date: 2013-11-04
forum: Desktop Environments
---

### Post by Jeffrey Martin on 2013-11-04
Hello all,

I'm using my own custom install of Ubuntu, this is the mini.iso on which i've installed only the packages i want. There's nothing from Unity installed, just gnome-shell for the DE.

I want to know what would be the best way to start learning how to adapt the look and behavior of the gnome-shell. I assume theming only allows you to change the look and that changes in the behavior or location of panels would have to be made in extensions?

I know there's more DE to use but it seems to make the most sense to use the ones where the most development effort is focused on, so this would be gnome-shell or unity i guess. I like gnome-shell, i just want to tweak the look and behavior to do what i want.

Jeff

---

### Post by BrunoLotse on 2013-11-04
Hi, Jeff:How about GNOME Shell Extensions? [https://extensions.gnome.org/](https://extensions.gnome.org/)I am using them extensively to customize L&F of my GNOME Shell. I would also suggest gnome-tweak-tool.Cheers,Bruno

---

### Post by deadflowr on 2013-11-04
Gnome extensions is definitely where to look for some added functionallty.

If you like to mess around with scripts look in 
/usr/share/gnome-shell

There are a few js files in the /usr/share/gnome-shell/js/ui folder you can muck about with, if you feel lucky.

Then there is the file in /usr/share/gnome-shell/theme/gnome-shell.css
which you can add or subtract various settings.
Most useful of them changing the panel outlook, such as making it transparent, or adding color, which ever you prefer.

---

### Post by Frogs Hair on 2013-11-04
This is an all purpose customizable Gnome Shell theme . I have never even used all the options yet.  

[http://www.webupd8.org/2013/06/highly-configurable-elegance-colors.html](http://www.webupd8.org/2013/06/highly-configurable-elegance-colors.html)

---

### Post by Jeffrey Martin on 2013-11-04
Thank you all so far, i am looking for the things deadflowr mentioned.

I'm not interested in existing extensions, what i want to do is write an extension/theme myself that customizes my entire installation to my needs. I read everything is done in JS so i will try to dig in and try some things ;)

Thanks again

---

### Post by deadflowr on 2013-11-04
> **Jeffrey Martin said:**
> Thank you all so far, i am looking for the things deadflowr mentioned.

I'm not interested in existing extensions, what i want to do is write an extension/theme myself that customizes my entire installation to my needs. I read everything is done in JS so i will try to dig in and try some things ;)

Thanks again

Well good luck on your adventure
You might also look over this
[https://wiki.gnome.org/GnomeShell/Development](https://wiki.gnome.org/GnomeShell/Development)

---

