---
title: "Need help using Beryl and Emerald Themes"
date: 2007-07-18
forum: Desktop Environments
---

### Post by AndyCat on 2007-07-18
I need help with Beryl. I have installed it and I can use it, I dont like that when I start Beryl my borders dissapear... How do I fix this and I also installed the Emerald Themes Pack from the repositories coz I want to use the transparent borders. I open the emerald theme manager and select the one i want but nothing happens... :confused:

How can I use Beryl with the theme I want and how do I make it to start as default when i use my linux???


thanks in advance

---

### Post by steevols on 2007-07-18
Okay, I think I can help:

For the window edges, you need to check something first: is Beryl working? To do this, press ALT and click on a borderless window. If you can drag it jello-style, Beryl's core is running okay.

If that's working, then try pressing alt-f2 for a run box, then type "metacity --replace" to kill Beryl. Then, run "beryl --replace -c emerald" and see what happens. If it doesn't work, you could try "beryl --replace -c gtk-window-decorator" (emulates metacity).

To start beryl along with Gnome, goto Gnome Settings > System Preferences (or the other, maybe) > Sessions and add a beryl command.

---

### Post by AndyCat on 2007-07-18
hello there. Nothing happened.... :( dont know wat else to do.... Is there any way I can use emerald themes without starting beryl?

---

### Post by AndyCat on 2007-07-18
btw beryl core is working. But every time I start beryl my window borders dissapear.. and still no theme....

---

### Post by steevols on 2007-07-18
Idea: open a CLI (alt-f2, "gnome-terminal") and type "beryl"... post what comes up.

---

### Post by steevols on 2007-07-18
Oh! Duh... I hope.

Head into synaptic, search "emerald" and uninstall everything you see.

Then, install the main emerald meta-package.

THEN, open the Beryl Settings thingamajigger, head to "Window Decorations" and set "emerald" to the command.

Then, try again.

---

### Post by MightyMag on 2007-07-30
That little thing worked great for me. Many thanks.  :D

---

