---
title: "Em dash character input problem"
date: 2006-03-06
forum: Desktop Environments
---

### Post by nekr0z on 2006-03-06
I've set up a compose key via modifying xorg.conf, and it even seems to work, but not all of the compose key sequences do work. If there's a 2-key sequence, it's all OK, but with 3-key sequences it's not. For instance, I cannot input the "Em Dash" character. I press the compose key, then "minus" 3 times, then release compose key, but what I get is "--" and not the Em Dash.
Is there a workaround for this?

---

### Post by bogen on 2006-07-14
I'm experiencing the same problems (with German keyboard/system). *Some* compose key combinations, among them the en and em dashes and angle quotation marks (‹ and ›), simply don't work (and messing arount in /usr/share/X11/locale/en_US.UTF-8/Compose doesn't accomplish anything). :(

Any hints anybody?

(*sigh* Mac OS X still some light years ahead, I guess! ;) )

---

### Post by nekr0z on 2006-07-16
Well, I seem to have figured this out.

First of all, the correct way to input a compose sequence is 1. to press AND RELEASE compose key *and 2. enter the desired combination.

Second, the programs that a written in GTK (GNOME origin, like Firefox, Evolution etc.) do not accept compose sequences longer than 2 keys (not including the compose key itself), which makes it impossible to enter such characters as Em Dash (compose-minus-minus-minus). The programs written in Qt (KDE origin, like Kontact, Amarok etc.) DO accept compose sequences of any length.

So to input Em Dash in Firefox I usually open Kate, input it there, and then copy-paste it. Quite a pain in the arse, but I found no other way.

---

### Post by bogen on 2006-07-20
The is a solution: [http://ubuntuforums.org/showthread.php?t=209115](http://ubuntuforums.org/showthread.php?t=209115)

---

### Post by nekr0z on 2006-07-20
Great, it works! Thanks!

---

