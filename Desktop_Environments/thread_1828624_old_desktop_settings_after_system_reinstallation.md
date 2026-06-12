---
title: "old desktop settings after system reinstallation"
date: 2011-08-19
forum: Desktop Environments
---

### Post by albelix on 2011-08-19
I had to reinstall ubuntu 11.04 from CD (before I used only upgrades) on my Sony notebook because of touchpad problems (mouse freezes, and I could not permanently recover it). In the new install, I want to map the partition with my workfiles to home directory, and it all works fine using 

sudo mount /<partition> /home

However, when I do the same thing in /etc/fstab, for some reasons the system boots with old desktop settings, including the problem with my touchpad. This means that my workfiles partition contains some info about desktop settings, but I could not trace where they are located; playing with fstab command options does not help either. Any suggestions how can this be sorted out?:confused:

---

