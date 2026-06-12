---
title: "Visual Effects preferences change hangs - Lucid"
date: 2010-04-22
forum: Desktop Environments
---

### Post by peterkirn on 2010-04-22
In Lucid beta 2, Visual Effects hangs when changing settings. I can switch to "None" successfully, but when switching either to Normal or Custom (the latter after installing simple-ccsm), the dialog hangs on "Keep Settings." (That is, "Do you want to keep these settings?" appears, and if I click "Keep settings," the dialog hangs.)

Oddly enough, however, switching DOES work. Killing gnome-appearance-properties solves the issue.

I ask this prior to submitting a bug report, as I think perhaps this is related to other issues with the proprietary NVIDIA driver installation. Jockey doesn't show the restricted driver as installed, even though the NVIDIA setup reports it does -- I think because NVIDIA is using 195 and that dialog reports 190 (?)

---

