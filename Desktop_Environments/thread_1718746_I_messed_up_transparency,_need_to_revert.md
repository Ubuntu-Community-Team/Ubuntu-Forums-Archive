---
title: "I messed up transparency, need to revert"
date: 2011-03-31
forum: Desktop Environments
---

### Post by teejay17 on 2011-03-31
Hi all,
I messed up when playing with transparency in Opacity settings in Compiz, and made everything too transparent, to the point that I can't do anything on my desktop. All I see is my wallpaper. 
How can I kill this to revert back to the old setting, or at least enter into a safe graphics mode to reset? 
Thanks in advance.

---

### Post by teejay17 on 2011-03-31
Or would killing Metacity do the trick? Problem is, I can't even see the terminal, as it is 100% transparent! 
Would fixing it via live CD be an option?

---

### Post by Krytarik on 2011-03-31
a) while you are over a window you would like to see, press Alt and use the mousewheel to increase the opacity of that window

b) press Alt+F2 and enter "metacity --replace" blindly, to run Metacity to be able to revert Compiz' settings

c) press Ctrl+Alt+Backspace to quit your running xsession and login to "Failsafe GNOME"

b) if nothing else helps, boot into "recovery mode"

---

### Post by teejay17 on 2011-03-31
> **Krytarik said:**
> a) while you are over a window you would like to see, press Alt and use the mousewheel to increase the opacity of that window

b) press Alt+F2 and enter "metacity --replace" blindly, to run Metacity to be able to revert Compiz' settings

c) press Ctrl+Alt+Backspace to quit your running xsession and login to "Failsafe GNOME"

b) if nothing else helps, boot into "recovery mode"
Thanks, you are a life saver! "A" worked long enough to enable me to see enough to implement "B".

---

### Post by Krytarik on 2011-03-31
> **teejay17 said:**
> Thanks, you are a life saver! "A" worked long enough to enable me to see enough to implement "B".
LOL:P

See my earlier post about how to avoid this:
[http://ubuntuforums.org/showthread.php?p=10488654#post10488654](http://ubuntuforums.org/showthread.php?p=10488654#post10488654)

---

### Post by teejay17 on 2011-03-31
> **Krytarik said:**
> LOL:P

See my earlier post about how to avoid this:
[http://ubuntuforums.org/showthread.php?p=10488654#post10488654](http://ubuntuforums.org/showthread.php?p=10488654#post10488654)
That is definitely good to know for future reference.

---

