---
title: "Connection to Firefox"
date: 2010-01-15
forum: Desktop Environments
---

### Post by OldAlgis on 2010-01-15
Hi All!

I want to move my working to Karmic Coala kubuntu (9.10).  KDE is rather nice with the plasmoids, but I have a problem with Firefox. When I click on the Firefox icon, it comes with an installation screen.  When I respond by clicking on that screen a button labelled "Install", it tells me that it is already installed...  I can start Firefox from CLI ok, but would like to be able to have the usual "click icon" access.

Any ideas?  I guess, I could install a "link to application" on the plasmoid, but surely the menu should work, too.

---

### Post by kellemes on 2010-01-15
> **OldAlgis said:**
> Hi All!

I want to move my working to Karmic Coala kubuntu (9.10).  KDE is rather nice with the plasmoids, but I have a problem with Firefox. When I click on the Firefox icon, it comes with an installation screen.  When I respond by clicking on that screen a button labelled "Install", it tells me that it is already installed...  I can start Firefox from CLI ok, but would like to be able to have the usual "click icon" access.

Any ideas?  I guess, I could install a "link to application" on the plasmoid, but surely the menu should work, too.

If it's the icon from the menu.. use the menueditor to change the command. (right click application launcher)
If it's the icon from the panel.. right click the icon and change the icon settings etc..

---

### Post by nerdy_kid on 2010-01-15
i think you are clicking the firefox installer. 
```

sudo apt-get remove kubuntu-firefox-installer  && sudo apt-get install firefox

```
should fix it.

---

### Post by OldAlgis on 2010-01-21
> **nerdy_kid said:**
> i think you are clicking the firefox installer. 
```

sudo apt-get remove kubuntu-firefox-installer  && sudo apt-get install firefox

```
should fix it.

Correct on both counts! The Firefox menu entry was pointing persistently to the  the kubuntu-firefox-installer. Clearly, the link was supposed to be auto-changed to kubuntu-firefox, as it did for me in other kubuntu karmic installations, but it failed to do so and I did not twig to the apt-get commands.  Thanks a lot for pointing it out to me!  

It all works OK now - no more (compalsory) starting of firefox from CLI!

---

