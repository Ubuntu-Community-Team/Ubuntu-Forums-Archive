---
title: "Keybehaviour in Enemy Territory"
date: 2007-10-10
forum: Gaming &amp; Leisure
---

### Post by multi on 2007-10-10
I've been playing Enemy Territory for a couple of years in Windows now and since I've started using Ubuntu as my main OS I figured why not play ET under Linux. 

Everything is working fine but I'm running into a minor but very annoying problem. I use the Left Control key for crouching in ET, when the Left Control is pressed I can not change weapon with the 1to7 keys. Well it is possible to change to knife (=1) when crouching, but changing back to any other is impossible. Adding to this problem is the fact that when I change to smg (=3) when crouched the game menu shows up, same as like I pressed the escape button. After some extensive googling I found out that the ctrl+3=escape combination is a shortcut that originated in the VT-terminal, though I haven' been able to find any solution on disabling this while playing ET or disabling it at all. It is not listed in the Gnome shortcut list. 

Any help on changing weapons while being crouched (read L_CTRL pressed + 1to7) and disabling the ctrl+3=escape function is greatly appreciated.

---

### Post by multi on 2007-10-15
Since it doesn't look like somebody is gonna be able to help me I figured out a way to work around the problem. I wrote a little script that loads when ET starts and switches the ALT and CTRL key with xmodmap, when ET stops the keys are switched back again. This fixes my problems in game but doesn't realy solve my question. That's why I'm not going to mark this thread as solved, I am still interested in just disabling the unwanted keybinds.

---

### Post by viperpiper on 2008-07-24
> **multi said:**
> Since it doesn't look like somebody is gonna be able to help me I figured out a way to work around the problem. I wrote a little script that loads when ET starts and switches the ALT and CTRL key with xmodmap, when ET stops the keys are switched back again. This fixes my problems in game but doesn't realy solve my question. That's why I'm not going to mark this thread as solved, I am still interested in just disabling the unwanted keybinds.

I have been having the same problem you initially described. Have you discovered anything else?

If not, could you give me an example of the script you use to solve the problem?

---

