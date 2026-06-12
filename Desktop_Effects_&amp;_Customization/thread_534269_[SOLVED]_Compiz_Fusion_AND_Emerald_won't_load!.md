---
title: "[SOLVED] Compiz Fusion AND Emerald won't load!"
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by jawinterton on 2007-08-25
Hey guys, I am going crazy trying to figure out why Compiz Fusion and Emerald won't load.  I thought I had it working, then I restarted and... nothing.  I did the alt-f2 "replace --emerald &" command too.  

Any ideas?

---

### Post by hyperair on 2007-08-25
t's "emerald --replace" and "compiz --replace"

---

### Post by BRILLtheTHRILL on 2007-08-25
when i run emerald --replace in the terminal i get this error.



(emerald:30658): Wnck-WARNING **: Unhandled action type (nil)
a bunch of times.

---

### Post by inkjob on 2007-08-25
i have upgraded, first the upgrade kills CF entirely. So I remove CF and emerald and reinstall and remove and reinstall this way and that following every step to the letter but i just can't seem to get emerald to load properly it is a little frustrating and i just thought i would post here. this is my first cup. :)

---

### Post by hyperair on 2007-08-25
So do I, but emerald runs. Open another terminal and type "pidof emerald" after that to check if Emerald is still running. If it is then there'll be a number as output.

---

### Post by H3g3m0n on 2007-08-25
Might be worth trying to delete all the configuration directories
```

~/.compiz
~/.config/compiz
~/.gconf/apps/compiz
```

Not all of them might be there, sometimes when compiz is updated some old configuration setting will break things.

---

### Post by hyperair on 2007-08-25
Well the rule is that if Compiz doesn't run, Emerald won't have any effect.

---

### Post by jawinterton on 2007-09-03
I got it working.  I just made sure my compiz fusion 3rd party software sources were connecting and working and then I was able to get the proper versions.  After that I did the replace thing after alt-f2 and it works now.

---

### Post by hyperair on 2007-09-04
Good to hear.

---

