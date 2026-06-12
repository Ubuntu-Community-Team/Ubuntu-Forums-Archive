---
title: "Lost title and status bars in some KDE apps."
date: 2009-01-15
forum: Desktop Environments
---

### Post by alex777 on 2009-01-15
There are no title and status bars in Krusader, Akregator and Dolphin, which is irritating - I can't minimize or «unmaximize» these applications for example. Moreover when I run these applications I don't see the Gnome Panels on the top and on the bottom - these applications seem to run sort of «full screen». Other Gnome and KDE applications on my system (K3b, Smplayer, Ktorrent) run Ok. 

It happened after I changed a couple of settings in my Compiz configuration (I wanted to «pin» my task list to the desktop and I did so: [http://ubuntuforums.org/showthread.php?p=6552170](http://ubuntuforums.org/showthread.php?p=6552170)). But maybe these events are not connected, I don't know. What can I do?

I'm using Ubuntu 8.10.

---

### Post by Vinci71 on 2009-01-16
> **alex777 said:**
> There are no title and status bars in Krusader, Akregator and Dolphin, which is irritating - I can't minimize or «unmaximize» these applications for example. Moreover when I run these applications I don't see the Gnome Panels on the top and on the bottom - these applications seem to run sort of «full screen». Other Gnome and KDE applications on my system (K3b, Smplayer, Ktorrent) run Ok. 

I'm using Ubuntu 8.10.

Same here, but I just upgraded to the last packages in 8.10. I didn't made any change to Compiz settings. I experienced this problem with KMail and Krusader, while K3b, Klibido and other seems to work fine.

---

### Post by alex777 on 2009-01-16
It's a Compiz bug. If you disable Compiz window titles are back again (Preferences -> Appearance -> Visual Effects -> None).

But I hope someone suggests a better solution because I need Compiz.

---

### Post by alex777 on 2009-01-16
I've found a better workaround until they fix this bug. Just start your glitchy KDE applications UNMAXIMIZED, and you'll see the window titles. But never maximize them, or the problem will be back.

---

### Post by eyelessfade on 2009-01-16
Actually I don't have the problem on kde-nightly so I guess the bug might be in kde.

---

### Post by prince_niceguy on 2009-03-18
seems this resolves the issue...

Uncheck the checkbox located at:
System -> Preferences -> CompizConfig Settings Manager -> Utility -> Workarounds -> Legacy Fullscreen Support



thanks to this [thread]("https://answers.launchpad.net/ubuntu/+source/kdepim/+question/61586")...

---

### Post by walter_j on 2009-03-19
This problem happens without compiz, and often happens to firefox in gnome. I found if you delete the rc file in ~/.kde/share/config for the app, the app generates a new rc with borders. The issue also happens in firefox, so you have to find the gnome settings file and delete it too - but you lose bookmarks and plugins...

walter

---

