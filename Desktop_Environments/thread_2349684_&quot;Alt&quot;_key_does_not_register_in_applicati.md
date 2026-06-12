---
title: "&quot;Alt&quot; key does not register in applications unless super is held first"
date: 2017-01-17
forum: Desktop Environments
---

### Post by Offlein on 2017-01-17
[COLOR=#242729][FONT=Arial]I recently switched to the "Ubuntu GNOME" distribution, from Ubuntu's standard distribution with the Unity window manager.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]For some reason, although using Alt+Mouse1 works to drag windows around just fine, the key does not work as a modifier within applications. In Slack, for instances, Alt+UpArrow should move to the previous conversation. It does nothing. In my IDE, Alt+F should open the file menu. It does not.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
What DOES work is holding the Windows (aka the Super) key, and then holding Alt. That works like just holding does the way that we'd expect. But this is incredibly awkward to press.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Things were a little weird initially, by the way, when I installed gnome-shell, and I figured this is because Unity had co-opted its own GTK settings, so I checked around and attempted to reset my settings by deleting the relevant hidden folders in my home directory, to the best of my ability.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm not sure if this triggered the change or if it existed before, but I thought it might be relevant.

I'm in Gnome 3.20.4. But if I switch to the "Gnome Classic" (Gnome 2.x, I think) desktop environment, this issue goes away.[/FONT][/COLOR]

---

### Post by Taemojitsu on 2017-01-17
If you go to somewhere that offers key-pressing detection, like setting shortcut keys, does the Alt key show up?

For example, in the CompizConfig Settings Manager (ccsm), when setting a keyboard shortcut, you press 'Grab key combination', and then if you press Alt, then an image of the Alt button turns green. Anything like that in standard Gnome?

---

### Post by Offlein on 2017-01-20
@Taemojitsu, I'm so sorry, apparently I don't get notifications [currently] for these.

Yes! Alt DOES turn green when I "grab" it in gnome-shell. And I can alt-tab (and rebind alt-tab) and stuff just fine.

---

