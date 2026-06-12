---
title: "Update manager problem."
date: 2009-04-16
forum: General Help
---

### Post by ismialexis on 2009-04-16
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by scragar on 2009-04-16
```
sudo dpkg --configure -a
```Run that from a terminal.

---

### Post by ismialexis on 2009-04-16
sudo dpkg --configure -a
dpkg: failed to write status record about `pulseaudio-utils' to `/var/lib/dpkg/status': No space left on device


thats what it said when i tried

---

### Post by scragar on 2009-04-16
Sounds like you've run out of space on that partition, is there any way you can free some up for dpkg to finish? If not you might be able to free some up by deleting a few old logs and cleaning a few caches:
```
cd /var
sudo rm cache/apt/archives/*.deb
sudo rm log/*.gz
```
I'd also run the disk usage analyser, might be interesting to know where all your hd space has gone.

---

### Post by ismialexis on 2009-04-16
tried to delete stuff using disk usage analyzer and when i click move to trash it says could not find a trash folder on this sytem The folder "user" was not moved to the trash.

---

### Post by ismialexis on 2009-04-16
alexis@alexis:~$ cd /var
alexis@alexis:/var$ sudo rm cache/apt/archives/*.deb
rm: cannot remove `cache/apt/archives/*.deb': No such file or directory
alexis@alexis:/var$ sudo rm log/*.gz
rm: cannot remove `log/*.gz': No such file or directory
alexis@alexis:/var$

---

### Post by scragar on 2009-04-16
> **ismialexis said:**
> tried to delete stuff using disk usage analyzer and when i click move to trash it says could not find a trash folder on this sytem The folder "user" was not moved to the trash.

Don't delete anything you are unsure about until you get the OK from someone on this board or you understand your system better, I'm assuming you just tried to delete /usr DONT, /usr contains lots of important things like most of the executables on your system(for the file manager, the graphics, games, programs...), along with man pages etc.

If you can upload something from your home directory to your emails or something similar and delete it that would be best. You won't need much free space, a MB or two should be sufficient to fix the install.

When you have finished the install there are a few things you can uninstall to free some space, there are threads dedicated to that though(I won't link to them now since you are unable to use the package manager).

---

