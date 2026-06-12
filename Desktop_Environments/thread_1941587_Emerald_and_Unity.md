---
title: "Emerald and Unity?"
date: 2012-03-15
forum: Desktop Environments
---

### Post by Spewed on 2012-03-15
Does Emerald work in Ubuntu 11.10 with Unity and Compiz? I just want to be sure there are no complications, or interferences on either end.

---

### Post by lovinglinux on 2012-03-16
Yes, it works. However you need to get a special version that was patched, since it is no longer under development.

I don't remember exactly where I got it, but I believe it was from [https://launchpad.net/~malteworld/+archive/compiz/+packages](https://launchpad.net/~malteworld/+archive/compiz/+packages)

More info at [http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html](http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html)

The article is for Ubuntu 11.04, but it worked with 11.10 as well.

Keep in mind it will probably be unstable.

---

### Post by Spewed on 2012-03-16
> **lovinglinux said:**
> Yes, it works. However you need to get a special version that was patched, since it is no longer under development.

I don't remember exactly where I got it, but I believe it was from [https://launchpad.net/~malteworld/+archive/compiz/+packages](https://launchpad.net/~malteworld/+archive/compiz/+packages)

More info at [http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html](http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html)

The article is for Ubuntu 11.04, but it worked with 11.10 as well.

Keep in mind it will probably be unstable.

I followed this guide. [http://www.ubuntubuzz.com/2012/01/install-emerald-theme-manager-on-ubuntu.html](http://www.ubuntubuzz.com/2012/01/install-emerald-theme-manager-on-ubuntu.html)

I thought that it was working, but whenever I type in "emerald --replace" I get the following 

root@kolton-TZ68A:/home/kolton# emerald --replace

(emerald:24562): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:24562): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:24562): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:24562): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


Whenever I close out the terminal I have no windows decorations. From there I type in 

gtk-window-decorator --replace

I get the same message, I close out of the terminal and the windows decorations yet again go away. ?

---

### Post by Spewed on 2012-03-16
Nevermind, looks like the issue resolved it's self.

---

### Post by Spewed on 2012-03-16
> **Spewed said:**
> Nevermind, looks like the issue resolved it's self.

I lied, the situation only resolved it's self momentarily. I closed the terminal and my borders stayed, no issues, right? Of course not. So I open up emerald and try to switch the theme, it changes to none of themes that I have. So I open back up the terminal and take a shot in the dark and type in again "Emerald --replace". Then my theme changes, but once I close the terminal my borders go away. Apparently I have to keep open the terminal to have any windows borders. 

Even trying to revert using the gtk replace command I showed you earlier, can't close out of that terminal.

---

### Post by wojox on 2012-03-16
Install CCSM and then go into ccsm and set the Window Decoration to -> emerald --replace Reboot and you should be good.

---

### Post by Spewed on 2012-03-16
Thanks, that worked! :D

---

