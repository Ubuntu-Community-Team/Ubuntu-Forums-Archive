---
title: "Compiz effects only work for one user"
date: 2011-08-29
forum: Desktop Environments
---

### Post by benny6669 on 2011-08-29
Apologies in advance if this is a re-post of an existing question, but if it is I haven't been able to find it:

I recently installed Ubuntu 11.04 on an Athlon XP 2500+ box with 2GB RAM and a new NVIDIA 7600GT AGP video card w/ 280.13 drivers from NVIDIA site (couldn't get the 270.xx version from the official repos working properly). Using "Ubuntu Classic" GNOME 2.32 since I dislike Unity. Dual-monitor outputs go to LCD over VGA (primary) and S-Video RF modulator for TV (secondary). It took some doing to get working right; I had to copy over the xorg.conf from the previous (OpenSUSE 11.3 w/ KDE4) OS to get dual-monitor working correctly. The /home directory for all users is on a separate partition, so old settings from previous OS installations (without the NVIDIA card) are still there.

The problem is, one user's display configuration is screwy. Primary user (mine) works great for everything; Compiz effects work, CCSM changes appear as expected, and new windows/applications appear on the monitor that they're expected to. However, the secondary user doesn't work right: maximized windows appear on the secondary monitor by default (IIRC there's a bug-report about that somewhere), and changes to CCSM (including importing the other user's Compiz profile) seem to do nothing.

Is there a config file option or directory that I should be looking at? I have a feeling I'm missing something silly somewhere, perhaps Compiz isn't set to start for this user's login? My apologies again if this is already answered somewhere that I just can't find yet; any suggestions, links or other help are greatly appreciated!

---

