---
title: "Gnome 3.2 Menu in Gone"
date: 2011-11-11
forum: Desktop Environments
---

### Post by chazdg24 on 2011-11-11
I wanted to add a minimize and maximize to the right of my windows. So I did the following:

gconftool-2 --set /apps/metacity/general/button_layout  --type string "menu:minimize,maximize,close"
logout and login that it per the instructions of this website: 

I logged out and back in and that was it. No menu. Help!!!

There must be a way to reset the Menu.  I tried rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails.  That didn't work.

I  then tried rm -rf .gnome .gnome2 .gconf .gconfd .metacity.  That didn't work.

I then tried [Logout, switch to command line (Alt+ctrl+F1), login, do: rm -rf .gnome .gnome2 .gconf .gconfd .metacity, switch to X (Alt+ctrl+F7)].  That didn't work.

I can't find any other ideas on Google to try.  Thanks in advance for any ideas.

---

### Post by chazdg24 on 2011-11-12
I got it wrong.  What is crashing the Gnome menu is the gnome-shell-extensions-alternative-status-menu, installed via Terminal or Synaptic.  When I remove it, the menu stays put.  Any ideas how to install a Shutdown to the menu without it?  Thanks!

---

### Post by Frogs Hair on 2011-11-12
Try to logout and back in and the menu should be gone . I would suggest this when adding extensions prior to use also . With out the extension the method is to use the Alt key while the session menu is open and power off will display . [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by chazdg24 on 2011-11-12
> **Frogs Hair said:**
> Try to logout and back in and the menu should be gone . I would suggest this when adding extensions prior to use also . With out the extension the method is to use the Alt key while the session menu is open and power off will display . [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

Thanks.  I like the cheat sheet way.  I just wish I could make it permanent.  :(

---

### Post by Frogs Hair on 2011-11-12
> **chazdg24 said:**
> Thanks.  I like the cheat sheet way.  I just wish I could make it permanent.  :(

I have had good luck with the Webupd8 extensions so far . I assumed that is what you're using but if not . [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

---

### Post by chazdg24 on 2011-11-12
> **Frogs Hair said:**
> I have had good luck with the Webupd8 extensions so far . I assumed that is what you're using but if not . [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

The problem was that my profile did not have a picture.  Once I added a picture to my profile, the alternative-status-menu worked flawlessly.  That is just too bizarre as I tried to figure this problem out for days and days.  :?

By the way, I really appreciate your help.

Charlie

---

### Post by Frogs Hair on 2011-11-12
> **chazdg24 said:**
> The problem was that my profile did not have a picture.  Once I added a picture to my profile, the alternative-status-menu worked flawlessly.  That is just too bizarre as I tried to figure this problem out for days and days.  :?

By the way, I really appreciate your help.

Charlie

That is just weird ! I can't imagine why that would make a difference , but I glad it's working .

---

