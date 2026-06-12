---
title: "Compiz and Metacity"
date: 2009-12-21
forum: Desktop Environments
---

### Post by The Recorder on 2009-12-21
I have a few desktop environments on my machine, and wasn't using GNOME for a few weeks.  Yesterday, when I logged into GNOME, I had Compiz, but I had no window decorations - I had had Metacity running.  I tried several things, but Compiz would only give me decorations if I used Emerald.  If I used Metacity (metacity --replace), Compiz would stop running.

Has anyone else had this problem?  Is there a solution, or has Compiz reverted back to its old ways of not running with Metacity?

(Am running Ubuntu 9.10, with Compiz 0.8.4.)

Thanks much!

---

### Post by lovinglinux on 2009-12-21
I'm on KDE right now, so I can't test metacity, but [fusion-icon](apt:fusion-icon) should be able to handle this, since I can select Kwin Window Decorator with Compiz, instead of Emerald (although I use Emerald).

---

### Post by The Recorder on 2009-12-21
> **lovinglinux said:**
> I'm on KDE right now, so I can't test metacity, but [fusion-icon](apt:fusion-icon) should be able to handle this, since I can select Kwin Window Decorator with Compiz, instead of Emerald (although I use Emerald).

I have fususion-icon installed.  If I use it to switch to Metacity (or GTK-Windo-Decorator), I lose Compiz.  This is not the case with KDE.  I run KDE with its own compositor, but it will work with Compiz - I still get the KWIN window decorations.

Thanks for the suggestion...

---

### Post by konqueror7 on 2009-12-21
have you tried changing the window decorations in *fusion-icon*? there are 2 options, GTK and Emerald, you may try changing it to GTK.

if still no windows decorations, try changing the compiz options to either, *Loose Binding* or *Indirect Rendering*...see if that works out...:)

---

### Post by wojox on 2009-12-21
You can't run Metacity and Compiz. There both window managers. Turn on Visual Effects and go to System > Preferences > CompizConfig Settings Manager and look for Window Decoration and make sure it's checked.

---

### Post by The Recorder on 2009-12-21
> **wojox said:**
> You can't run Metacity and Compiz. There both window managers. Turn on Visual Effects and go to System > Preferences > CompizConfig Settings Manager and look for Window Decoration and make sure it's checked.

You couldn't do so a while back, but I was doing so since at least when Karmic came out.  Window Decorations, in CCSM, is checked.

I have to amend my above KDE statement.  KWIN will not run when I switch to Compiz (under the "System Settings". "Default Settings" section), and that had worked since Intrepid...  I'm stumped...

---

### Post by The Recorder on 2009-12-21
Solved the problem.  During the three or so weeks that I didn't use GNOME, I uninstalled "regular E17, and installed E17 ECOMORPH.  E17 ECOMORPH's Compiz was conflicting with the "regular" Compiz.  Removed E17 ECOMORPH, reinstalled "regular" E17, and then reinstalled the "regular" Compiz, and all is back to "normal"

Thank for all the help...  You kept my brain working:confused:

---

