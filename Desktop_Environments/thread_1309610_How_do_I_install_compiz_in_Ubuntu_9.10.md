---
title: "How do I install compiz in Ubuntu 9.10?"
date: 2009-11-01
forum: Desktop Environments
---

### Post by biran1229 on 2009-11-01
I'm new to ubuntu and can not figure out how to install compiz, and get it to work. So if anyone can help by sending me easy-to-follow instructions it would be great.

---

### Post by Dave33 on 2009-11-01
Hi

You should use the search engine.

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

or just install compizconfig-settings-manager from synaptic and you can enabe the effects from there.

Dave33

---

### Post by screaminj3sus on 2009-11-01
Compiz is installed by default.... Go to system > Prerferences > Visual effects and select normal or extra and it will be enabled if your video card supports it and has the correct drivers installed.

What video card do you have? If you have a supported video card with the right drivers installed it usually enables compiz automatically.

---

### Post by imwithid on 2010-01-22
> **screaminj3sus said:**
> Compiz is installed by default.... Go to system > Prerferences > Visual effects and select normal or extra and it will be enabled if your video card supports it and has the correct drivers installed.

What video card do you have? If you have a supported video card with the right drivers installed it usually enables compiz automatically.


Thank you! I've been wondering why I couldn't zoom into the screen ever since 9.04 (it seems as though the visual effects are now defaulted to "None" rather than "Normal"). I no longer have to lean into the screen! This has been driving me crazy but I hadn't bothered to look it up until now.

---

### Post by Compizhowdoiinstall on 2010-06-21
C'mon please give me a link to the installer for compiz fusion!!!

---

### Post by steveneddy on 2010-06-21
> **Compizhowdoiinstall said:**
> C'mon please give me a link to the installer for compiz fusion!!!

Compiz is installed by default. 

If your video card will support the effects it will be running.

Right click the desktop, select 

**Change Desktop Background**

Click the

**Visual Effects**

tab at the top and see which radio button is selected.

If it is on **None**, you will have no visual effects, so you should try the **Normal** button and see what happens.

For more control install Compiz Config Settings Manager by opening up a terminal and copy and pasting this into the terminal:

```
sudo apt-get install compizconfig-settings-manager
```

You will find it after installation under

System --> Preferences

I hope this helps.

---

### Post by steveneddy on 2010-06-22
> **Compizhowdoiinstall said:**
> C'mon please give me a link to the installer for compiz fusion!!!

Another thought ***Compizhowdoiinstall*** - 

Open up Synaptic Package Manager and simply click in the main window and start typing **compiz**

it should take you automatically to all of the compiz stuff - just right click and select install - then up top there is a green arrow that says **Apply**

simply click to apply your choices.

Uninstalling software is just as easy.

---

