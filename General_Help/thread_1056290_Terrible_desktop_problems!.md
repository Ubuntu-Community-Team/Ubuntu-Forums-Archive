---
title: "Terrible desktop problems!"
date: 2009-01-31
forum: General Help
---

### Post by photon_man62 on 2009-01-31
Hello. I am writing this thread for a friend who does not speak English, so I can't IMMEDIATELY give you detailed info about his computer.

He runs Kubuntu Desktop 8.10 and has installed updates. He has the desktop driver that you can activate from a menu (he says his graphics card is a "Radeon x1600 series"). At the moment I told him to download an official ATI driver.

OK so now a more detailed explanation:

My friend went to the Appearance menu and selected "Extra Effects". Now, he can't resize windows, and his "sidebar" (as he called it) got smaller. So he went back and now chose "No Effects". Now he CAN resize windows, but the "sidebar" problem is still there. Other than that, his whole display seems to "flash" (you get it).

Any way to fix this? If not, he'll have to install regular Ubuntu.

---

### Post by photon_man62 on 2009-01-31
OK, so now he has installed the official driver.

---

### Post by jbrown96 on 2009-01-31
I think that kwin has stopped running. Try Alt+F2 (alt button and F2 pressed at the same time) and then type ```
kwin
``` and then enter. What version of KDE is he running? Try Alt+f2 again and ```
konsole
``` then go to help-->About KDE and write back with the version. If it's, version 4 (4.x.x), then he should use Kwin's effects system; it's quite good. I can help enabling that if that what he's running.

If this still doesn't fix the problem, it would be handy to see a screenshot of the desktop. Usually just pressing the print screen button (PrtSc) will bring up a dialog to save it. 


Edit: I think I might understand what he's talking about. If it it KDE 4, then he might need to resize it. He can right click on the middle and choose "panel settings" there are some arrow on the bar now (green and blue I believe) that he can drag to resize. If this is the problem, I would recommend upgrading to KDE 4.2 (not if he's using 3.x.x, though).

---

### Post by photon_man62 on 2009-01-31
It says

Wersja 4.1.3 (KDE 4.1.3)

---

### Post by photon_man62 on 2009-01-31
Still doesn't work, even after running kwin.

He says he's exhausted, so no screens until tomorrow :(

---

### Post by photon_man62 on 2009-01-31
OK he gave me some screens:

No effects:
[http://img205.imageshack.us/img205/3796/lol3rj8.jpg](http://img205.imageshack.us/img205/3796/lol3rj8.jpg)

Extra effects:
[http://img522.imageshack.us/img522/7789/lol4ph7.jpg](http://img522.imageshack.us/img522/7789/lol4ph7.jpg)

---

### Post by jbrown96 on 2009-01-31
He should upgrade to KDE 4.2 Follow the instructions [here]("http://www.kubuntu.org/news/kde-4.2") After upgrading, do a restart just to make sure. Then, disable the effects in the appearance window. Go to System Settings--->Desktop then enable the effects. There is a tab to specify each effect. 

The download is quite large so it might take a while.

---

