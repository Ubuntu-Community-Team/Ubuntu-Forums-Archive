---
title: "How to Set Different Icons?"
date: 2013-05-25
forum: Desktop Environments
---

### Post by FrankJAlejo on 2013-05-25
Hey guys, so recently I been trying to make my ubuntu look very google themed. I wanted to change the systems icons to also be very googled themed.
I wanted to know how could I make [http://carlosjj.deviantart.com/art/Google-JFK-Icons-ICO-and-PNG-270715545#comments](http://carlosjj.deviantart.com/art/Google-JFK-Icons-ICO-and-PNG-270715545#comments) [http://cornmanthe3rd.deviantart.com/art/Plex-287022406](http://cornmanthe3rd.deviantart.com/art/Plex-287022406) working in ubuntu? 

Am a fresh newbie to ubuntu :p

---

### Post by zombifier25 on 2013-05-26
That icon set has yet to be made for Linux (which would make installation easy), so you'll have to rename everything by hand to create a new icon theme. If you only wish to replace the icons, then run this command:
```
gksu nautilus
```
Now you'll have nautilus running as root, which can do anything so **be very careful**. Navigate to /usr/share/applications, search for the app you want to replace the icon (for example Firefox), right click it, choose "Properties", click on the icon and navigate to the icon you downloaded in your home folder (/home/yourusername). The change will not be instant, you have to restart the Unity desktop by running
```
unity
```

---

