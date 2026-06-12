---
title: "Application Launch Bar Doesn't Offer Apps I've Added to Main Menu"
date: 2015-09-03
forum: Desktop Environments
---

### Post by LaneLester on 2015-09-03
I recently installed Lubuntu 15.04 and I added a side panel for apps I use often. The side panel has only one **Application Launch Bar** to which I've added six of the apps installed by the Lubuntu CD.

I've also installed **LibreOffice** (downloaded .deb's) and **GIMP** (from repositories), and I want to add them to the side panel. Although the two apps show in the menu, they do not show up in the **Application Launch Bar Preferences.**

I rebooted after adding the apps in hopes that would make them available. But it didn't.

Strangely enough, I used **MenuLibre** to add **jGnash** (Java app) to the main menu, and I was able to add it to the Application Launch Bar.

Lane

---

### Post by Rex Bouwense on 2015-09-04
I just checked on my Lubuntu and I can indeed add both the LibreOffice applications and Gimp as quick launch.  It should not make any difference whether your LXPanel is on the bottom or the side.  How are you trying to add them?

---

### Post by LaneLester on 2015-09-04
Thanks, Rex. I'm not sure Quick Launch, as you mentioned, is the same as having apps in the Application Launch Bar in a panel. But maybe it is.

Strangely enough, the two apps finally showed up as available to be added to the Application Launch Bar. I have no idea what changed to make them available.

Lane

---

### Post by Rex Bouwense on 2015-09-04
Great.  I have no idea why there was a delay.  Normally, if the application appears in the main menu, you can create a quick launch icon on the Application Launch Bar.

---

### Post by LaneLester on 2015-09-05
I discovered that MenuLibre saves application launchers, not in /usr/share/applications, but in /home/*username*/.local/share/applications. Perhaps that explains the strange behavior I saw.

Lane

---

### Post by LaneLester on 2015-09-05
I discovered that MenuLibre saves application launchers, not in /usr/share/applications, but in /home/*username*/.local/share/applications. Perhaps that explains the strange behavior I saw.

Lane

---

