---
title: "Ubuntu Budgie Login Screen"
date: 2018-04-10
forum: Desktop Environments
---

### Post by speartip on 2018-04-10
Anyone know how to change the wallpaper of Ubuntu Budgies login screen?
It seems Budgie has it's own version of lightdm, but using lightdm-gtk-greeter-settings has no effect.
Thanks in advance.

---

### Post by Frogs Hair on 2018-04-10
They use slick greeter which is native to Mint . That may give you a place to start.

---

### Post by speartip on 2018-04-10
Thanks Frogs Hair.
Actually reading on the Solus Forum it seems it's not possible to do this at the moment, although the thread was nearly a year old.
I'll wait & see if anyone else chimes in. slick-greeter is installed, but it doesn't appear to be editable.

---

### Post by kerry_s on 2018-04-10
so settings-> background-> lockscreen
does nothing?

yeap it does nothing. go manual.

dconf-editor -> x -> dm -> slick-greeter -> background

yeap, won't change. guess it's work in progress :)

---

### Post by davidmohammed on 2018-04-10
Tracking this here on upstream - hint - look at the dbus command that gives the current workaround to change the users login wallpaper.

[https://github.com/budgie-desktop/budgie-desktop/issues/1326](https://github.com/budgie-desktop/budgie-desktop/issues/1326)

hint no. 2 ... if anyone can do a bit of coding we could squeeze in the fix for 18.04.

---

### Post by speartip on 2018-05-21
I'll mark this thread as solved as it seems that you can now change the Background in "Login Window"

---

### Post by gregorskii on 2018-06-09
When I change the login background using the Login Window app all I get is a solid color.. What do you think? budgie 18.04


EDIT: had to disable draw user backgrounds due to [https://github.com/linuxmint/slick-greeter/issues/94](https://github.com/linuxmint/slick-greeter/issues/94) it was trying to draw my users background, getting denied then drawing a color.

---

### Post by speartip on 2018-06-10
That's interesting, my "draw user backgrounds" is still enabled. Although all I'm doing is navigating to the /usr/share/backgrounds folder to pick a preinstalled picture. It may be different if your using your own pics.

---

