---
title: "wow help please."
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by Lunatrix on 2007-07-14
i just installed my Graphics card drivers from the restricted drivers manager, now everytime i restart my screen just goes black. my computer screen shuts off SHUTS OFF then turns back on. i cannot see anything. i need some help please!!

---

### Post by Lunatrix on 2007-07-14
please anyone? i need an answer

---

### Post by WowMike2002 on 2007-07-14
> **Lunatrix said:**
> please anyone? i need an answer

Sounds like a refresh rate problem, try getting into your xonf file and manually setting it lower before you go to boot graphically, LiveCD if you need to.. if its an LCD it should be set to 60, CRT anywhere up to 72 is good depending on personal flavor.

Let me know if that helps at all!

---

### Post by Lunatrix on 2007-07-14
ok, i have no clue what youve said except for refresh rate lol. can you explain please?

---

### Post by Lunatrix on 2007-07-14
can you please explain?

---

### Post by haden9 on 2007-07-14
Try starting in Safe Mode, over at terminal type the following:

sudo dpkg-reconfigure xserver-xorg

Afterwards follow the configuration routine until you get to the monitor settings, three options should show up:

Simple
Medium
Advanced

Each and everyone of them have their proper characteristic, over at advanced you can set the refresh rate manually so I would suggest looking that information up about your monitor and setting up properly there. Let me know how it goes plz.

:popcorn:

---

### Post by Lunatrix on 2007-07-14
well im about to check it out, im bottin up

---

### Post by Lunatrix on 2007-07-14
didnt work

---

### Post by 3rdalbum on 2007-07-14
> **Lunatrix said:**
> didnt work

Have you restarted the computer?

Also, if you just want to get back to the desktop, you can follow that procedure until it gets to "Autodetect Video Card". At that point, you tell it NO. It will ask you to choose a driver - choose "vesa". When asked about "Autodetect Monitor Settings", tell it no, and then use the "Simple" item to choose the size of your monitor.

After that's finished, type:

```
sudo reboot
```

And reboot back into Ubuntu - you should have a basic unaccelerated desktop.

---

### Post by Lunatrix on 2007-07-14
man, then i wont be able to use compiz


this sucks

---

### Post by Lunatrix on 2007-07-14
and nope that didtn work either.

---

### Post by stepan2 on 2007-07-14
have u dont somethin to it to make it do this?can u tell us what u did. also ,sometimes if u are using compiz it has this error. maybe you are running compiz at autostart?

---

### Post by Lunatrix on 2007-07-14
i got it working. i used envy.

---

