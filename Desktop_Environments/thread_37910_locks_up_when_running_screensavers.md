---
title: "locks up when running screensavers"
date: 2005-05-29
forum: Desktop Environments
---

### Post by gogodidi on 2005-05-29
I recently 'discovered' a collection of screensavers in "/usr/lib/xscreensavers"
I looked through them, and some of them seem to crash and lock up my system, not just X, but the entire system, I can't go into another teletype, but I can move my mouse...

the only solution is to turn the pc off and restart it...

It has happened twice with the following screensavers

"flyingtoasters" and "skyrocket"

(I might want to mention that this is Ubuntu with KDE installed...)

I'm guessing this is to do with a bug in the software... but why does everything lock up?

---

### Post by Spleenie on 2005-05-29
[QUOTE=gogodidi]I recently 'discovered' a collection of screensavers in "/usr/lib/xscreensavers"
I looked through them, and some of them seem to crash and lock up my system, not just X, but the entire system, I can't go into another teletype, but I can move my mouse...

the only solution is to turn the pc off and restart it...

It has happened twice with the following screensavers

"flyingtoasters" and "skyrocket"

(I might want to mention that this is Ubuntu with KDE installed...)

I'm guessing this is to do with a bug in the software... but why does everything lock up?[/QUOTE]
 Is it possible that there are two screensaver managers running at once? xscreensaver is I believe different to the kde screensaver manager.

Also, are you able to ctrl-esc when your screen freezes? Or is there zero feedback from your keyboard?

---

### Post by gogodidi on 2005-05-29
my keyboard is "dead"

---

### Post by Mez on 2005-05-30
thos elook like GL Screensavers...


do you have open gl installed?

to test run the command

glxgears

from a console...

if this works properly, then well, I dont know, but if it doesnt, then you need to (re) install your openLG drivers

---

### Post by kudlaty82 on 2005-06-25
i think it has something to do with deb packages available in kubuntu. i have compiled my favourite screensavers (really slick screensavers)  from source and everything runs fine in kde control center - zero lockups or crashes

---

### Post by kudlaty82 on 2005-06-25
forgot to mention - you don't really have to mess up with either screensaver daemons or videocard or gl drivers (if they run properly - try glxgears) - it won't change anything. i've already tried

---

### Post by godzero on 2005-06-26
I have had similar probs.. mine seems to xorg eating up HUGE amounts of memory (2+ GB!!) durring a screensaver.
(that doesn't get de-allocated afterwards)

---

### Post by glasscleaner on 2005-06-26
same thing here.. opengl driver are ok. in gnome everything work well only in kde my computer freez.

---

