---
title: "Tearing while watching movies as well when dragging windows around."
date: 2009-01-11
forum: General Help
---

### Post by Nitrius on 2009-01-11
I got an ATI 4870 512MB card, and here on Ubuntu everything tears a lot, if i drag a window around or while i watch movies. And i wonder if this is possible to fix? Tried turning on the vblank feature in the compiz control panel, but that didn't change much. I've also tried with the drivers that came with Ubuntu and with drivers right of the ATI site(8.12).

This is in Ubuntu 8.10.

---

### Post by louierev07 on 2009-01-11
im having the same problems.  I tired turning off all effects and it helped a little but i still see some.  Im using a Q6600 CPU and an 8800GT vid card,  Im assuming my computer should be good enough to use all effects.

Could this be CPU related?  do u also have a Q6600?  I tried adding a cpu freq scaling monitor to my panel and it wont let me because something isnt configured,  Could this be why its not performing?

---

### Post by Nitrius on 2009-01-11
Got q6600 as well. Though it overclocked to 3GHz. But i doubt that is the problem, tearing is usually related to the graphic card. My guess is that this is some kind of driver problem or some bad implementation somewhere for the graphic cards.

---

### Post by louierev07 on 2009-01-11
if u try to add cpu scaling monitor does it give u this:

CPU frequency scaling unsupported

is this the case with all cpu's?

---

### Post by mtbsoft on 2009-01-11
It's a known issue with ATI graphics - my own does the same though not so much with moving windows about - I understand that it is an issue mainly on the ATI side.  I've tried all sorts of methods to be able to watch videos under fusion, none have worked.

I've followed one suggestion and installed Fusion-Icon (sudo apt-get install fusion-icon).  It doesn't stop the problem but provides a simple and easy-to-access way of switching between compiz and metacity (effectively turning on and off and the compiz effects).  I switch to metacity whenever I want to watch a movie and switch back the rest of the time.

Not ideal but workable.

---

### Post by mtbsoft on 2009-02-03
Happy Day!!!

I just installed the latest 9.1 release of the ATI proprietary video drivers and... NO MORE TEARING!

I had to check that I still didn't have Metacity enabled but it's true, the latest driver appears to have finally cured the dreadful flicker and tearing issues.

I watched an entire movie and only saw the very occasional little twitch, all which coincided with other high CPU activity going on in the background on my laptop.

Woohoo!

---

### Post by theApokalypsis on 2009-02-03
Indeed the new drivers do! glad you beat me to the punch. 

Of course there are still some quirks and issues but full Compiz/Xv playback none the less.

been waiting some time!

:D

---

### Post by Crafty Kisses on 2009-02-03
Oh that's good the new drivers fix it, although I don't use ATI, I'm still glad. Thanks for the information.

---

