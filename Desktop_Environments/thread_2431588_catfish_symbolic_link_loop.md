---
title: "catfish symbolic link loop"
date: 2019-11-18
forum: Desktop Environments
---

### Post by rattskjelke on 2019-11-18
I have been running Xubuntu 19.10 for several weeks and noticed what appears to be a bug that appeared recently.

When you install WINE it makes symbolic links from the My Documents, My Music, etc. folders in your wine username folder in ~/.wine to your ~/Documents, ~/Music, etc. folders and some symbolic links from ~/.wine/dosdevices/ to other folders.

Catfish never had a problem with these links in the past. Now it can't handle them properly.

Now whenever I search for something in my home (/home/username) folder Catfish looks like it follows the symbolic links in the wine prefix folder back to the /home/username folder and locks in a loop continuously finding the same files over and over until I quit Catfish.

Anybody out there know how to fix or prevent this?

---

### Post by vanadium on 2019-11-19
In the Catfish preferences, exclude these symlinks to prevent Catfish from searching these. According to the [release notes of 1.4.10](https://bluesabre.org/2019/09/13/catfish-1-4-10-released/), the version that ships with ubuntu 19.10, linked folders should be searched only once, but then, that feature may currently not be working as intended.

---

