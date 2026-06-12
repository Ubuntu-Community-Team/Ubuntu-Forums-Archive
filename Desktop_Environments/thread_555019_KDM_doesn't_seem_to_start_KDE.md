---
title: "KDM doesn't seem to start KDE"
date: 2007-09-19
forum: Desktop Environments
---

### Post by idtt2s on 2007-09-19
I can see the KDE option fine, but when I start it using KDM, I get a terminal to the top left of my screen. I'm assuming this is the "failsafe" mode, in which I start KDE using "startkde", which works fine. How can I get KDM to start KDE correctly?

---

### Post by Lord Illidan on 2007-09-19
Very strange.. How did you install KDE?

---

### Post by idtt2s on 2007-09-19
I installed KDE using "apt-get install kdebase", but during the installation, I was using GDM to boot into my DEs and that worked fine. I also installed and removed KDE4, following the guide which required me to mess with my kde.desktop file, even though it was just to make a copy. I highly doubt that would make a difference but I guess I'll declare it anyways.

---

### Post by idtt2s on 2007-09-19
I fixed it. The problem lies in one of the KDM configuration files. Even though I tried going through my system deleting files that relate to KDM, the problem still presists. So I did an "apt-get remove --purge kdm" and reinstalled KDM. Now everything is fine.

---

