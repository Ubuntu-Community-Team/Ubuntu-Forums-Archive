---
title: "Bad Ubuntu woes!"
date: 2009-01-22
forum: General Help
---

### Post by psycovic23 on 2009-01-22
Hey everyone,

I've been struggling to make a working Ubuntu setup for the past 2 months or so and I'm starting to come to the end of my patience.  I'm not new to Linux (used to use Gentoo way back when) but I no longer have time to run around fixing bugs...so is there anything that can be done?

I have a T61p on 8.10 and have been having problems with:

random kernel panics somehow involving wireless

Firefox is REALLY sluggish - GMail scrolling sucks

Flash sometimes starts skipping like a record and I have to restart Firefox

Firefox just goes into its grayed out "freezing" mode at times

Gnome-do is always crashing without me noticing

When I'm using GNU/Screen, switching between windows when I'm in vim doesn't refresh the buffer...aka, I'll switch back to vim and have to scroll through all the lines for all my code to appear

Nothing is snappy at all. Doing a shortcut to bring up the console takes a good 2 seconds.


Would it help if I were to downgrade to 8.04?  I REALLY don't want to go back to Windows...Linux is just way more convenient in terms of the things I work on daily, but if I can't fix these things, my computer's pretty much unusable. Help!

---

### Post by TenPlus1 on 2009-01-22
Try installing Ubuntu 8.04.1, turn off Tracker and Pulse Audio in Sessions, plus turn off Visual Effects in Appearance...

As for Flash, go here and get latest Flash 10 .deb for Ubuntu, install...

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Hope it helps...

---

### Post by psycovic23 on 2009-01-24
I went back to 177 drivers, and most of those things went away. I haven't had time to reinstall (and I hope I can fix things without doing that). Does anyone know why Firefox is so sluggish?

---

### Post by philinux on 2009-01-24
Firefox fine here but certain addons can slow it down

Run it in safe mode to see if any improvement. If so disable addons and bring them back one by one to identify the culprit.

firefox -safe-mode

---

### Post by gjoellee on 2009-01-24
The issues with Firefox has more with Mozilla to do then Ubuntu, and when it comes to flash in Linux it is not good. I used Xp before and flash worked extremely well. 

When I moved to Linux flash starts lagging and starts flickering etc....! This is Adobes fault

---

### Post by psycovic23 on 2009-01-24
> **gjoellee said:**
> The issues with Firefox has more with Mozilla to do then Ubuntu, and when it comes to flash in Linux it is not good. I used Xp before and flash worked extremely well. 

When I moved to Linux flash starts lagging and starts flickering etc....! This is Adobes fault

I'm trying Opera right now and it's still laggy on Gmail when I scroll. Any ideas?

---

### Post by sPiN1 on 2009-01-24
i suggest using the browser epiphany, it's the least sluggish browser and does all the things firefox does, just quicker.

---

### Post by jrusso2 on 2009-01-24
> **gjoellee said:**
> The issues with Firefox has more with Mozilla to do then Ubuntu, and when it comes to flash in Linux it is not good. I used Xp before and flash worked extremely well. 

When I moved to Linux flash starts lagging and starts flickering etc....! This is Adobes fault

Flash and Firefox work great for me never had a problem for years.  Maybe its a user issue?

---

