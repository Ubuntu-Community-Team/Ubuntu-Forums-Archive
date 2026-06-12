---
title: "Upgrade to Jaunty via terminal"
date: 2009-06-18
forum: General Help
---

### Post by rbc on 2009-06-18
I did not know that one could not upgrade from 8.04 to 9.04, so I upgraded to 8.10. I am very pleased with it, but during the upgrade process, even though the CPU is 2GB (I do not have it in front of me, so I forget what GHz it is), the CPU seemed to be taxed to its limits. At least that’s what the desktop widget thingy showed. So, here is the question…..if I do ctrl+alt+F1 and drop to command line, and upgrade from there, will that be gentler on the CPU? Also, do I have the terminal commands correct:
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by Cheesemill on 2009-06-18
The GUI won't be using much of your CPU at all, the decompression and installation of the packages will be using most of your CPU.
This is a good thing. The more CPU power the update process uses the faster it will complete.

Also the apt-get dist-upgrade command doesn't upgrade. You need to hit ALT+F2 and run:
```
gksudo update-manager -d
```
instead.

---

