---
title: "SCIM in dwm?"
date: 2010-02-26
forum: Desktop Environments
---

### Post by 655 on 2010-02-26
So I'm running dwm, and everything is going swimmingly, but the only thing that's missing is being able to pull up the SCIM toolbar to do CJK input. Specifically SCIM-Anthy.

When I start a dwm X session direct from the shell, I'm unable to pull up SCIM with what I believe to be the default keybinds (ctrl+space, ctrl+~,  (my binding) etc.).  I have scim launching in my xinitrc and when I drop to the shell I see that the SCIM daemon is running, but I can't pull it up.

When I launch a gnome session using dwm as the WM, I can pull up SCIM just fine.  I presume that the keybindings are stored somewhere that is more gnome-friendly and I need to find a way of doing that in dwm.

Here's my xinitrc:

```
#!/usr/bin/env bash
urxvt -e screen &
#export XMODIFIERS=@im=SCIM
#export GTK_IM_MODULE="scim"
#export QT_IM_MODULE="scim"
#scim -d &
#export QT_XFT=true
#export GDK_USE_XFT=1
export LANG="en_US.UTF-8"
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim-bridge"
export QT_IM_MODULE="scim-bridge"
export XIM_PROGRAM="scim -f x11 -c simple -d"
scim -f x11 -c simple -d
exec dwm-startup
```

FWIW, the commented out stuff is there because I decided to try with scim-bridge instead of scim, but either way the daemon runs in the background.  Where are these settings stored?  My urxvt setup and my system locale are completely primed to support UTF8 and CJK character input, but I just cant turn on the toolbar.

---

### Post by 655 on 2010-02-26
Okay, I was looking in SCIM settings.  Apparently the 'panel' that controls these things is designed for GTK; that may be part of the problem.  

I don't understand why I can't just use keybindings to do this, because the extent of my usage is hitting alt-grave to enable Japanese input, typing, then turning it off as needed.  I don't need the actual tray popup, but it seems as though it's being controlled by that...?

---

### Post by 655 on 2010-03-05
Bump!!

---

