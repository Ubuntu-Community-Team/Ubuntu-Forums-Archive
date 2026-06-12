---
title: "Blurred menu icons in Clearlooks theme"
date: 2007-10-19
forum: Desktop Environments
---

### Post by MellonCollie on 2007-10-19
Are the icons in the Clearlooks theme supposed to look like this? :confused:

(OO icons)
[img]http://img135.imageshack.us/img135/4185/screenshot3xm6.png[/img]

(gthumb, OO drawing)
[img]http://img507.imageshack.us/img507/1986/screenshot4wm7.png[/img]

(Bluetooth, Hardware info, PalmOS device, Preferred apps, SCIM) 
[img]http://img246.imageshack.us/img246/1387/screenshot2xp7.png[/img]

(Keyring manager, Screens and Graphics, Software sources, Synaptic, Time and Date)
[img]http://img205.imageshack.us/img205/5341/screenshotsc2.png[/img]

---

### Post by SlackLagg on 2007-10-21
I've recently noticed this too, and I would appreciate any input.  (Also to improve on OP's screenshots, it only seems to be .png icons) 

(Although I may have just noticed this because my X settings got kinda messed up when I upgraded to 7.10 and now I'm looking at everything with a microscope to see what's broken)

---

### Post by BattlePanic on 2007-10-28
I have also noticed this problem.  I am using Gutsy 7.10 and I've only noticed this issue when I'm using the Clearlooks theme.

---

### Post by makro on 2007-10-31
same problem here

---

### Post by pete83 on 2007-10-31
This is a known issue, apparently using 24x24 icons in a 22x22 space.

There is also a known workaround:

Create a file called "~/.gtkrc-2.0" (that is, a ".gtkrc-2.0" file in your home/username folder), and put the following text in the file:
```
gtk-icon-sizes = "panel-menu=24,24"
```
Next time you select your icons or whatever, that should register and the icons should stop being blurry. At least, it worked for me.

---

