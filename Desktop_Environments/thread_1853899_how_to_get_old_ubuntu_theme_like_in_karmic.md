---
title: "how to get old ubuntu theme? like in karmic?"
date: 2011-10-03
forum: Desktop Environments
---

### Post by deskman on 2011-10-03
hi! i wonder if there is a way to make my natty narwhall look like like older ubuntu releases.. karmic koala for ex. i just like the simple brownish interface. us there something to do with it?

---

### Post by jaydensmith95 on 2011-10-03
I am  new this forum please suggest me

---

### Post by searchfgold6789 on 2011-10-03
If you're talking about getting rid of the Unity interface (with all the buttons on the side and the ubuntu logo thing) then your best bet is to run Ubuntu in Classic Mode. At the login screen, just select the login type to Ubuntu Classic instead of Ubuntu. There's a menu for it at the bottom.

---

### Post by Frogs Hair on 2011-10-03
The themes are in available in the Synaptic Package Manager or open the terminal and run the following command .```
sudo apt-get install community-themes
```

---

### Post by Frogs Hair on 2011-10-03
If you would like the 9.10 wallpapers .```
sudo apt-get install ubuntu wallpapers-extra
```

---

### Post by nickleboyblue on 2011-10-03
As far as Unity goes, I don't know of a way to make it look like an earlier release while keeping the launcher.  However, if you want to get rid of the launcher, here's how:

When you get to the login screen, there are a couple of menu buttons on the bottom.  One of them allows you to select different "sessions."  Select "Ubuntu Classic," login, and from then on, it should automatically select that for you. That is where you'll be able to tweak things and make it look a lot more like the older versions.

---

### Post by Krytarik on 2011-10-03
> **deskman said:**
> hi! i wonder if there is a way to make my natty narwhall look like like older ubuntu releases.. karmic koala for ex. i just like the simple brownish interface.
For the Karmic versions of "human-theme" and "humanity-icon-theme" (if you also want the icons), download them here:

"human-theme": [http://old-releases.ubuntu.com/ubuntu/pool/main/h/human-theme/human-theme_0.37_all.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/h/human-theme/human-theme_0.37_all.deb)

"humanity-icon-theme": [http://old-releases.ubuntu.com/ubuntu/pool/main/h/humanity-icon-theme/humanity-icon-theme_0.4.1ubuntu5_all.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/h/humanity-icon-theme/humanity-icon-theme_0.4.1ubuntu5_all.deb)

Then basically follow this guide, adapting some of the steps to your particular case (the directory for the icon themes is "/usr/share/icons"):

[http://www.tuxgarage.com/2011/06/install-older-newer-ambiance-radiance.html](http://www.tuxgarage.com/2011/06/install-older-newer-ambiance-radiance.html)

Greetings.

---

### Post by deskman on 2011-10-08
thanks to everybody!
legacy-human did the trick for me!

---

