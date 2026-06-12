---
title: "Removing packages not through apt"
date: 2009-01-18
forum: General Help
---

### Post by Pixel on 2009-01-18
How wold I go about removing programs I compiled from source?

I know I can delete the file in /usr/bin, but I know that wouldn't be everything... am I forced to hunt down every single file spread across my HDD manually, or is there an easier way?

---

### Post by Rocket2DMn on 2009-01-18
Usually you go the source directory that you installed from and run
```
sudo make uninstall
```
If you didn't use sudo during the install, you shouldn't need it to uninstall.
For the future, check out the program checkinstall which is used when building from source so that you can handle the program through apt/synaptic.  It doesn't always work, but it's worth trying.

---

