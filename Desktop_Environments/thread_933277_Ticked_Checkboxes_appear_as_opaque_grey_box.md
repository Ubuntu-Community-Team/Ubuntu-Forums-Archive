---
title: "Ticked Checkboxes appear as opaque grey box"
date: 2008-09-29
forum: Desktop Environments
---

### Post by carpii on 2008-09-29
I have a problem with my KDE 3.5.9 Desktop. (Kubuntu 8.04)

Whenever i tick a checkbox, instead of showing it ticked, it appears as an opaque grey box. This is also true for radio buttons

When they are unticked they look fine
Also when they are ticked but not focused, they are fine too

Its only when I focus a ticked control (or go to tick one) that it appears badly

I wonder if maybe I have a corrupt theme, or is this some other problem. Pelase help as its driving me crazy :(

---

### Post by carpii on 2008-11-13
Sorry to bump this

Can anyone else at least confirm they are having the same problem, even if you dont know how to fix it?

Thanks

---

### Post by smilingfrog on 2009-01-15
I'm having the same problem. I have noticed it more with gnome interfaces in KDE rather than with native KDE applications. For instance, the check boxes and radio boxes are opaque in Firefox, but not in Konqueror. 
I have noticed it with the minesweeper game, and using the system monitor.
Most annoying is with firefox. I haven't found a workaround yet.

---

### Post by smilingfrog on 2009-01-15
I found a fix here [http://blog.larsneumann.net/2008/09/firefox-3-annoying-shade-on-checkboxes-and-radio-buttons/](http://blog.larsneumann.net/2008/09/firefox-3-annoying-shade-on-checkboxes-and-radio-buttons/)

> The fix that worked for me is to install the package “gtk2-engine-qtcurve”, then open kcontrol and go to Appearance -> GTK Styles and change the GTK Styles to “QtCurve”.

Restart firefox and it should work.
G

---

### Post by carpii on 2009-01-16
Thanks for the tip. However Im struggling to install it...

~> sudo apt-get install gtk2-engine-qtcurve
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gtk2-engine-qtcurve

Is it something I need to download from elsewhere ?
Also can you confirm youre on KDE 3.5 rather than KDE 4.x  

Thanks

---

### Post by carpii on 2009-01-16
Got it. I should have searched synaptic first 

Incase anyone else has same problem, the package is called gtk2-engines-qtcurve  (note the S in engines)

Thanks so much, works a treat. Feels like a breath of fresh air not to have this problem anymore :))

---

