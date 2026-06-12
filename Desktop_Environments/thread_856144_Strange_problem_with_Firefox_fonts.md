---
title: "Strange problem with Firefox fonts"
date: 2008-07-11
forum: Desktop Environments
---

### Post by mmickey on 2008-07-11
Hi folks, 
yesterday I installed some new fonts, and deinstalled some displayfonts, but system fonts are up and running, also bitstream vera... but when I started my firefox today, I encountered that view... somehow each space is far to wide... bitsream vera is set in firefox and its rendering fine in every other application... 
could you please help me???
thanks in advance.
mickey

my system: hardy 64bit, FF 3.0

---

### Post by kerry_s on 2008-07-11
try clearing your cache.

can you put a screen shot of your font settings, like this:

---

### Post by mmickey on 2008-07-11
Thanks for your reply. Cache is cleared, didn't help.
Here is the other screenshot...
Tanks.
mickey

---

### Post by kerry_s on 2008-07-11
strange, your settings look fine to me. 
is it only with that font or all fonts?

---

### Post by mmickey on 2008-07-11
Its only in Firefox and with all fonts, at least with all testet, and I testet several... 

thats really annoying, reading a longer text is nearly impossible...

best, 
mickey

---

### Post by kerry_s on 2008-07-11
not sure what else you can try.

---

### Post by mmickey on 2008-07-11
thanks for your help...

---

### Post by kevmitch on 2008-07-11
You could take a look in View->Character Encoding to see what character set you're using.

Then browse to "about:config" and type "font" in the "filter" bar. See if any of the font definitions, particularly the ones for your encoding, look amiss. You also want to watch out for settings in BOLD. This indicates that they have been changed from their defaults.

---

### Post by mmickey on 2008-07-11
Hi I checked that... everything is fine here... but it still doesn't work...
do you know which lib is responsible for font rendering in firefox? 
could it be that I somehow messed something up with CSS styles, what could it be, and how to fix it?

best
mickey

---

### Post by kevmitch on 2008-07-11
I guess an easier way to start with a clean slate is to move your profile out of the way temporarily

```
mv ~/.mozilla ~/.mozilla.bak
```

Though, it's also a possible that the correct font is no longer installed or some strange newly installed font is being incorrectly identified as the regular Bitsream Vera. You might want to try undoing your font installations/deinstallations and, if that fixes it, adding them back one by one. I think you should be able to take a look in /var/log/apt, or /var/log/aptitude to get an idea of what changes you made.

---

### Post by kevmitch on 2008-07-11
I'm pretty sure that firefox 3 uses libcairo2 for rendering. You might also want to take a look at the dependencies of firefox and xulrunner-1.9. You can do that by right clicking them in synaptic, and selecting properties->dependencies.

---

### Post by mmickey on 2008-07-11
nothing works... I checked what you proposed, also without my profile... I think I'm back in wondows times... REINSTALL...

best
mickey

---

### Post by daWsOn_s on 2008-08-31
I have the same problem. Unbelievable there is no solution! I'm not willing to install the system again:mad:

It's just SPACE, I mean what kind of file has this style setting for firefox and epiphany? It has to be somewhere!

---

