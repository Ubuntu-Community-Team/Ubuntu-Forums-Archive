---
title: "Changed desktop environments and its messed up my system"
date: 2015-03-19
forum: Desktop Environments
---

### Post by Ben_Hazelwood on 2015-03-19
Hi first time post here so let me know if I've missed anything useful out

After installing Ubuntu for the first time the other day, I decided I wasn't really a fan of Unity and installed Gnome. Everything worked fine and I stayed with Gnome for a while.

I then installed KDE to try it out and things didn't go so smoothly. It seemed to change things like scrollbars and other UI items even when logged into a GNOME session. 

Therefore I decided to uninstall KDE, however it only removed a few KB vs. the roughly 150MB it took to install.

I then followed this script I found online to completely remove KDE from my system found on this forum post:

[http://askubuntu.com/questions/451620/how-to-completely-remove-kubuntu-desktop-from-ubuntu](http://askubuntu.com/questions/451620/how-to-completely-remove-kubuntu-desktop-from-ubuntu)

```
sudo aptitude remove '?and(?and(?reverse-depends(kubuntu),?not(?reverse-depends(ubuntu-gnome-desktop))), ?not(?or(?priority(required), ?priority(important))))' ubuntu-gnome-desktop+
```

However, I fear this may have removed far more from my system than I realised as it has changed really weird things like my keyboard layout.

Another issue is that my right click menu is now dark grey as opposed to the white before.

Any ideas about how to get a pure GNOME back on my system?


Moral of the story: don't run a script if I have no idea what it does!!!

---

### Post by CantankRus on 2015-03-19
Try installing ubuntu-gnome-desktop.
```
sudo apt-get install ubuntu-gnome-desktop
```

---

### Post by Ben_Hazelwood on 2015-03-19
> **CantankRus said:**
> Try installing ubuntu-gnome-desktop.
```
sudo apt-get install ubuntu-gnome-desktop
```

i've tried that but thanks for the idea. I've also tried reinstalling unity but the same problem occurs there.

---

### Post by CantankRus on 2015-03-19
Sometimes the easiest solution is to backup, reinstall and start afresh.
Half an hour of your time and just add it to your learning experience.
If you only want Gnome, install it in the beginning.
 [http://ubuntugnome.org/](http://ubuntugnome.org/)

---

### Post by Ben_Hazelwood on 2015-03-19
> **CantankRus said:**
> Sometimes the easiest solution is to backup, reinstall and start afresh.
Half an hour of your time and just add it to your learning experience.
If you only want Gnome, install it in the beginning.
 [http://ubuntugnome.org/](http://ubuntugnome.org/)


I was starting to think that may be te best option. Shame I already had to do it the other day due to some Bumblebee curiosity. You'd think I'd learn eventually...:p

---

### Post by CantankRus on 2015-03-19
> **Ben_Hazelwood said:**
> I was starting to think that may be te best option. Shame I already had to do it the other day due to some Bumblebee curiosity. You'd think I'd learn eventually...:p
In my fiddling days I used to do a fresh install every week. :p

---

### Post by Ben_Hazelwood on 2015-03-19
> **CantankRus said:**
> In my fiddling days I used to do a fresh install every week. :p

Haha I can see why. Really should just use VM but it just takes the fun out of it

---

### Post by sammiev on 2015-03-19
In my Gnome Desktop I have VMware installed and test everything else there. One day one of those I test maybe my main Desktop.

Nice for testing the next release as well.

---

