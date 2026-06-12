---
title: "KDE File Association Problems After Upgrade"
date: 2008-12-12
forum: Desktop Environments
---

### Post by Freezewarp on 2008-12-12
Hi, I'm currently having some problems with the file associations used in Dolphin and Koqueror that make using them somewhat troubling. Anyway, this started when I upgraded from Kubuntu 8.04 to 8.10. Previously I had both KDE3 and KDE4 installed, with KDE3 being known as "KDE". When I upgraded KDE3 was removed (as it should have been) and KDE4 was changed to the primary "KDE". Unfortunately, when I upgraded, it seems as though the file associations were not updated, and so I now have a big mess whenever I try to open a file. There are many applications still listed in the "open with" menu in the file browsers from before the upgrade, being called "[Applications] (KDE4)". Many times the KDE applications that don't end in "(KDE4)" will still be executed with a kde4 command, like "kde4-[application]". Also, the same problem is occurring with KRunner when I try to launch an application. Is there any way to completely erase all traces of these files as well as update the commands to execute the programs?

Any help would be greatly appreciated.

p.s. I have already tried erasing the ~/.kde/share/mimelnk and /usr/share/mimelnk folders.

Edit: Well, I think I fixed it. Had to remove ~/.local/.

---

