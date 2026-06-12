---
title: "Entries in Kile Settings menu gone missing"
date: 2012-11-18
forum: Desktop Environments
---

### Post by bobo52703948 on 2012-11-18
Hi.

Kile is giving me a bit of trouble. Most of the entries in the Settings menu have vanished – most importantly, the entries for “configure Kile” and “configure shortcuts“ are gone. This was just after changing some of the fonts settings in Kile; everything worked after a fresh install of 12.10 on a completely new system, and then with no apparent reason said entries were just gone.

The only things that remain in the Settings menu are “Define current document as master document“, “System check“, “Show side bar/messages bar” and “Toolbars shown”.

I found some other threads dealing with similar problems; in most cases the solution was simply deleting  ~/.kde/share/config/kilerc. I tried this, but no go. Another thread – [http://ubuntuforums.org/showthread.php?t=816974](http://ubuntuforums.org/showthread.php?t=816974) – was closer to my problem, but unfortunately the solution seems to be specific to KDE. 

[Edit: The problem does not exist when using Kile in another account on the same system, but that does not solve the current problem. Reinstalling Kile was no use, either.]

I’m using Gnome Shell, but Kile is simply the best editor for me; it’s a must. Can anybody help?

---

### Post by janhar4711 on 2012-11-20
Hi.

I experienced the same weird behavior. In my case the menu items went missing after changing the layout of the toolbar, e.g., removing some icons. Resetting it to the defaults by right-clicking the toolbar in question selecting "configure toolbars" and hitting the "reset to defaults" button in the lower left did the trick.

In case you can't access the toolbar config dialog anymore your problem might be solved by removing the user interface configuration file for kile, which is (in my case) located at
~/.kde4/share/apps/kile/kileui.rc

Hope that helps!

---

### Post by bobo52703948 on 2012-11-21
Yay. Resetting the toolbars did the trick.

Thank you! You are my hero.

---

### Post by nortexoid on 2013-02-05
Nice! Resetting toolbars worked for me too. Odd bug.

Has anyone filed a bug report for this?

---

