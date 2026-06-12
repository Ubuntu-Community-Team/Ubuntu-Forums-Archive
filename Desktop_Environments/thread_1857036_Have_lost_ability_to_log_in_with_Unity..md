---
title: "Have lost ability to log in with Unity."
date: 2011-10-09
forum: Desktop Environments
---

### Post by altheablue on 2011-10-09
Hello all. I'm running 11.10 and I have somehow lost the ability to log in with Unity. At the log-in screen when I click the little, gear, the options for Gnome, Gnome Classic, KDE, etc. are there, but the Unity and Unity 2D options are gone. 

The only possible cause I can think of is that I uninstalled and reinstalled Nautilus in Software Center. (I did this because it was crashing literally every time I opened it.)

Any thoughts would be much appreciated. :)

---

### Post by Krytarik on 2011-10-09
The removal of Nautilus tore many packages with it that depend on it, so better just reinstall it the next time (either via command line or Synaptic; the latter needs to be installed first in 11.10), if you think it would solve your issue.

Now, however, just reinstall the package "ubuntu-desktop", which will effectively also pull in Unity:
```
sudo apt-get install ubuntu-desktop
```Note: To reinstall a package instead (if it's installed at that time; as opposed to the above case), just add the option "--reinstall" to a command like the one above.

Regards.

---

### Post by altheablue on 2011-10-09
Thank you! :D 

Still working on Nautilus (actually it seems to be better), but Unity is back. Thanks for your help! :)

---

### Post by Krytarik on 2011-10-09
> **altheablue said:**
> Still working on Nautilus (actually it seems to be better)
You could also give Thunar a try, possibly it fits your needs. ;-)

---

