---
title: "[Solved] FVWM Super_L Key"
date: 2007-10-27
forum: Desktop Environments
---

### Post by deserthowler on 2007-10-27
> **deserthowler said:**
> I am trying to use Super_L on my laptop as a modifier key to pop up some menus.  If I use Super_L as the only key, it works fine.  If I try to use if as a modifier, I have no luck.

my xmodmap shows mod4 Super_L but when I try 4 in the modifier location of a key binding, nothing seems to happen.

Earl

I found some help searching the FVWM forum and came up with the following key bindings which work fine:

###########################
###  Menu Key bindings  ###
###########################

# Keys for menus using Windows and Menu keys

Key Super_L        A     M     Menu MenuFvwmRoot
Key Super_L        A     C     Menu MenuNavigate
Key Super_L        A     S     Menu MenuAdmin
Key Menu           FSTW  M     Menu MenuWindowOps
Key Menu           A     C     WindowList
Key Menu           FSTW  S     Menu MenuWindowMove

This might not be the most elegant of solutions but it works on my Dell 1420n laptop.  I decided not to use the Super_L and Menu keys as modifiers but went with M, C, and S.  I got some strange results trying the Super_L as a modifier. :confused:

My apologies to Thomas for not going to the FVWM forum to ask first. :oops:

My FVWM window manager grows slowly but it is more functional (for me) and fun than Gnome.

Earl

---

