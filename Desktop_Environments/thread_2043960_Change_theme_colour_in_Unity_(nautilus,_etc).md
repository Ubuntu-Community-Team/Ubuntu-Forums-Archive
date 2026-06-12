---
title: "Change theme colour in Unity (nautilus, etc)"
date: 2012-08-17
forum: Desktop Environments
---

### Post by Cammy on 2012-08-17
When Unity came out I had a hard time with it, so I tried a few other desktop managers.  Unfortunately, I had some for of buggyness or another with each of them, so I'm back to give Unity a more fair of a shake.

I've gotten pretty much everything the way I want it, except for the desktop theme, and even that is pretty close.  The only thing I haven't been able to do is to apply a dark theme to the backgrounds of things like dialog boxes, nautilus, etc.

In Gnome there was something called "shell theme" that doesn't seem to exist in Unity.  Is there something similar, or do I have to go digging around in code somewhere to do it?

---

### Post by w201 on 2012-08-17
Have you tried compiz and ununtu tweak?

---

### Post by Cammy on 2012-08-17
> **w201 said:**
> Have you tried compiz and ununtu tweak?

I have compiz installed, and I have something called "tweak tool".  The latter has a "theme" section where I've chosen things like Window theme (titlebars), cursor theme, icon theme, GTK+ theme (which seems to theme the controls, buttons, etc) and finally "shell theme" which is not selectable.

I'm assuming that last one is what controls the things I want to change.

---

### Post by vasa1 on 2012-08-17
> **Cammy said:**
> I have compiz installed, and I have something called "tweak tool".  The latter has a "theme" section where I've chosen things like Window theme (titlebars), cursor theme, icon theme, GTK+ theme (which seems to theme the controls, buttons, etc) and finally "shell theme" which is not selectable.

I'm assuming that last one is what controls the things I want to change.

Don't use it but I think you may have to first install the appropriate "Gnome extensions" to get some options available in "Shell theme".

---

### Post by Cammy on 2012-08-17
Thanks.  I have those installed, but they don't seem to have much of an effect.

---

### Post by Frogs Hair on 2012-08-18
Gnome shell extensions and shell theme won't appear in Unity, but you should be able to change themes from Advanced Settings AKA Gnome Tweak Tool. If you want more themes see the link. [http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167) The Gnome Shell is in the software center if you want to install it.

---

### Post by lolpenguin on 2012-08-19
You will need the change the GTK theme. You will need to know CSS and some general GTK knowledge.
The themes are in /usr/share/themes/.
Copy a theme to ~/.themes/ (create the folder). Change the name, and mess around with gtk-widgets.css.
But you probably don't want to break things, so go to [GNOME Look]("http://www.gnome-look.org/") and have a look at some of the great GTK 3.x themes there. MAKE SURE IT IS GTK 3.X, or you will get some ugly applications.

---

### Post by Cammy on 2012-08-19
Aha! Solved, accidentally.

When I chose a new theme in the gnome tweak tool, the gnome tweak tool dialog box wasn't changing.  It turns out that I had to close out of the tweak tool to get the colours to apply.

So I'm in business, oddly enough.

---

