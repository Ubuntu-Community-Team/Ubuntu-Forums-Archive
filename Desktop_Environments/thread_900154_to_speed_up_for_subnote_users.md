---
title: "to speed up for subnote users"
date: 2008-08-25
forum: Desktop Environments
---

### Post by nicedog on 2008-08-25
i am using a EEE PC 900 with 1G RAM.

i chose Xubuntu becuz the Ubuntu web said it is lighter weighted for old pc... in fact Xubuntu does not run noticably faster than Ubuntu... 

following some postings, i changed the WM to fluxbox which come with a baby naked UI may require some more tweaking.

while i may spend more effort to tweak the fluxbox, i am thinking to stop some of the services in the XFCE session that may gain me some performance.... already stopped the following:

Bluetooth, CUPS

others candidtates i need your advice before stopping it cuz i don't what they are.

Power management (there are 2!!??)
action scheduler (again there are 2!!)
Multicast DNS recovery

also, in seesion and startup dialog the option "Start up GNOME services" is enabled? what are they actually? cuz i am running XFCE, I wonder if i really need GNOME services, cuz any software based on GNOME should load the proper GNOME lib when running it...

besides, i am thinking to replace the web browser to enhance the sys performance. the default firefox 3 would somehow freeze up if opening a few tabs and running along other app like miro... heard that FF# under linux is a memory hog.. not sure... installed Kazenase, Seamonkey and Opera... first impression is that i didn't notice any apparent performance boost over FF3 (maybe Seamonkey is subjectively faster, need more time to test...

any idea on my lighter and stable web browser?

---

### Post by qball on 2008-08-25
gnome startup service is gdm. That is what you use to log into your xfce.
The delays in firefox 3 you can "solve" by setting the disk-cache to 0.

I don't think the services you mention will affect the actual  performance of xfce. (mostly bootup).

I self find xubuntu more then fast enough, on lesser hardware.

---

