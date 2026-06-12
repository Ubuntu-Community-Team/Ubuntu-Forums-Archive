---
title: "KDE Fails to start"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Bruno Amaral on 2006-07-20
for some reason, KDE froze on me and I had to hit the reset switch.

after the boot, I get to the login screen, type the password...and instead of my desktop, I'm sent back to that login screen.

so far I tried :
sudo dpkg-reconfigure -p high xserver-xorg
sudo dpkg-reconfigure kde-core
and even
sudo dpkg install kde-core

I don't want to re install kubuntu. Does anyone have a clue on what I can do?

---

### Post by wieman01 on 2006-07-20
I usually experience this kind of problem after tempering with the "xorg.conf" file. Could you check if there are any characters in the file that don't belong there?

You could try to recover the file by renaming the backup-file "xorg.conf~" into "xorg.conf" and thus overwriting it... But make sure you have safety copies of both files.

---

