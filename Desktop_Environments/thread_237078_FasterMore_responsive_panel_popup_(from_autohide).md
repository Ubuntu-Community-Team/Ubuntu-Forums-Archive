---
title: "Faster/More responsive panel popup (from autohide)"
date: 2006-08-15
forum: Desktop Environments
---

### Post by 3ntity on 2006-08-15
Hello,
I was wondering if there's any way to make (GNOME) panels which you've set to autohide to appear faster/be more sensitive. Now it takes about 1-1.5s to appear with 4 buttons :/, and running on a PIV, 1GB RAM I feel it could be quite a bit better then that (I'm used to the responsive RK Launcher under windows... hoping to achieve a similar effect). 
Also, can you make a panel disappear completely? Now there's still an indication of it being there when using autohide, and the arrow alternative is quite annoying as well. Or are there any alternative programs/apps I could use for this, a la RK Launcher?
Thanks in advance :)

**edit:** getting panels to popup faster (say, after 50ms), can be achieved with:
> **mcduck said:**
> yes, and the trick is even fairly easy:

1. Open Configuration Editor (you can just run 'gconf-editor' in a terminal)
2. Browse to apps/panel/toplevels and find your panel there
3. set 'unhide_delay' to 50 (or whatever you want)
All credits go out to mcduck!

---

### Post by wilberfan on 2006-11-27
> **3ntity said:**
> Hello,
I was wondering if there's any way to make (GNOME) panels which you've set to autohide to appear faster/be more sensitive.

I've just set my top panel to "autohide" and I'm wondering about this, too...   It seems just a triiiiiiifle too slow to suit me.

Anyone know if this setting can be changed?

---

### Post by mcduck on 2006-11-27
yes, and the trick is even fairly easy:

1. Open Configuration Editor (you can just run 'gconf-editor' in a terminal)
2. Browse to apps/panel/toplevels and find your panel there
3. set 'unhide_delay' to 50 (or whatever you want)

---

### Post by wilberfan on 2006-11-28
Gaaaah!    That works *awesome!*   One less teensy aggrivation in my life!  :D

---

### Post by mcduck on 2006-11-29
oh, I forgot the part about making it disappear completely..

If you didn't notice it yet, in the same place in Configuration Editor there's value 'auto_hide_size'. Set that to 1 and you'll hardly notice the panel any more. (0 doesn't work, you still need to be able to move your mouse over the panel to make it unhide).

---

### Post by ComplexNumber on 2006-12-28
> **mcduck said:**
>  (0 doesn't work, you still need to be able to move your mouse over the panel to make it unhide).
i've noticed that too. it works in all other distros, though. also, when i tried both edgy and dapper, the hide_delay and unhide_delay doesn't even have any effect when to 0. any idea why? :confused:. should it be set to 1 instead?

---

### Post by d3v1ant_0n3 on 2006-12-28
I have my hide size set to 0 - it works fine 95% of the time.

---

### Post by ComplexNumber on 2006-12-28
> **d3v1ant_0n3 said:**
> I have my hide size set to 0 - it works fine 95% of the time.
what about the other 5%?

one of the first thing i do when i install a new distro is to change the hide_delay, unhide_delay, and auto_hide_size to 0. but its never once worked in ubuntu. it just has no effect. i mean, its not as if it it were a one-off. ive install ubuntu  about 5 times, and each time its not worked. there must be a reason why.

---

### Post by manutdfan2850 on 2007-01-03
> **mcduck said:**
> yes, and the trick is even fairly easy:

1. Open Configuration Editor (you can just run 'gconf-editor' in a terminal)
2. Browse to apps/panel/toplevels and find your panel there
3. set 'unhide_delay' to 50 (or whatever you want)

you are a lifesaver 

Thank you!!!!!!! =D>

---

### Post by rbhigday on 2007-01-03
> **mcduck said:**
> yes, and the trick is even fairly easy:

1. Open Configuration Editor (you can just run 'gconf-editor' in a terminal)
2. Browse to apps/panel/toplevels and find your panel there
3. set 'unhide_delay' to 50 (or whatever you want)

Thanks for the tips, With my little 14 inch screen every little bit a screen real estate I can gain is a plus.  But the slow delay for hiding and showing was driving me crazy, thanks again.

---

### Post by rbhigday on 2007-01-14
Just a note for you dual monitor people you will have to edit this again once you installed the second monitor as they each have there own settings

---

### Post by 3ntity on 2007-03-13
> **mcduck said:**
> yes, and the trick is even fairly easy:

1. Open Configuration Editor (you can just run 'gconf-editor' in a terminal)
2. Browse to apps/panel/toplevels and find your panel there
3. set 'unhide_delay' to 50 (or whatever you want)
I guess it's a bit late by now, but i stopped checking for answers after about two months... 

Anyways, thanks a lot, both tips you've given are very useful :D

---

