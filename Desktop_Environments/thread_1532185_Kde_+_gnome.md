---
title: "Kde + gnome"
date: 2010-07-16
forum: Desktop Environments
---

### Post by AClockWorkLemon on 2010-07-16
Hi there :D

I am aware that this may have been asked before, however i could not find a satisfactory answer whilst searching.

I Am running Ubuntu 10.04 LTS, with GNOME desktop. Recently I installed the KDE Desktop to see what it was like. For the moment, i would like to use both.

I was wondering how i could set different startup preferences for each. Currently i want:

GNOME:
Emerald
AWN

KDE:
Plasma display (the environment itself)

Over time i may expand this.

Any help on how i can set different startup preferences would be greatly appreciated

---

### Post by WinterMadness on 2010-07-16
the startup options are independant from one and other if im not mistaken.

so if you log into gnome, and go whereever it is you go to change the startup applications it wont effect the kde startups. The only exception ive noticed was AWN manager

---

### Post by AClockWorkLemon on 2010-07-16
AWN is the main issue at the moment.

Also, it would seem both KDE and GNOME store their autostart apps in the same place - ~/.config/autostart/

KDE has a separate sutostart folder, namely ~/.kde/Autostart/ , but it also looks in the generic folder.
This means i can specify apps that only start for KDE, but not apps that only start with GNOME

---

### Post by SnickerSnack on 2010-07-16
This might help: [http://ubuntuforums.org/showpost.php?p=4854518&postcount=2](http://ubuntuforums.org/showpost.php?p=4854518&postcount=2)

Once you have kde and gnome using different startup programs, it should be possible to have awn start with different settings.

This: [http://ubuntuforums.org/showpost.php?p=5056877&postcount=14](http://ubuntuforums.org/showpost.php?p=5056877&postcount=14)

(last line in the code block: X-GNOME-Autostart-enabled=true)

suggests that maybe you can set programs to start in gnome but not kde.

---

### Post by AClockWorkLemon on 2010-07-16
I think i might have got it sorted out...

BUT i CANNOT for the life of me stop AWN opening!
I have removed the awn.desktop files from /etc/xdg/autostart, ~/.config/autostart AND ~/.kde/Autostart, and it dosn't open in GNOME, but it still opens in KDE (and no, there is not any entries for it in KDE's autostart settings

Never mind, it has magically dissapeared :D

---

