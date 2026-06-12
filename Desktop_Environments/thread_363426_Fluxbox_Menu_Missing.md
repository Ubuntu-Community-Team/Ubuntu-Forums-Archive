---
title: "Fluxbox Menu Missing"
date: 2007-02-16
forum: Desktop Environments
---

### Post by Dylnuge on 2007-02-16
Very excited to have my new Ubuntu desktop up and running, I finally decided to install fluxbox. I installed the software, and rebooted, selected it in GDM, and low and behold, no menu. When i right click I get this

```

Fluxbox

```

As opposed to the usual list of applications and commands that come under the Fluxbox title. I could not even log off, or open a terminal, or anything. All I could do was change desktops and check the time. Since the desktops had nothing on them, my computer was essentially a fancy clock.

Needless to say, I rebooted. (By use of the power button, I may add).

Anyone know what is wrong, or how I can fix Fluxbox so I can at least access the terminal.

I am really annoyed with the post reply button at the bottom of the edit screen. I just typed some new info and lost it.

So here is the short version: my menu file in my home/.fluxbox directory refrences a file that does not exist (/etc/X11/fluxbox/fluxbox-menu). There are two other similar files. Should I copy one to fluxbox-menu or edit my home directorys file to ref them?

Here is the list of files in that dir. Should be short work to tell which ones match.
fluxbox.menu-user  init  keys  system.fluxbox-menu

---

### Post by yabbadabbadont on 2007-02-16
Install the "menu" program and then run, "sudo update-menus".  After that you should have a fluxbox menu.  Just for future reference, when all else fails, just hit ctrl-alt-backspace to force x-windows to restart.  Which would have put you back at the GDM login screen.

---

### Post by Dylnuge on 2007-02-16
Thanks.

PS: Like your icon. Isn't that part of the Gentoo set (a very stylish set)?

---

### Post by yabbadabbadont on 2007-02-17
> **Dylnuge said:**
> Thanks.

PS: Like your icon. Isn't that part of the Gentoo set (a very stylish set)?

You are welcome.  I created it using the bubble icon template found in the Gentoo forums and then my fellow forum pal Wolven hosted it on his [www.ionbox.org](www.ionbox.org) website.  I think it was submitted by someone else later on for inclusion in the Gentoo Icons set.  I don't know if it was ever officially included though.

---

