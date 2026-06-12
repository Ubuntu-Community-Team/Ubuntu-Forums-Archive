---
title: "Differences between Gnome and KDE"
date: 2012-10-22
forum: Desktop Environments
---

### Post by Gramzivi on 2012-10-22
What are differences between Gnome and KDE. But i don't think on graphic differences.
I think first of all the background things like compiling method, structure, building, etc.

I heard that GNOME is written in many strange OO C, while KDE is written in C + +, or that KDE has become more centralized.

---

### Post by BaardKopperud on 2012-10-22
The most important difference is that GNOME uses the GNOME-library - an extension of the GTK+-library, while KDE uses the KDE-library - an extension of the Qt-library (now by Nokia).  

GTK is a library written in and for C, while Qt is written in and for C++.

KDE has it's own windowmanager (the program that draws the re-sizable frame around windows, with titlebar and close, minimize, maximize/restore-buttons, while GNOME uses some 3rd-party (preferably) GTK+-aware windowmanager.  

There isn't a default or recommended wm for GNOME, but it's pre-configured for using a suitable one (which few users changes).  These have been - depending on GNOME-version - the Enlightenment, Sawfish and Metacity windowmanagers.  This can cause problems if you also want to use the wm as stand-alone, as some parts (like background image, task-bar and virtual desktop-switching) may be handled by both the wm and GNOME, so you must either live with having it double-up in GNOME (e.g. two taskbars, one from GNOME and one from the wm) or missing it completely when you run the wm as stand-alone (without GNOME).

As you've noted, the different parts/applications are more tightly integrated and looks more alike in KDE than i GNOME.  GNOME is still more a collection of separate applications than a more integrated set, and uses more "3rd-party"/"non-GNOME" parts - like Evolution like the "standard" mail-application.

---

### Post by Gramzivi on 2012-10-22
> **BaardKopperud said:**
> The most important difference is that GNOME uses the GNOME-library - an extension of the GTK+-library, while KDE uses the KDE-library - an extension of the Qt-library (now by Nokia).  

GTK is a library written in and for C, while Qt is written in and for C++.

KDE has it's own windowmanager (the program that draws the re-sizable frame around windows, with titlebar and close, minimize, maximize/restore-buttons, while GNOME uses some 3rd-party (preferably) GTK+-aware windowmanager.  

There isn't a default or recommended wm for GNOME, but it's pre-configured for using a suitable one (which few users changes).  These have been - depending on GNOME-version - the Enlightenment, Sawfish and Metacity windowmanagers.  This can cause problems if you also want to use the wm as stand-alone, as some parts (like background image, task-bar and virtual desktop-switching) may be handled by both the wm and GNOME, so you must either live with having it double-up in GNOME (e.g. two taskbars, one from GNOME and one from the wm) or missing it completely when you run the wm as stand-alone (without GNOME).

As you've noted, the different parts/applications are more tightly integrated and looks more alike in KDE than i GNOME.  GNOME is still more a collection of separate applications than a more integrated set, and uses more "3rd-party"/"non-GNOME" parts - like Evolution like the "standard" mail-application.


thats the answer i wanted
thank you very much

---

### Post by jerrrys on 2012-10-22
> **BaardKopperud said:**
> There isn't a default or recommended wm for GNOME, but it's pre-configured for using a suitable one (which few users changes).  These have been - depending on GNOME-version - the Enlightenment, Sawfish and Metacity windowmanagers.  This can cause problems if you also want to use the wm as stand-alone, as some parts (like background image, task-bar and virtual desktop-switching) may be handled by both the wm and GNOME, so you must either live with having it double-up in GNOME (e.g. two taskbars, one from GNOME and one from the wm) or missing it completely when you run the wm as stand-alone (without GNOME).

As you've noted, the different parts/applications are more tightly integrated and looks more alike in KDE than i GNOME.  GNOME is still more a collection of separate applications than a more integrated set, and uses more "3rd-party"/"non-GNOME" parts - like Evolution like the "standard" mail-application.

No default WM for Gnome?  Do you really know that to be a fact.  I don't.  Metacity is default window manger for Gnome Classic and Mutter is default window manager for Gnome-shell.

Use WM as a stand-alone?  A stand-alone to what.  Come on now ..

Double up in Gnome?  No such thing that I know of.  How bout some links to back some of this up ..

3rd party/non-gnome.  Evolution?

[http://packages.ubuntu.com/precise/metacity](http://packages.ubuntu.com/precise/metacity)

[http://packages.ubuntu.com/precise/mutter](http://packages.ubuntu.com/precise/mutter)

[http://packages.ubuntu.com/precise/evolution](http://packages.ubuntu.com/precise/evolution)

---

### Post by Mr.JJ on 2012-10-23
> **BaardKopperud said:**
> As you've noted, the different parts/applications are more tightly integrated and looks more alike in KDE than i GNOME.  GNOME is still more a collection of separate applications than a more integrated set

 In addition to what jerrrys said, GNOME 3 is fast moving towards a coherent titghtly integrated desktop. With all the newly designed default applications, and GDM, systemd, ibus etc. it becomes more and more closely integrated.

---

### Post by qamelian on 2012-10-23
> **jerrrys said:**
> No default WM for Gnome?  Do you really know that to be a fact.  I don't.  Metacity is default window manger for Gnome Classic and Mutter is default window manager for Gnome-shell.

Use WM as a stand-alone?  A stand-alone to what.  Come on now ..

Simply as a standalone environment. Most window managers I have used can actually be run on their own to provide a GUI, instead of as part of a larger "desktop environment". For example, Sawfish used to be the default WM for Gnome before Metacity, but Sawfish can be run all on its own to provide a lightweight (in comparison to a full DE) GUI experience. The same holds of Compiz and many others, like Openbox.

---

### Post by BaardKopperud on 2012-10-24
> **jerrrys said:**
> No default WM for Gnome?  Do you really know that to be a fact.  I don't.  Metacity is default window manger for Gnome Classic and Mutter is default window manager for Gnome-shell.

It may have changed now, but previously - i believe even in the GNOME config-files - it was made a point of that the set-up with a particular WM should not be considered "the default" or "the standard" WM, but rather as "an example" - and they've used quite a few different WMs together with GNOME through the years.  Of course, most users leaves the configuration alone, and doesn't change the WM.  My point was that it's more of an "example set-up" than "the default".  Possibly ithat's changed now that GNOME has gotten a WM that's part of the project (Metacity).

> Use WM as a stand-alone?  A stand-alone to what.  Come on now ..

As a stand-alone Window Manager - i.e. without using a Desktop Environment like GNOME, KDE or xfce.  A WM just draws the "window", but often has a bit more - like taskbar.  A DE on the other hand, is typically much more complex and comes with a collection of "standardized" applications. 

icewm, metacity, afterstep, fvwm, wmaker, enlightenment and twm (to name a few) are all just window managers, and can be used alone... Or they can (more or less successfully) be used together with GNOME, where it just draws the actual windows.

> Double up in Gnome?  No such thing that I know of.  How bout some links to back some of this up ..


My point was that since many of these WMs also have their own taskbars, virtual-desktop swappers and backgroundimage, it may be difficult to configure them to be both able to work alone and with GNOME with the same configuration.  E.g. if you use fvwm2 it defaults to make icons of minimized windows.  If you use it with GNOME, you typically disable the icons and use the GNOME-taskbar instead.  But if you then run fvwm2 as standalone (same config, but without GNOME), you suddenly have neither icons nor a taskbar to retrieve minimized windows from.  Or you can leave the icons on, though that is surplus together with the GNOME-taskbar.  Another example is where both GNOME and the WM tries to set the background image, and you background therefore suddenly changes when you shift to another desktop or similar (because the other program suddenly gets to set the background).  This was a problem while Enlightenment was used as GNOME's WM, since Enlightenment had it's own themes and backgrounds too.

> 
3rd party/non-gnome.  Evolution?


Yes, admittedly not the best example as it was incorporated into GNOME a long time ago...  However it started out as a stand-alone program made by Ximian, and at first certainly didn't look much GNOMEish.

With 3rd party I didn't mean commercial or non-Linux, I meant non-GNOME - like the Enlightenment and Sawfish WindowManagers; which was used as an integrated part of GNOME, while not being part of the GNOME-project.

---

