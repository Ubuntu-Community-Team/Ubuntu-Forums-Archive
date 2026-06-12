---
title: "Games blinking in fullscreen after update"
date: 2012-09-22
forum: Desktop Environments
---

### Post by Syrx on 2012-09-22
I have Ubuntu 12.04 with Gnome Shell.
I installed updates and after that I noticed that my games (Nexuiz, Hedgewars...) are blinking in full screen. So I looked in the list of packages that were changed and discovered this:
xserver-xorg-video-intel was updated to version 2:2.19.0-0ubuntu1~xup1
So I forced the old version (2:2.17.0-1ubuntu4.1) and everything was ok. 

With the new version, I had the problem only in Gnome Shell, Unity and Gnome Classic were both ok. 
I was using integrated Intel HD Graphics 4000.

Personally I don't mind using the old version, but I was not sure if I should report it somehow.

---

