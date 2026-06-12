---
title: "no top window bar in kde"
date: 2010-03-12
forum: Desktop Environments
---

### Post by catlover2 on 2010-03-12
i cannot find a way to turn on the bar at the top of the window,
the one with the _ and x on it

thanks!

---

### Post by catlover2 on 2010-03-14
bump

---

### Post by petersohn on 2010-03-14
In System Settings, under Appearance (or Desktop?) there is a tab called Window Decoration. Try selecting something from there.

Sorry I don't have my Kubuntu machine nearby, so I can't be more exact.

---

### Post by lykwydchykyn on 2010-03-14
Are the windows movable?  If you alt-click on a window and drag will the window move, or are they all stuck in place?

I ask because it sounds like kwin is not running (kwin draws that top bar).

Also, is there any history on this issue?  Is this a new install? have you configured anything?  Is this Kubuntu or KDE installed over some other flavor of ubuntu?

---

### Post by catlover2 on 2010-03-15
i cannot seem to find appereance (or desktop) in system,

i am running kde from ubuntu, BUT ever since i got xfce it says xubuntu!?

no the windows are not alt-click movable.

i have had this install for 2-3 weeks and i noticed this the first time i tried 
kde (a few days ago)...

thanks for the reply!

---

### Post by l4zy on 2010-03-15
Have you configure compiz or some other window manager ?

---

### Post by kellemes on 2010-03-15
Menu -> Settings -> System Settings -> Default Applications ->  Window Manager -> "Use the default KDE Window Manager (KWin)"

---

### Post by lykwydchykyn on 2010-03-15
> **catlover2 said:**
> i cannot seem to find appereance (or desktop) in system,

i am running kde from ubuntu, BUT ever since i got xfce it says xubuntu!?

no the windows are not alt-click movable.

i have had this install for 2-3 weeks and i noticed this the first time i tried 
kde (a few days ago)...

thanks for the reply!

Sounds like no window manager is running.  If the above suggestion doesn't fix it, try opening konsole and running "kwin" in the konsole.  Paste the output here.

---

### Post by catlover2 on 2010-03-15
i ran kwin and it told me that it wasn't installed,
but it told me the code to install it and now im happily kde-ing
away, with a top bar of course!

---

### Post by lykwydchykyn on 2010-03-15
> **catlover2 said:**
> i ran kwin and it told me that it wasn't installed,
but it told me the code to install it and now im happily kde-ing
away, with a top bar of course!

That's very odd; how exactly did you install KDE to begin with?  If you were missing kwin, I would imagine other important components are also missing.

---

### Post by catlover2 on 2010-03-15
kde came in the ubuntu 9.10 install .iso as far as i know.

---

### Post by craetech on 2010-03-22
It is also beyond my understanding that it seems kwin is no longer used in KDE 4.3 but rather a kde-window-manager. According to kwin package description in KPackageKit, kwin is now a "dummy" package. Not sure how that works. Furthermore, my Kubuntu Karmic did not come with kwin installed (to my surprise, "apt-get install kwin" is a new installation!).

Would love some enlightenment. :)

---

### Post by lykwydchykyn on 2010-03-22
> **craetech said:**
> It is also beyond my understanding that it seems kwin is no longer used in KDE 4.3 but rather a kde-window-manager. According to kwin package description in KPackageKit, kwin is now a "dummy" package. Not sure how that works. Furthermore, my Kubuntu Karmic did not come with kwin installed (to my surprise, "apt-get install kwin" is a new installation!).

Would love some enlightenment. :)

Apparently, for whatever reason, they put kwin in a package called "kde-window-manager".  It still installs kwin (the program, not the package).

Installing the "kwin" package will also install kwin, because even though it is a dummy package it still depends on kde-window-manager and would install it if missing.

---

### Post by kellemes on 2010-03-22
> **lykwydchykyn said:**
> apparently, for whatever reason, they put kwin in a package called "kde-window-manager".  It still installs kwin (the program, not the package).

Installing the "kwin" package will also install kwin, because even though it is a dummy package it still depends on kde-window-manager and would install it if missing.

+1

Just a little confusing I guess..

---

### Post by craetech on 2010-03-23
> **lykwydchykyn said:**
> Apparently, for whatever reason, they put kwin in a package called "kde-window-manager".  It still installs kwin (the program, not the package).

Installing the "kwin" package will also install kwin, because even though it is a dummy package it still depends on kde-window-manager and would install it if missing.
+1

Thanks, lykwydchykyn! :)

---

