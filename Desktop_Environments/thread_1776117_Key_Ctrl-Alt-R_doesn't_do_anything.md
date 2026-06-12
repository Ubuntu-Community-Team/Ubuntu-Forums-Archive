---
title: "Key Ctrl-Alt-R doesn't do anything"
date: 2011-06-05
forum: Desktop Environments
---

### Post by pheitman on 2011-06-05
I've just done a fresh install of Natty. The key Ctr-Alt-R doesn't do anything. I've checked in both Unity and Gnome. Using the Keyboard Layout GUI when I press Ctrl and then Alt and then R, the Ctr and Alt keys light up but the R key doesn't. Ctr-Alt-S works (and so do the other keys I've tried). kev shows a keynotify event for Ctrl-Alt-R, not a keypress event. I've checked my Keyboard Shortcuts to make sure it isn't listed there, but since the Keyboard Layout doesn't show the R key being pressed I don't think it's a shortcut issue.

Any ideas? I'd like to be able to use Ctrl-Alt-R in emacs...

Thanks in advance,

Peter

---

### Post by landisf on 2011-07-23
I seem to have the same problem. I just installed Natty from scratch and tried to use my old .emacs file. My binding to \C-\M-r doesn't work anymore. Binding to \C-\M-l works fine.

Update: It seems that I can actually help someone for the first time in this forum :): I noticed that ctrl-alt-r moves my window back to the old position if I previously moved it with one of  the (presumably new) short-cuts ctrl-alt-num1, ctrl-alt-num2,... 
     [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html) inspired me: to change this,  install compizconfig-settings-manager ( **sudo apt-get install compizconfig-settings-manager** ). In the compizconfig-settings-manager under the 'window management section', find the 'grid' settings. There, convince ubuntu, that you don't need the 'restore' mechanism bound to ctrl-alt-r very often and disable it. This takes effect immediately.

And, did this help? :)

Florian

---

### Post by pheitman on 2011-07-24
Yes! That solved the problem - thanks for the tip!

---

