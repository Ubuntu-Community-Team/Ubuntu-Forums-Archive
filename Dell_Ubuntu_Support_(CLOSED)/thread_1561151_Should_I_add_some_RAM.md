---
title: "Should I add some RAM?"
date: 2010-08-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by s0563764 on 2010-08-25
Hi I recently installed Ubuntu 10.04 on my old Dell 8300 as a media centre, it has currently 512MB of RAM and works fairly well and smooth(better than XP). I was wondering if it is worthwhile adding some RAM to it? According to the system monitor it does not fully use the 512MB (in fact the recognises it as 496.7MB), and instead swaps into using a small amount of memory on the HDD. I am currently using the computer for general household uses like media playing, and internet.

---

### Post by wojox on 2010-08-25
I bought a 1GB stick and added it to my old Dell (512GB) and saw a big difference. It never even touches swap now.

---

### Post by rollin on 2010-08-25
Good suggestion from Wojox as usual! You could try a "lightweight" alternative like Xubuntu which ships the Xfce environment. You'll still get all the functionality of an Ubuntu OS but things will be slimmed down to make it less RAM intensive.
If you want to recreate the original Ubuntu but with the lightweight window manager Xfce here are a few ideas.
Install Xubuntu
Then run the command sudo apt-get install ubuntu-desktop
Once this is finished add the following commands to your startup applications:
killall xfce4-panel
gnome-panel

Reboot and you should now have an Xfce environment (lighter RAM) which looks like the default Gnome Ubuntu out of the box :D
Note you'll have duplicate applications in some cases like screensavers. Just examine the menu under System > Preferences > Main Menu and look at their properties and uncheck the gnome variants and keep the Xfce versions.

---

### Post by mörgæs on 2010-08-26
Xubuntu is a bit lighter than Ubuntu, but if you want to be really light on memory (while staying in the *buntu family) Lubuntu is the best option. 

You could try this:
[http://ubuntuforums.org/showpost.php?p=9758078&postcount=8](http://ubuntuforums.org/showpost.php?p=9758078&postcount=8)

---

### Post by ronnielsen1 on 2010-08-26
Upgrading memory is one of the best upgrades you can do

---

### Post by s0563764 on 2010-08-27
Cheers guys, I considered the memory upgrade when it was an XP. Ubuntu runs a lot smoother but I've been spoilt by newer machines which have more RAM etc, so my computer behaviour has grown into playing movies and surfing etc at the same time.

I wasn't sure if it was because the pentium 4 was just not up to scratch, but I'm sure its the lack RAM, as the swap gets fairly big.

---

