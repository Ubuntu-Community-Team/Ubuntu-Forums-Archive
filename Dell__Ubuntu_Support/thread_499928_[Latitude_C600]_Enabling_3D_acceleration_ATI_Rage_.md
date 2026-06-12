---
title: "[Latitude C600] Enabling 3D acceleration ATI Rage 128"
date: 2007-07-13
forum: Dell  Ubuntu Support
---

### Post by yary.ribero on 2007-07-13
Hello Everyone!

I have just installed Ubuntu Feisty Fawn on my oooold laptop, a latitude C600, and I am very satisfied.
Since yesterday I have managed to make all work, now I am trying to enable 3D acceleration on my graphic card: ATI Rage Mobility, based on the chip 128.
I downloaded the proper driver from site [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) but i failed to compile.
After looking on log i noticed that, despite it was the last release, it was out of date.
I'm editing the code handly, but I'd like to know if someone encountered the same problem with drivers from that site, and if someone know an easier solution or want to lend me a hand.
Bye!

---

### Post by Rocket2DMn on 2007-07-13
If you can't use the open source drivers, you may need to download the restricted ATI drivers.  
Here is a guide you can follow: [http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty](http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty)

The short way is to enable restricted repositories by editing /etc/apt/sources.list and running
```
sudo apt-get update 
sudo apt-get install xorg-driver-fglrx
```

3D acceleration can be enabled after rebooting.  I forgot the command, I think it might be fglrx-config, but I think you can do it from the GUI, too.

There is no need to have to edit the code .

---

### Post by angryfirelord on 2007-07-13
> **Rocket2DMn said:**
> If you can't use the open source drivers, you may need to download the restricted ATI drivers.  
Here is a guide you can follow: [http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty](http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty)

The short way is to enable restricted repositories by editing /etc/apt/sources.list and running
```
sudo apt-get update 
sudo apt-get install xorg-driver-fglrx
```

3D acceleration can be enabled after rebooting.  I forgot the command, I think it might be fglrx-config, but I think you can do it from the GUI, too.

There is no need to have to edit the code .
Good guide, but it won't work. :) The fglrx drivers only work with the Radeon 9500 up and the Rage is way older then that. 

The open-source drivers do provide 3D functionality, but what are you trying to run on it? More than likely, the card is too old to run any 3D intensive applications.

---

### Post by Rocket2DMn on 2007-07-13
Hrmm, I didn't double check compatibility, I forgot how old Rage cards are - I was there, I should know better.
But yeah, sounds like 3d acceleration shouldn't be too much of a loss if the computer is that old.  Driver support for video cards, ATI especially, in linux is not too hot.  Hopefully Gutsy will have better support, but I think the older cards are just kinda screwed, even my Mobility Radeon 9000 is likely too outdated to get any attention.

---

### Post by angryfirelord on 2007-07-13
Yeah, ATI's a weird nut. On one hand, you card can't be too old or the fglrx driver won't work. On the other hand, if your xorg is too new, it won't work either (like in fedora, where I had to downgrade my xorg to get it working, but that's not fedora's fault in any shape).

---

### Post by yary.ribero on 2007-07-15
Thanks for replies.
I'm trying to run  a game that works perfectly on the same pc under win xp, the game's name is Tibia ([www.tibia.com](www.tibia.com)), a game that uses mainly cpu rather than graphic card.
My interest is not just play that game, but revising the code I downloaded since I think it's out of date. A proff of what I say? In the includesfo that drivers you can find #include <linux/config.h>, a file that was removed some linux kernel release ago.
I'll go on with revisingf, if someone is interested in helping, leave me a message.
Bye!

---

