---
title: "firefox goes fugly after gtk-qt-engine install"
date: 2008-09-15
forum: Desktop Environments
---

### Post by dijxtra on 2008-09-15
I run vanilla Ubuntu 8.04 with KDE 3.5 on top of it and today Adept Updater installed gtk-qt-engine. I didn't spare time to read about what that package is (who does that anyway?) so now my firefox is fugly, and leafpad and gajim too. Should I configure gtk-qt-engine after it is installed? Or do I need it at all, can I just delete it and live without it? What do I need it for anyway?

---

### Post by Daisuke_Aramaki on 2008-09-15
ur rite! :( i just replaced the new version with the old one and the settings are back. the gtk style configurator in KDE Control Center also disappeared after the new version install.

---

### Post by Daisuke_Aramaki on 2008-09-15
my bad! the new version clearly states in the desciption that its directed at kde4 users! so i didn't rtfm properly!

---

### Post by dijxtra on 2008-09-15
> **Daisuke_Aramaki said:**
> my bad! the new version clearly states in the desciption that its directed at kde4 users! so i didn't rtfm properly!
Well, apart from gtk-qt-engine, Adept installed gtk-qt-engine-kde4 also. I suppose gtk-qt-engine is for kde3 then, right?

BTW, yes, I have both KDE 3.5 and KDE 4.1 installed on my system. Could there be a collision of some kind?

---

### Post by Daisuke_Aramaki on 2008-09-15
> **dijxtra said:**
> Well, apart from gtk-qt-engine, Adept installed gtk-qt-engine-kde4 also. I suppose gtk-qt-engine is for kde3 then, right?

BTW, yes, I have both KDE 3.5 and KDE 4.1 installed on my system. Could there be a collision of some kind?

kde4 thing that adept installed is just a transitional package, which is not needed once the engine is installed. the gtk-qt-engine is the real deal!

---

### Post by baruch60610 on 2008-09-15
I had the same thing happen, but I can't say that it was related to gtk-qt-engine.  As far as I recall, I had that already installed.

However, I *was* adding some other gtk engines.  When I restarted Firefox, it was indeed fugly beyond all reason.  Mostly it looked as though all my spaces were tabs, three, four, maybe even five character widths in every space.

I tried uninstalling FF and removing every hint of a config file, which did nothing.

I haven't yet found a way to fix it.  I'd love to hear any hints from someone who figured out how to make it all better.

---

### Post by Daisuke_Aramaki on 2008-09-15
> **baruch60610 said:**
> I had the same thing happen, but I can't say that it was related to gtk-qt-engine.  As far as I recall, I had that already installed.

However, I *was* adding some other gtk engines.  When I restarted Firefox, it was indeed fugly beyond all reason.  Mostly it looked as though all my spaces were tabs, three, four, maybe even five character widths in every space.

I tried uninstalling FF and removing every hint of a config file, which did nothing.

I haven't yet found a way to fix it.  I'd love to hear any hints from someone who figured out how to make it all better.

ur rite! i had the engine already installed as well. but adept updated it with the new package and thats when the screwup began. but after having had a closer look at it, it was very clear that this update was meant for kde4.1, and since the qt engine i had previously was also qt4, maybe it was upgraded! assuming ur in kde3.5 and its variants, its simple to reset the update!

open synaptic and search for gtk-qt-engine. u will get the newly installed package. mark it and goto Package->Force Version, and choose the older one and install. everything shud be back to normal again.

---

### Post by dijxtra on 2008-09-15
> **Daisuke_Aramaki said:**
> open synaptic and search for gtk-qt-engine. u will get the newly installed package. mark it and goto Package->Force Version, and choose the older one and install. everything shud be back to normal again.
Yup, that fixed it. That package was downloaded from ppa.launchpad.net which I put to my list of repositories when KDE 4.1 got out. Now that I removed that repository from my list, will my KDE 4.1 installation still get updated? Is KDE 4.1 now in official ubuntu repositories?

---

### Post by Giant Speck on 2008-09-15
So, wait.  How am I supposed to change my GTK Styles & Fonts settings now that it's been removed from the Control Center?

---

