---
title: "emacs won't show black on white"
date: 2006-01-20
forum: Desktop Environments
---

### Post by UphillSkier on 2006-01-20
HI, all 

I had to reinstall Breezy and ran into a funny problem with emacs.  I want to have it display black fonts on white background.  When I launch emacs from a terminal at first it starts as black on white and then reverses.   The normal switches don't work.  For example if I do 

```
emacs --background-color=pink &
```

the window starts off pink but then, just before mule is loaded, the window turns black.  There must be some initialization file countervailing the command line settings, but I can' t find it.  I don't have a .emacs file in my home directory. 

This problem did not happen when I installed from Breezy preview and upgraded. 
Can anyone suggest a solution?

BTW, I have autex and ess installed.

Thanks for any help
Andy

---

### Post by slashem on 2006-01-21
Put this in your .emacs:

(set-foreground-color "Black")
(set-background-color "White")

---

