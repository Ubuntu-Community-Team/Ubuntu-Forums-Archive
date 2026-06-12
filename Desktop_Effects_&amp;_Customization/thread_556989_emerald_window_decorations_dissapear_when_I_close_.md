---
title: "emerald window decorations dissapear when I close a window."
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by pixeltarian on 2007-09-22
first off, this is what the console spits out when I start compiz fusion (seems to run fine though):

compiz --replace
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded
/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.

A handler is already registered for the path starting with path[0] = "org"
(repeats this line over and over)

/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png


my problem is that when I run emerald, it works, but when I close a window all the window decorations disappear. 
 
when I bring it back again with "emerald --replace &" I get: 

jeffrey@jeffrey-desktop:~$ emerald --replace &
[1] 7914
jeffrey@jeffrey-desktop:~$ 
(emerald:7914): Wnck-WARNING **: Unhandled action type (nil)
(this also repeats a bunch of times)


any ideas? 
I've got a Nvidia FX6800 
I installed compiz fusion just some normal way through repos and such. 

let me know what information would be of use.  thanks so much, 

-pixeltarian

---

### Post by Forlong on 2007-09-22
> **pixeltarian said:**
> 
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded
/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
You have mismatched packages, probably due to use of multiple repositories.

---

