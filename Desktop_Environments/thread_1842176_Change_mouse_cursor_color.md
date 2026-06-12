---
title: "Change mouse cursor color?"
date: 2011-09-10
forum: Desktop Environments
---

### Post by b00n on 2011-09-10
This seems like a stoopid question... but how do I change the color of the mouse cursor?

It seems like I should be able to do something like ~/.Xresources
[INDENT] [FONT=Courier New]*cursorColor: red
*pointerColor: red
[/FONT][/INDENT]But log out/log in again, no change.  I have a notion there is a resource browser/editor someplace I found before -- I currently have orange cursors in both xterms and Emacs without any ~/.Xresources, or cursor color entries in ~/.emacs -- but so far have not found it again.

10.04 if it makes any difference (last I checked newer versions still had a bug driving my video card).

Thanks!

---

### Post by Copper Bezel on 2011-09-11
Do you mean by applying a mouse cursor theme? If you're running the Gnome desktop, see [this guide]("http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html"). Normally, this should be a simple GUI process; there's a bug in Compiz that requires you to change it manually by a text config file, but it's one quick edit. = D

Edit: I should note that the cursor theme selected in Appearance Settings > Theme tab > Customize affects the cursor when drawn over some windows, so you might need to change it there, as well, but once the cursor theme is installed, you can do this with a couple of quick clicks there.

---

### Post by BenB1 on 2011-12-03
> **Copper Bezel said:**
> Do you mean by applying a mouse cursor theme? If you're running the Gnome desktop, see [this guide]("http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html"). Normally, this should be a simple GUI process; there's a bug in Compiz that requires you to change it manually by a text config file, but it's one quick edit. = D

Works out quite well.

---

### Post by b00n on 2011-12-04
> **Copper Bezel said:**
> Do you mean by applying a mouse cursor theme? If you're running the Gnome desktop, see [this guide]("http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html"). Normally, this should be a simple GUI process; there's a bug in Compiz that requires you to change it manually by a text config file, but it's one quick edit. = D


I am not trying to change themes (that would be okay, too), just change the cursor color.

I will have a look at the guide -- thanks!

---

