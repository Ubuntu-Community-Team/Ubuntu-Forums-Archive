---
title: "My desktop environment is missing a chromosome: Someone help."
date: 2007-10-28
forum: Desktop Environments
---

### Post by BnetTheAwesome on 2007-10-28
My desktop is lacking direct rendering and I need help. I had someone look at it and they concurred it was a driver problem. I've talked about this in other threads. (Mainly this post: [http://ubuntuforums.org/showpost.php?p=3618637&postcount=22](http://ubuntuforums.org/showpost.php?p=3618637&postcount=22))

Since no-one responded I guess me and my ATI 9100 U3 graphics card with the default "ati" driver will have to leave and shotgun Hector Ruiz right between the eyes for not making their drivers open source. Someone please help. I WANT DIRECT RENDERING BACK! And blender won't work for me. Someone help.

---

### Post by athaki on 2007-10-29
> **BnetTheAwesome said:**
> My desktop is lacking direct rendering and I need help. I had someone look at it and they concurred it was a driver problem. I've talked about this in other threads. (Mainly this post: [http://ubuntuforums.org/showpost.php?p=3618637&postcount=22](http://ubuntuforums.org/showpost.php?p=3618637&postcount=22))

Since no-one responded I guess me and my ATI 9100 U3 graphics card with the default "ati" driver will have to leave and shotgun Hector Ruiz right between the eyes for not making their drivers open source. Someone please help. I WANT DIRECT RENDERING BACK! And blender won't work for me. Someone help.

Well to answer some of your definition questions from your other thread 

GRUB- bootloader for many linux operating systems

BIOS - basic input/output system (I believe)

X server - the Graphical User Interface for many Linux operating systems

Xorg.Conf - file that contains your video and other hardware configuration

cp - depends could mean control panel or anything else (sorry, not much help there)

Now for your driver problem, are you running XGL? If you are, then direct rendering is probably turned off (as it was for my mobility x300). Also, are you using the restricted driver? If you are and running XGL then you won't have direct rendering. If you can live without compiz then revert back to metacity by removing XGL 

```
 sudo apt-get remove xserver-xgl 
```

I hope this helps.

---

### Post by BnetTheAwesome on 2007-10-29
It seems your advice helped some bit but I've still got two glaring errors.

First off, Blender won't load. It just shuts down during start-up.

Secondly, every time I start up it asks me about my keyboard settings and asks whether I want GNOME or X settings. How do I make the choice permanent? Thanks also.

---

