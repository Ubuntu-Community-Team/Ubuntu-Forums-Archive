---
title: "processor timing"
date: 2009-04-14
forum: General Help
---

### Post by gamelord12 on 2009-04-14
I've tried running both Hitman: Codename 47 (Steam version) and Unreal Tournament on 64-bit Ubuntu using a Core 2 Duo.  Both would be fine, but it seems that they each rely on a clock function to tell how much time has elapsed.  This causes the conversations in Hitman to be cut short and it causes Unreal Tournament to run at twice the speed.  Is there any way to adjust the clock function that these games rely on?  At first I thought it was that these games were running on both cores instead of just one (which is how I usually solve these things when they happen in Windows) but after trying three different utilities to do that, that wasn't the case.  Any ideas?  I figure some smart person wrote a program for this by now.

---

### Post by gamelord12 on 2009-04-15
Any ideas?

---

### Post by richlowe101 on 2009-09-01
Be warned that I haven't tested this myself yet [I have the same problem] but I will do later today.

Download [[COLOR="Blue"]this launch script[/COLOR]]("http://icculus.org/lgfaq/files/ut") and replace the script in /usr/local/games/ut (or wherever you installed UT) with this script.

[Advice taken from [[COLOR="Blue"]here[/COLOR]]("http://icculus.org/lgfaq/")]

---

