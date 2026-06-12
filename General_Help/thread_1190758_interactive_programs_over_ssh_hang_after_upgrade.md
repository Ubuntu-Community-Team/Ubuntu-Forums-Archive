---
title: "interactive programs over ssh hang after upgrade"
date: 2009-06-18
forum: General Help
---

### Post by jokkmokk on 2009-06-18
hi,

I recently upgraded to ubuntu 9.04 and now I get a very strange ssh problem. I have a small server running debian etch and I can connect to it just fine. But when I start an interactive program like vi or top it seems to just hang, there's no output, nothing happens, I can't even kill it with ctrl-c. This happens with the gnome-terminal as well as from a tty. If I connect from a windows machine using putty it works, so I assume it's a problem with ssh?! Unfortunately I have no clue how to approach this problem so I would appreciate any help you can offer.
I was running 8.04 originally, there everything worked. I then installed 8.10 from scratch and immediately upgraded to 9.04 so maybe the problem already existed with 8.10?

thanks,

jokkmokk

---

### Post by jokkmokk on 2009-06-23
i still have this problem, anyone got any ideas?

---

### Post by charlmatthee on 2009-07-19
Have you tried ssh -t?

From the man page:

-t      Force pseudo-tty allocation.  This can be used to execute arbitrary screen-based
        programs on a remote machine, which can be very useful, e.g. when implementin
        menu services.  Multiple -t options force tty allocation, even if ssh has no local tty.

---

