---
title: "[SOLVED] What has happened? Please help with desktop"
date: 2008-06-08
forum: Desktop Environments
---

### Post by AndreiMe on 2008-06-08
This is the deal:
clean ubuntu install, everything went well... until i rebooted for some updates and my desktop went ...mad!
everything dissapeared and now all i have is my wallpaper and the icon of my memory stick. i can't even use alt+f2. 
any ideas please?

---

### Post by Vadi on 2008-06-08
Try doing ctrl+alt+1, and do "sudo apt-get remove ubuntu-desktop" and then "sudo apt-get instal ubuntu-desktop"..

---

### Post by bigken on 2008-06-08
boot into recovery mode at the prompt type 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

you could also try this found another thread 

gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop true

---

### Post by mrmark24 on 2008-06-08
AndreiMe: I, too, installed some updates, and everything on the top and bottom of my Ubuntu screen went-away...  I thought it was because I completely removed Evolution from Synaptic Package Manager, but following Vadi's recommendations, I soon discovered that the gnome-desktop had somehow become "uninstalled" on my computer.  Try the "sudo apt-get remove ubuntu-desktop", and it may tell you, like it did me, that it isn't intalled.  When you try "sudo apt-get install ubuntu-desktop", don't forget the second "L" in install :)

Vadi: I did what you suggested, and with "remove", it told me gnome-desktop was not installed.  I didn't meant to be "nit-picking" about the second "L" in my reply to AndreiMe; it's just that the two "L's" in install are important.  Anyway, I tried this and now have both of the bars at the top and bottom; thank you :)

bigken: for some reason when I booted into "recovery mode", it would not let me connect to any of the Ubuntu servers, thus I could not do what Vadi suggested, which is pretty much what you suggest.  Following Vadi's recommendations, though, I was able to discover that the gnome desktop wasn't installed and it installed properly when I did the "sudo apt-get install gnome-desktop".

Thank you to all for posting and helping to resolve this issue!
mrmark24

---

### Post by AndreiMe on 2008-06-09
so ... it worked! thanks alot i really didn't want to reinstall everything.

---

