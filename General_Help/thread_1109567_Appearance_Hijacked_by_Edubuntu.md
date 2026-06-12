---
title: "Appearance Hijacked by Edubuntu"
date: 2009-03-28
forum: General Help
---

### Post by OsakaWilson on 2009-03-28
I just finished installing Jaunty and thought it looked great. However I added the "Educational Desktop of Ubuntu" thinking it would be just a bunch of educational software. It changed all of the icons in the system to Edubuntu icons and the flash screen when I boot up is Edubuntu.

I removed the educational desktop, but the icons and flash screen remain. Is there any way to revert? I am fully willing to completely reinstall the system to get my settings back.

---

### Post by Denestria on 2009-03-28
```
sudo update-alternatives --config usplash-artwork.so
```
will get change the boot splash.

---

### Post by OsakaWilson on 2009-03-28
I put that in, but this is what I got. Then I rebooted, but still the Edubuntu screen.

"There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure."

---

### Post by Denestria on 2009-03-29
Well then try
```
sudo dpkg-reconfigure usplash
```

and check synaptic for edubuntu-artwork package.  It probably wasn't removed with the desktop bundle.

---

