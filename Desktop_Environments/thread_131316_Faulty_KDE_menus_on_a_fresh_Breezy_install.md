---
title: "Faulty KDE menus on a fresh Breezy install"
date: 2006-02-16
forum: Desktop Environments
---

### Post by sniffass on 2006-02-16
This install was performed just last night, and i've stuck to only the recommend packages for installation for fear of breaking my installation. I opened up digikam rather excitedly, especially since I'd heard about it's batch convert features. That;s the problem, I navigate to TOOLS and then batch tools, and the sub menu doesn't display, some small poor excuse for a menu is present. I noticed this in other programs too, one of the menus in Krita was broken and somewhere else. I have the .7 digikam off the breezy repos with the plugins. I even installed a version .8 from an external source, but it has the same problem. It's hard to explain so i put a little picture of the problem in here. If anyone has seen this before or knows how to fix it I would be grateful in the extreme.
[IMG]http://www.wheresgabe.frih.net/images/snapshot1.gif[/IMG]

---

### Post by tagg3rx on 2006-02-16
Hurm I just installed Digicam from Synaptic and the menus work fine for me

I just searcked synaptic for digicam and installed all 3 items it found
digikam
digikamimageplugins
kipi-plugins

personaly i just go about installing what ever grabs my fancy.  It always makes it easier to figure out out to fix something if your the one who broke it.

---

### Post by bailout on 2006-02-16
I have the same thing. I had assumed that the menu was empty. Perhaps it needs a certain plugin or batch operation created before it can show anything.

Unfortunately I tried updating to the latest 0.8 release and now digikam won't start at all.

---

### Post by sniffass on 2006-02-16
[QUOTE=tagg3rx]Hurm I just installed Digicam from Synaptic and the menus work fine for me

I just searcked synaptic for digicam and installed all 3 items it found
digikam
digikamimageplugins
kipi-plugins

personaly i just go about installing what ever grabs my fancy.  It always makes it easier to figure out out to fix something if your the one who broke it.[/QUOTE]


well problem solved! It seems it needed kipi-plugins to be installed. I mean how the hell am i supposed to know that in addition to searching the repos for digikam i also need to hunt down kipi-plugins to get all the features.

Well thanks a lot for the point - case closed!

---

