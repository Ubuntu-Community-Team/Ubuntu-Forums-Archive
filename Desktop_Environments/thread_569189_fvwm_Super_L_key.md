---
title: "fvwm Super_L key"
date: 2007-10-06
forum: Desktop Environments
---

### Post by deserthowler on 2007-10-06
I am trying to use Super_L on my laptop as a modifier key to pop up some menus.  If I use Super_L as the only key, it works fine.  If I try to use if as a modifier, I have no luck.

my xmodmap shows mod4 Super_L but when I try 4 in the modifier location of a key binding, nothing seems to happen.

Earl

---

### Post by ThomasAdam on 2007-10-08
> **deserthowler said:**
> I am trying to use Super_L on my laptop as a modifier key to pop up some menus.  If I use Super_L as the only key, it works fine.  If I try to use if as a modifier, I have no luck.

my xmodmap shows mod4 Super_L but when I try 4 in the modifier location of a key binding, nothing seems to happen.

Earl

Shame you're not asking this on the fvwm forums, where I see you're registered,  

Can you be more specific as to what it is you've told FVWM to do?  Until then, there's nothing anyone can do to help you.

-- Thomas Adam

---

### Post by deserthowler on 2007-10-25
> **ThomasAdam said:**
> Shame you're not asking this on the fvwm forums, where I see you're registered,  -- Thomas Adam

:oops::oops:

> **ThomasAdam said:**
> Can you be more specific as to what it is you've told FVWM to do?  Until then, there's nothing anyone can do to help you. -- Thomas Adam

######################
###  Key bindings  ###
######################

# Keys for menus using Windows and Menu keys

Key Super_L        A     M     Menu MenuFvwmRoot
Key Super_L        A     C     WindowList
Key Menu           FSTW  M     Menu MenuWindowOps
Key Menu           A     C     Menu MenuNavigate
Key Menu           FSTW  S     Menu MenuWindowMove

This works now.  I found the hints to the solution by searching the FVWM forums. :biggrin::biggrin::biggrin:

Earl

---

