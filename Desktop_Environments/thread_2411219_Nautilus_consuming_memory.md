---
title: "Nautilus consuming memory"
date: 2019-01-27
forum: Desktop Environments
---

### Post by Jijimon on 2019-01-27
I am using Ubuntu 16.04 (up to date). i3 processor, 8GB RAM, desktop. When I open a folder (saving day-to-day files) containing 25,000 file system monitor will show memory full (8GB RAM), system will slow down, sometimes crash Ubuntu. The same problem experienced in 18.04, Debian also. (I am an average user only, I can use terminal by copy paste method only, don't know the meaning.)

---

### Post by mc4man on 2019-01-27
A long time issue, though typically that 'smaller' number you have would just take excessive time, not consume all & burn.. 
[https://bugs.launchpad.net/nautilus/+bug/869793](https://bugs.launchpad.net/nautilus/+bug/869793)

You could try turning off file preview/thumbnails, may help a little.
Otherwise consider,
1. Break folder into multiple subdirectories containing smaller number of files
2. Install a file manager that handles large file count dir.'s  well, use it to open this and any similar directories.
  gnome-commander would work well in this case.

---

