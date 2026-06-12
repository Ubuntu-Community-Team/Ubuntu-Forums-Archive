---
title: "How to install a tar.gz theme?"
date: 2013-11-14
forum: Desktop Environments
---

### Post by blake4 on 2013-11-14
I'm trying to install [http://gnome-look.org/content/show.php/Teds+Grey+TRON+Scheme?content=150416](http://gnome-look.org/content/show.php/Teds+Grey+TRON+Scheme?content=150416). I have a .themes folder in my Home folder, and Drag N' Drop doesn't work in Settings, like people have said on other threads. How do I install this theme?

---

### Post by oldos2er on 2013-11-14
Moved to Desktop Environments.

---

### Post by Frogs Hair on 2013-11-14
Install Themes or Icons 


Downoload the correct GTK theme version for your Ubuntu release. 


12.04 (GTK 3.4) 12.10-13.04 (GTK 3.6)13.10 (GTK 3.8)


Fully extract the theme packages and hold the folders on the desktop until needed . (Right Click Package > Extract Here) 


Install the Gnome, Tweak Tool , Unity Tweak Tool, or Ubuntu Tweak. 


(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in the Nautilus file browser.


(All Users) Use gksudo nautilus in the terminal to open the Nautilus as root and navigate to > File System or Computer / usr / share / themes or icons .


Move theme folders into desired loaction.


Use the tweak tool/s to make theme and icon selections.

---

### Post by stinkeye on 2013-11-14
Another way to add themes is to add the noobslab theme ppa.
```
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update

```

The ppa contains some of the better themes from gnome-look.
You can browse the ppa in the software center by selecting it from  the **All Software** dropdown.
Select "more info" for a particular theme which will show a gnome-look
or deviantart address you can copy to view pics in your web browser.

---

