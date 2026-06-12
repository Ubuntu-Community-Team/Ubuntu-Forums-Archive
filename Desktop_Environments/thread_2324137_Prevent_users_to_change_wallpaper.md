---
title: "Prevent users to change wallpaper"
date: 2016-05-11
forum: Desktop Environments
---

### Post by Asier_Asu on 2016-05-11
Hello, I am new in this forums, and my english level is not the highest it could be (I am spanish)

I have been trying to prevent users to change their desktop's image on Ubuntu 16.04, but I was unable. I heard that editing /usr/share/unity-2d/shell/launcher/Launcher.qml and deleting all strings that contains "wallpaper" I could make it, but the directory does not exist anymore. Also I try changing Desktop/ permissions, but neither it works. Using dconf-editor seems to have the solution to my problem, but in org.gnome.desktop.background I did not see the way I can lock the wallpaper.

Hope you can help me, and again sorry for committing grammar mistakes or misspellings.

---

### Post by Frogs Hair on 2016-05-13
Hello and Welcome 

One way to do this would be to remove/delete all but the default wallpaper from usr/share/backgrounds. Elevated permissions would be required to do so. If the users have Internet access there is nothing preventing them from using an image from the web.

---

