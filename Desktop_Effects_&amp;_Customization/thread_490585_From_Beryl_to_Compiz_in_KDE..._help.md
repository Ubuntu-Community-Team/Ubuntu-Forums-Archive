---
title: "From Beryl to Compiz in KDE... help?"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by bg1256 on 2007-07-02
Hi,

I've been running Beryl for just about a year, and I'd like to give Compiz a try, given the recent merge.

I am running Kubuntu Feisty, and I've installed Compiz via Adept Package Manager.  In my system tray, I can select compiz as the WM instead of Beryl or Kwin; however, I cannot locate any type of settings manager for Compiz. 

If I could find that, it would be of great help, as I cannot get window decorations working (other than default KDE), scale, or desktop cube working.

Any help is much appreciated! :D

---

### Post by eentonig on 2007-07-10
+1

---

### Post by bg1256 on 2007-07-16
A little  bump after a week...

---

### Post by simonalpha on 2007-07-16
As far as I know, there is no way to adjust Compiz in KDE using a KDE (Qt) tool.
There is Gnome Compiz Manager, which has both a config tool and a tray icon, in KDE the config tool may work, but I doubt the tray icon will.
There also used to be Compiz settings, but according to the Compiz website, the project is dead.
Gnome Compiz Manager is in the repo.

Hope this helps....

---

### Post by Happy_Man on 2007-07-16
At this point, all you can do is install Compiz Fusion. Normal compiz, which depends on gconf, won't run correctly in KDE. Compiz Fusion, however, will. I'm doing it right now. ;) 

Howto: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by bg1256 on 2007-07-24
> **Happy_Man said:**
> At this point, all you can do is install Compiz Fusion. Normal compiz, which depends on gconf, won't run correctly in KDE. Compiz Fusion, however, will. I'm doing it right now. ;) 

Howto: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

Okay, that helps me an awful lot.  I knew fusion would run, but I didn't realize compiz would not. Thanks for the heads up.

---

### Post by BDNiner on 2007-07-24
I can't get compiz fusion to run on kubuntu. I have an Nvidia FX5200. I get the error:

Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.

When i try compiz --replace

---

### Post by bg1256 on 2007-07-24
Well, if I knew anything, I'd help you.. .but sorry, I don't.

I can get Compiz running just fine, I just can't find a settings manager to allow to to configure its behavior.

---

### Post by Happy_Man on 2007-07-24
> **bg1256 said:**
> Well, if I knew anything, I'd help you.. .but sorry, I don't.

I can get Compiz running just fine, I just can't find a settings manager to allow to to configure its behavior.
That package is in Trevino's repos, under the name "compizconfig-settings-manager".

---

### Post by BDNiner on 2007-07-24
I am managed to get it working. Surprisingly a reboot fixed the issue of no window decorations. I was just restarting X, but i guess that was not enough. I also added some extra lines to the xorg.conf file. i found the info in the main sticky about getting compiz-fusion to work. It took me reading every page, that sucked.

---

