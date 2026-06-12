---
title: "Can't change the launcher icons in AWN....."
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by Izobalax on 2007-05-10
OK....

I've got Avant-Windows-Manager nicely installed now and it all works ***fine***.... except that I can't change the launcher icons. When I right-click an icon and select "preferences", the little pop-up window gives me the option to change the icon used, but nothing happens when I click on this option. :( 

I tried for AWN in the configuration editor, but there didn't seem to be any icon editor option in there for AWN. 

Any ideas, O' Peeps of Ubuntu?

/izo

---

### Post by uthturn on 2007-05-10
i have the exact same problem

---

### Post by kpolice on 2007-05-10
It is just a placeholder and is not yet implemented

---

### Post by Izobalax on 2007-05-11
> **kpolice said:**
> It is just a placeholder and is not yet implemented

Really? That's a shame. I also noticed that AWN didn't save my launchers, resulting in a blank bar when I switched my machine on. I've just seen that this, also, seems to be a common problem. :(

What a shame. 'Tis quite nice really. Looks like I'll have to stick gDesklets for the mo.

/izo

---

### Post by aldreis on 2007-05-12
If you are willing to wait a little for the AWN developer, you could always edit the launcher ( a .desktop file ) and change the icon directly. 

You'll find the launcher files AWN uses through gconf-editor:

apps > avant-window-navigator > window_manager > launchers

---

### Post by Izobalax on 2007-05-13
> **aldreis said:**
> If you are willing to wait a little for the AWN developer, you could always edit the launcher ( a .desktop file ) and change the icon directly. 

You'll find the launcher files AWN uses through gconf-editor:

apps > avant-window-navigator > window_manager > launchers
Ah yes, I've just found that. How do I change the icons directly though there, then?

/izo

---

### Post by Izobalax on 2007-05-14
Nevermind. I figured it out. Stick the launchers on the desktop, change the icons there, then add them to AWN. :grin:

EDIT: unfortunately, it seems that AWN is unable to remember the icons when the system is booted up. :( I've figured out how to add launchers into AWN and keep it remembered, but it unfortunately means that I can't yet change the icons once I've done so. :(

/izo

---

### Post by airtonix on 2007-06-09
is better now.
+ right click to edit launcher from awn bar.
+ drag .desktop icons onto bar to make new launchers

would really like to see this : 
- move icons around on bar
 - set dimensions of bar
 - make drawers
 - swallow gnome apps like the xfce-gnome-applet

---

### Post by Zwoep on 2007-06-09
AWN still doesnt remember my launchers. :(

---

### Post by orb9220 on 2007-06-09
Did you install AWN from synaptic or package?
Do you have save sessions checked in sessions manager?

Just shooting in the dark here.

---

### Post by Bohlio on 2007-06-09
I think the launchers have to be in the top or bottom panel, or in the applications menu in order for AWN to remember them. I got a little mixed up about that when i first got AWN but Now i have it working perfectly.

---

