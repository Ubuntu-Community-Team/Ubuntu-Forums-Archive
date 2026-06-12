---
title: "[SOLVED] Wubi Help"
date: 2008-12-20
forum: General Help
---

### Post by davidbilla on 2008-12-20
Is it possible for Wubi to screw up an existing Windows installation? That is, is it possible for something to go wrong during wubi installation and the user becomes unable to boot into windows?

And, can I just create an iso of a livecd(8.04) and use it with 'daemon tools' to install ubuntu using wubi?

---

### Post by abn91c on 2008-12-20
wubi installs just like any windows program and makes virtual disks, it does not partition windows. Make sure you defrag windows before you begin, your iso needs to be in the same folder as the wubi.exe if you are trying to install it from the live cd use the install within windows option. Also avoid hardboots

---

### Post by davidbilla on 2008-12-20
Thanks for that. The other thing I wanted to know is, whether I can create an ISO of the "live cd" (which includes wubi itself) and load the iso as a virtual drive in windows using 'daemon tools' and then choose 'Install within Windows'. Will it work? Because here it's not the program wubi that is using the iso; the iso itself contains wubi. I presume that I won't need a reboot during the installation process. Because, if there is a need to reboot, then the iso won't be in memory, which means wubi won't be in memory.

---

### Post by abn91c on 2008-12-20
when you burn a ubuntu live cd, wubi installer is included, go to windows explorer and run it from there

---

