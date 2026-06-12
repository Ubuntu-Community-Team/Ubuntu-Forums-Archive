---
title: "Odd little gnome problem after crash"
date: 2007-08-27
forum: Desktop Environments
---

### Post by Goombie on 2007-08-27
I was goofing off playing a little Supertux Cart, when the game crashed on me all of a sudden. After the crash, my screen resolution was too small, so I did a Ctrl+Alt+Backspace, and logged in again. Now, I have the following problems:
1) The disk I keep my files on (a separate partition which is mounted automatically) does not show up on my desktop, although it does show up in the "Places" menu.
2) My desktop background, which is also kept on that disk, does not show up.
3) The right mouse button does not work if I click anywhere on the desktop background, but it works fine everywhere else (on the Panel, Nautilus, Firefox, etc).

So, that's my problem. I've tried rebooting and turning my computer off and on again, but the problem persists. My guess is that it's screwed up settings file somewhere, but I don't know where to look. Thanks for any help! :)
(Popcorn to whoever can help me fix it) :popcorn:

---

### Post by phidia on 2007-08-28
I'm not at home on my linux box ATM but if you open your desktop and go to the "View" menu item and select "view hidden files" you should be able to just rename files in your gnome and/or desktop settings. Remember/record your changes somewhere and keep restarting X in the method you've already described. 
You should be able to figure out which setting/preference "dot" file is causing the problem by doing that. Good luck and let us know how that works for you.

---

### Post by Wolki on 2007-08-28
Do other desktop icons show up?

---

### Post by Goombie on 2007-08-28
Umm, no, they don't. I tried a couple files and their icons don't show on the desktop. I'm guessing that has something to do with this.

---

### Post by Wolki on 2007-08-28
Try the following: alt-F2, "gconf-editor", return.

In the window that opens, navigate to /apps/nautilus/preferences/show_desktop and check whether the checkbox is checked. If it isn't, do that.

---

