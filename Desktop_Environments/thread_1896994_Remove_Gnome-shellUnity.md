---
title: "Remove Gnome-shell/Unity"
date: 2011-12-18
forum: Desktop Environments
---

### Post by SpEcIeS on 2011-12-18
Is there a way to remove Unity without having Gnome-shell installed and vice-a-versa?

---

### Post by 3Miro on 2011-12-18
If you want to keep Gnome 3, then you need either Gnome-shell or Unity in order to use it. You can remove Gnome 3 altogether, but you should make sure to install one of the other DE first (i.e. KDE, XFCE, or LXDE).

Check here:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by 73ckn797 on 2011-12-18
These instructions [http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html) will remove Unity but you would still have Gnome 3 and could run it in Classic mode.

---

### Post by SpEcIeS on 2011-12-18
The psychocats.net was the best I could come up with as well. I suppose what I am looking at, since I am a Fluxbox user, is a base type install, which is found in Debian installs. The demand for a generic desktop install links dependencies that are sometimes unnecessary.

---

### Post by 3Miro on 2011-12-18
> **SpEcIeS said:**
> The psychocats.net was the best I could come up with as well. I suppose what I am looking at, since I am a Fluxbox user, is a base type install, which is found in Debian installs. The demand for a generic desktop install links dependencies that are sometimes unnecessary.

Yes, I have noticed that Ubuntu packages sometimes come with more dependencies than what I would like. You can try to take an alternative CD and make just a base install of Ubuntu. Then you can add just the packages that you want, this will make the most "minimal" install possible.

---

### Post by ugm6hr on 2011-12-18
> **SpEcIeS said:**
> The psychocats.net was the best I could come up with as well. I suppose what I am looking at, since I am a Fluxbox user, is a base type install, which is found in Debian installs. The demand for a generic desktop install links dependencies that are sometimes unnecessary.

I'd suggest removing all Gnome packages using the commands listed here: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

Just omit the final ```
&& sudo apt-get install lubuntu-desktop
```

Given Lubuntu / LXDE is Openbox based, I suspect this will probably remove most of the unnecessary dependencies.
Else, start again with a genuine minimal installation, as per 3Miro.

---

