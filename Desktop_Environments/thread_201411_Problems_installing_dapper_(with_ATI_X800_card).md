---
title: "Problems installing dapper (with ATI X800 card)"
date: 2006-06-21
forum: Desktop Environments
---

### Post by uzusan on 2006-06-21
Ive been trying to install 6.06 for the last few hours without much luck.

The main problem i am having is related to my ATI X800 GTO (PCI-E) graphics card.

Firstly i tried to install via the dapper desktop cd, by loading the live CD first, however i could not get this to work as the x configuration / graphics drivers didn't recognise my card and i kept getting errors saying that the x server could not start.

so i decided to try a different approach, i still have some warty install cd's, so i loaded one and once it had installed, it gave me the same errors.

This time though, because i had installed the base system i followed the guide for installing the ATI binaries from the ati website, using the fglrx drivers and i managed to get gnome to load fine.

I tried at this point to upgrade from warty to breezy, following the breezyupgrade guide, but once it had finished gnome wouldn't load anymore. it seems there were a lot of packages now missing (one that i can remember was libgnome2.perl and 4 dependencies of that)

Any ideas on how i should go about installing dapper? im not really sure what to try next. I dont mind wiping the partition (there's not much there at the moment anyway).

What i ideally want is to have my system up and running with 6.06 and Xgl/Compiz.

EDIT: just noticed i put this in the wrong place, can someone move it to the installation / upgrade help forum please?

---

### Post by Winblowz on 2006-06-21
Have you tried booting the Dapper Drake live-cd in "safe mode"? If not, I'd first try that. If it still doesn't work, then I'd try using the alternate install cd.

---

### Post by uzusan on 2006-06-21
yeah i tried safe mode after it didn't work the first time.

are there any guides on using the alternate install cd? it looks like it can do a lot more than i need it too.

EDIT: just noticed this thread - [http://ubuntuforums.org/showthread.php?t=191944](http://ubuntuforums.org/showthread.php?t=191944) ill give that a try first.

---

### Post by uzusan on 2006-06-21
Damn, it didn't work.

I got the same result as before, when the bootup gets to the section where the x-server is being initialised the display blanks out, literally no signal going to the monitor (the monitor displays a message telling me this).

---

### Post by daradib on 2006-10-21
New topic:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

---

