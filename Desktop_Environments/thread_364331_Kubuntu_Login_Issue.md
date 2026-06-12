---
title: "Kubuntu Login Issue"
date: 2007-02-18
forum: Desktop Environments
---

### Post by ShareBuntu on 2007-02-18
Hello everyone,

I seem to have run into an interesting problem. I was modifying /usr/share/wallpapers/ by removing some unneeded wallpaper. Unfortunately I deleted a default image used by the login manager. Every time I press "ctrl + alt + backspace" I'm greeted with the normal login screen but with the wallpaper missing it displays a black background in the back.

Is there anyway to change the default background to something else?

---

### Post by ShareBuntu on 2007-02-18
After a bit of poking around I managed to solve the problem myself. :) For anyone interested, and for future reference, there is a directory called "/usr/share/apps/kdm/themes/kubuntu/" that contains an XML file called kubuntu.xml. Within a tag called "normal" you can specify the location of the wallpaper you want to use for the login screen.

Also, you can change background of the splash screen after you've logged in under System Settings -> Advanced -> Login Manager -> Background. Configuring this to suite kubuntu.xml and you'll have a consistent background that compliments your desktop wallpaper.

---

