---
title: "how to backup packages?"
date: 2009-02-16
forum: General Help
---

### Post by James4 on 2009-02-16
hello everyone,
I wanna know if there is way to backup installed packages so the it can be restored in case of reinstallation.
any help would be appreciated.

---

### Post by geirha on 2009-02-16
All packages you've installed from the repositories are located under /var/cache/apt/archives/. Those packages gets deleted if you run ```
sudo apt-get clean
``` so if you've run that at any point, then it doesn't contain all installed packages anymore.

Look at [https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD) for information on how to back them up.

---

### Post by shortylonglegs on 2009-02-16
I know you can get a list of all your installed packages and save them to a file:
```
dpgk --get-selection >> ./installed
```
Reinstalling is harder, the best way I've found is to open the file with gedit and do find and replace to get rid of all the extra space, so its just the list of packages on a single line, then run
```
sudo aptitude install < ./installed
```
I've read of other ways to do it, but could never get them to work right.

---

### Post by James4 on 2009-02-16
> **geirha said:**
> Look at [https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD) for information on how to back them up.

thanks man. that was great.

---

