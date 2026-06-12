---
title: "TightVNC key mapping problem"
date: 2007-10-01
forum: Desktop Environments
---

### Post by ShaneMr on 2007-10-01
I've installed TightVNC in Gutsy but when I change the xstartup file in the .vnc directory the kep mapping gets horribly confused.

My original xstartup was

#!/bin/sh
x-window-manager &

I changed it to 
#!/bin/sh
exec gnome-session &

When I make this simple change the keyboard mapping becomes totally wrong. When I type 'f' I get 'h' etc. I have tried selecting a different keyboard layout within the gui. I have also tried using kde instead of gnome but there is the same problem. I am not sure what the problem could be?

I am running gutsy 64 on an opteron system.

If there is any other questions that could help please ask.

Thank you,

Shane

---

### Post by peabody on 2007-10-01
This is a know bug in vino.  I don't know the exact number, but it's in launchpad.  There was a work-around posted near the bottom, I can't remember what it was off of the top of my head.

---

### Post by mbannach on 2007-10-06
Check out my post in :

[http://forums.gentoo.org/viewtopic-p-4338164.html#4338164](http://forums.gentoo.org/viewtopic-p-4338164.html#4338164)

Sounds like you have a similar problem.

Matthias

---

