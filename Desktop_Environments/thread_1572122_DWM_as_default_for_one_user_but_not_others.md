---
title: "DWM as default for one user but not others"
date: 2010-09-10
forum: Desktop Environments
---

### Post by metal.lunchbox on 2010-09-10
I have a desktop that I would like to use DWM with. I have used DWM before and love it, but that was on computers that no one else would use. Previously, I used xinitrc without a display manager. I'd like to keep my ubuntu 10.04 system more or less as is for all but one user- me. In the Login Screen preference dialog I can choose the default session but I would like to change only the default for one user. Is this possible? I'd like for gdm to just run an .xsession script as I did before instead of launching the default gnome session with metacity window manager, but I'll accept any solution which allows me to use dwm as the window manager for only one user. I'm very familiar with dwm and related tools but I do not have a proper understanding of how gdm works to fix this.

---

### Post by metal.lunchbox on 2010-09-10
I have looked into this more and I was able to get my user to have a dwm session by creating a file called dwm.desktop in /usr/share/xsessions/ which just executes dwm and a file ~/.dmrc which tells gdm to use dwm.desktop as the default session for that user. This works but it doesn't really do what I want. Obviously I could have dwm.desktop launch a script like .xinitrc instead of just dwm but the I'd really like to continue using gnome-session, just without it launching metacity and gnome-panel among other things. That way I can still logout and switch users easily.

---

### Post by metal.lunchbox on 2010-09-15
Like many things involving dwm, not specific to dwm code, the answers to my question can be found on the Xmonad wiki

see this article about gnome integration: [http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome](http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome)

---

