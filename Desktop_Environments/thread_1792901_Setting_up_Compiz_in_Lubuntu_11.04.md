---
title: "Setting up Compiz in Lubuntu 11.04"
date: 2011-06-28
forum: Desktop Environments
---

### Post by fugazi32 on 2011-06-28
Has anyone got a walkthrough/guide on how to install & set up Compiz desktop effects in Lubuntu/LXDE? Thanks! :cool:

---

### Post by JC Cheloven on 2011-06-28
Should not be difficult, although I don't even consider running compiz in my 64bit LUbuntu system (kinda oximoron?).

Anyway, you have to install the package "compiz" from the repository.

Then add it to your startup applications by editting /etc/xdg/lxsession/Lubuntu/autostart and adding this line to the bottom:
```
@compiz --replace
```

Reboot, and it should be working. 

Note: there are [some threads]("http://ubuntuforums.org/showthread.php?t=1576889") on the subject. If you do a search you may find the answers more quickly. The [ubuntu contributed documentation]("https://help.ubuntu.com/community/CompositeManager/CompizFusion") is also an excellent source of info.

EDIT: and for setting up compiz, install compizconfig-setting-manager.

---

### Post by travlemon on 2011-06-28
> **fugazi32 said:**
> Has anyone got a walkthrough/guide on how to install & set up Compiz desktop effects in Lubuntu/LXDE? Thanks! :cool:


Hello, the easiest way I found to set up Compiz in Lubuntu is to install the package fusion-icon for config purposes.  Run fusion-icon, right click the icon in the taskbar and set Compiz as your window manager, then set GTK as your decorator.

Then, you just need to make Compiz the default window manager.  While the easy way would be to add **compiz --replace** or **fusion-icon** to autostart, I created a video of how to do it so all new users have it as default automatically.

Here's the video, if you're interested:

Part 1 of 2:  [http://www.youtube.com/watch?v=7PRXBOV7Fqs](http://www.youtube.com/watch?v=7PRXBOV7Fqs)
Part 2 of 2:  [http://www.youtube.com/watch?v=tuxv3FtgqBw](http://www.youtube.com/watch?v=tuxv3FtgqBw)

---

