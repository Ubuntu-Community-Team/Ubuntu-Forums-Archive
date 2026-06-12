---
title: "Java Apps look Different between KDE/Gnome"
date: 2005-11-23
forum: Desktop Environments
---

### Post by Dromio on 2005-11-23
I regularly use a couple of java applications.  I've noticed that the interface looks very different when they are run from KDE than when they were run from Gnome.  In Gnome, they look flat and simple.  But from KDE, the widgets have gradients and rounded corners.  

Neither looks anything like the GTK or QT themes, they are their own themes.  I know that java (swing?) has its own theming, I just wonder why it's using a different theme for each environment.

---

### Post by the_it on 2005-11-23
As I recall, Java doesn't directly implement the window manager, but rather makes requests to the window manager to make windows.  It is only natural that Java looks different not just in KDE/Gnome, but also in windows.

---

### Post by f1dave on 2005-11-24
It surely does. Recently, I created a java application in JDK 1.5, and was amazed to see the difference in the look of the app between windows, gnome, kde, etc. If I'd known, I would have used images or something to make a more "uniform" look.

---

### Post by vitorsouza on 2005-11-24
Java has the concept of "Look & Feel". The programmer can set the L&F or leave it to the default. Maybe the default in KDE is different than the default in GNOME. But when you upgraded your system and replaced GNOME with KDE, maybe you also installed Java 5 instead of 1.4, and that also installs new and updated L&Fs. As I recall, Java has only one L&F for Linux, and it's GTK-looking. I don't know if that's changed for Java 5.

---

### Post by Dromio on 2005-11-24
It's definately a different look and feel, and it'd not that the window manager is handling the widgets.  The widgets look nothing like widgets for non-java apps.

I have both KDE and Gnome installed at the same time.  If I login to a Gnome session, java apps look one way.  If I login to a KDE session, they look different.  I'm sure there's a setting somewhere that tells java apps what look and feel to use-- I just can't figure out where it is.

It probably doesn't matter, but I've got a problem with drag+drop using a java app under KDE that doesn't happen in Gnome.  I'd like to get the look and feel the same under both so I can rule that out.

---

