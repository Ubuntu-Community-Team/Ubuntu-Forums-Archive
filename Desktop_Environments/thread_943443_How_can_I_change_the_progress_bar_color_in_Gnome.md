---
title: "How can I change the progress bar color in Gnome?"
date: 2008-10-10
forum: Desktop Environments
---

### Post by DaneM on 2008-10-10
Hello, all.

I've been using Linux for years, and I've never really noticed this, but try as I might, I simply can't find any way to change the color of the progress bar in Gnome without applying a whole new theme.  The progress bar(s) I'm talking about is the one that comes up whenever Synaptic is installing something, a file is being copied/transferred, etc.  Orange is nice and all, but everything else on my desktop doesn't matches it.

BTW, I'm using the emerald theme manager, if that matters.  I've also tried looking in Preferences > Appearance, and customizing stuff there, but nothing I've tried seems to work.  I can't even find any color in the various customization options that matches the current progress bar color.  I'm a little embarrassed about this; what command-line junkie can't manage a GUI decently??  :confused:

Any hints would be great!

Thanks.

--Dane

---

### Post by gummo on 2008-11-05
I am looking to do the exact same thing without any succes so far. So any help would still be much appreciated.

---

### Post by Scott M. Sanders on 2009-05-10
I wanna do something similar. In fact, I have two Ubuntu 9s installed with almost identical themes, except my desktop computer has a theme I call "Glossy Human" (blue/orange) and my server has just a base GUI with the default "Human" theme (orange), and yet my server's progress bars animate, but my desktop computer's progress bars do not, though it has Compiz (desktop effects) on "extra." How odd is that?

---

### Post by Scott M. Sanders on 2009-05-14
It seems that the controls are simply "hard-coded" images, static and/or animated, such that if you wanted to modify the display of the progress bars (or other controls like buttons or checkboxes), it would amount to creating and somehow registering a new "control" and the images for such (using another control's images and code as a template or creating them anew).

---

### Post by oldos2er on 2009-05-14
If you're using a theme that can be customized, click System, Preferences, Appearance, Customize, Colors, Selected Items, background color.

 If this doesn't work for you, try the package gnome-color-chooser.

---

### Post by days_of_ruin on 2009-05-14
> **Scott M. Sanders said:**
> I wanna do something similar. In fact, I have two Ubuntu 9s installed with almost identical themes, except my desktop computer has a theme I call "Glossy Human" (blue/orange) and my server has just a base GUI with the default "Human" theme (orange), and yet my server's progress bars animate, but my desktop computer's progress bars do not, though it has Compiz (desktop effects) on "extra." How odd is that?

The theme you are using decides whether or not you have animated progress
bars. Compiz is not related.

---

### Post by urosg3 on 2009-05-15
Install Gnome color chooser, from Synaptic, its really easy an intelligent[IMG]http://img190.imageshack.us/img190/908/screenshotgnomecolorcho.png[/IMG]

---

