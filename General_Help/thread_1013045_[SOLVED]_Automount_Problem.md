---
title: "[SOLVED] Automount Problem"
date: 2008-12-16
forum: General Help
---

### Post by greenco on 2008-12-16
Yesterday, I used the "sudo apt-get -y install liveusb" terminal command to install the liveusb module, so that I could make a bootable USB flash drive. Now I am having a problem with my CD/DVD drives not automounting. The drives are shown, when I double click on the computer icon and they work OK. The DVD drive holds a game disk, that must in the drive for the game to work. In order for me to play the game, I have to double click on the DVD drive icon, so that it opens and I can see the files. Before I installed the "LiveUSB" module, Ububtu 8.04 automounted the DVD drive, on bootup, and placed the game icon on the desktop. Is there a way to correct this?

Thanks

EDIT: I found that the FSTAB entry, for my CD/DVD drives was set to "noauto". I edited it to read  auto and now the DVD drive is mounted when I bootup.

---

