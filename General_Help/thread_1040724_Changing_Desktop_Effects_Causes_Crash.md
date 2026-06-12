---
title: "Changing Desktop Effects Causes Crash"
date: 2009-01-15
forum: General Help
---

### Post by ArdentMoth on 2009-01-15
So I noticed the other night that my Acer Aspire 5610 was finally capable of using desktop effects, including "Extra Effects."

Formerly, I had been unable to do this, thanks in part to my inability to properly get my motherboard and graphics working. So I was thrilled! If, I thought, I could finally use the effects, then maybe I could finally run Eve Online, or play Quake.

Well I was wrong.

I went to customize what kinds of effects I wanted (after playing with it and seeing that it was succesful; what a lovely little "wobbly window" thing when you drag em around violently) and got a shock around tab 3 or so. apparently my laptop didn't like something I did, the screen displayed a vibrant rainbow of artifacts and jiggity pink/green mess, then turned pink, then took me back to the login screen.

I logged back in.

After another blindingly multi-colored screen, it returned me again to the login screen. It was so anti-climactic that I had to do it about 3 more times before trying failsafe (which failed; had to do a hard reboot) and kde (apparently i don't have it?!). Not to be daunted, I tried again on good ol' Gnome; nothing.

HALP?

Thanks for reading.

---

### Post by gettinoriginal on 2009-01-17
Since you are asking in forums, I assume that you have the ability to get to terminal:  Enter this and it will return Compiz to default settings:  :P
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by Wartender on 2009-01-17
did this happen after activating the magnifier plugin? because something similar happened to me when i did that. i disabled it from the failsafe terminal using ```
key="gconftool-2 /apps/compiz/general/allscreens/options/active_plugins" ; $key -s -t string $($key -g | sed -e 's/,mag//g')
```

---

### Post by ArdentMoth on 2009-01-19
Thanks so much. It worked using the shorter version (what gettinoriginal posted) but I'm sure the longer line (Wartender) would have too.

Solved.

---

