---
title: "ZSNES Display problems"
date: 2010-05-08
forum: Gaming &amp; Leisure
---

### Post by hanlon on 2010-05-08
I cant get ZSNES to start on my aspire 1 netbook, running 9.10 NBR.

When I run it in terminal, it says "unable to start xxx X xxx display" (or something similar, where the xxx´s are the resolution)

Sorry, cant provide the EXACT terminal readout, as posting this from an internet cafe.  (Travelling, wifi is scarce).

Any ideas?

---

### Post by hikaricore on 2010-05-08
That means whatever display you're using does support the resolution it's trying to use.
You'll need to manually set the resolution in your ~/.zsnes/zsnesl.cfg file to a size supported by your netbook.

---

### Post by hanlon on 2010-05-08
Nope.  Still wont work.  I set it to 1024x600 which is the native resolution of the screen, and I still get  

> ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Could not set 1024x600-GL video mode.


(I found wifi)

Tried reinstalling both zsnes and SDL, and neither helped.

Im at a loss, and really want to play Final fantasy to kill some time on buses

---

