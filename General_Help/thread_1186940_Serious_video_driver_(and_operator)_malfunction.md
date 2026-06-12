---
title: "Serious video driver (and operator) malfunction"
date: 2009-06-14
forum: General Help
---

### Post by QIII on 2009-06-14
OK.  I should know how to fix this, but I'm flustered.

I have an ATI Radeon 3100 integrated video card.  I was actually helping someone else out, when I disabled the proprietary driver, then attempted to re-enable it.

While it was trying to download the driver, the system froze (a first for me).

I shut down and restarted.

Now what I have left is a black screen with some garbled colors in a band across the top of the monitor.

I've entered recovery mode, fixed my xorg.conf and have run dpkg-reconfigure xserver-xorg.

Still no joy.

Please help an old man remember...

---

### Post by QIII on 2009-06-14
Ach!

Never mind an old man, folks.

Needed to purge the fglrx driver...

Move along.  Nothing to see here but a doddering, drooling old gray beard.

---

