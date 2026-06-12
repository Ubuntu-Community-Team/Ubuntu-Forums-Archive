---
title: "How do I show a program on my TV?"
date: 2011-02-18
forum: Desktop Environments
---

### Post by Paper Pusher on 2011-02-18
My PC has an Nvidea 9800GT graphics card.
Both my monitor and my HDTV are connected to the card.
I have configured both my monitor and my HDTV to my computer.
The monitor is screen 0.  The TV is screen 1.
Everything is normal on screen 0.
The desktop background shows on both screens.

How do I start an application on my TV?
When I drag a window from my monitorto my TV, the window disappears,

---

### Post by Krytarik on 2011-02-18
If you really set up separate xscreens for each of your monitor, as it sounds, then you cannot move a window to each others screen, instead you have to only move your mouse the other screen and open the program from there. You should then also have panels at both screens.

---

### Post by Paper Pusher on 2011-02-25
Thank you for your suggestion.

Yes, I can move the mouse freely between screens.  But how do I create a new panel on my TV screen?

I've also tried starting programs from the command line, but -display 0.0, 0.1, and 1.1 all show up on my monitor.  None show up on the TV.

---

### Post by Krytarik on 2011-02-25
Then you apparently haven't set up the xorg.conf correctly, if at all.

Try following this guide:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

---

### Post by Paper Pusher on 2011-02-25
Thank you for your suggestion.
I haven't set up xorg.conf.
I've merely been using the Nvidia driver GUI.
I'll study your link and report back.


P.S.  In what part of Berlin do you live?

---

### Post by Krytarik on 2011-02-25
> **Paper Pusher said:**
> 
P.S.  In what part of Berlin do you live?
"What part", LOL! I hope you are not referring to "East" or "West"! ;-) I live in Charlottenburg.

---

