---
title: "[SOLVED] Compiz Fusion Transparency/Exclusions"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by ep3w on 2008-02-21
I am using compiz fusion in Gusty with AWN and I have figured out how to get the top menu bar transparent by using type=dock in the general settings in compiz and setting it to whatever value.  My problem is, this also makes AWN transparent.  My question is, is there any way i can have it not make AWN transparent too? Is there some other type I can use or some way i can get it to exclude specifically AWN maybe in window rules? Thanks for any help!

---

### Post by pythonusr on 2008-02-21
Well, you can just make the top bar by using ALT + SCROLLWHEELDOWN to get the transparent effect.

---

### Post by ep3w on 2008-02-21
I will have to try that when I get back, I am in class right now and don't have my mouse with me :)
That uses the same compiz fusion transparent effect, not the default gnome one that leaves the area around the clock and actual menus non transparent?

---

### Post by ep3w on 2008-02-21
ALT+MOUSEWHEEL works perfect and does what I want, but is there someway I can get it to stay like that after a  reboot? I am guessing its a shortcut to some setting in compiz but what one?

---

### Post by Psyker7 on 2008-02-22
name=gnome-panel

instead of type=dock wins.

---

### Post by ep3w on 2008-02-22
Yup that worked perfect! Thanks, i knew there was something I was missing.

---

### Post by Psyker7 on 2008-02-22
One point to note, it appears to not work to any panels created after compiz is loaded, or after you have changed the settings. As panels seem to load after compiz at startup this makes things look a bit weird.

```

sleep 5
compiz

```

Run at startup should fix it.

I use it to make a panel appear behind AWM, looks sweet :)

---

