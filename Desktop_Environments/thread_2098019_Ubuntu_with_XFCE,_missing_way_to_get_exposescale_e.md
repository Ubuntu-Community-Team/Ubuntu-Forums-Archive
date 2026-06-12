---
title: "Ubuntu with XFCE, missing way to get expose/scale effects without compiz!"
date: 2012-12-25
forum: Desktop Environments
---

### Post by Ronalds on 2012-12-25
Merry Christmas to all of Ubuntu users! :) I have been using ubuntu and loving it, for about half year, since I discovered 12.04 with unity, right now I have switched my desktop environment to XFCE, and I founded it to be very fast and good alternative for those who liked Gnome 2. What it lacks, is that it doesn't have Compiz type **effect-scale/expose or "show all windows", like Mac OS X expose effect**, you can get in Unity with compiz. I founded this effect in Ubuntu Tweak app (God bless the developer..), and it's amazing for rearranging windows by just turning my mouse to hot corner. In XFCE, I like that it doesn't use compiz, and it has it's own composting window manager, but it surely lacks this feature. I founded out some alternatives-**skippy**, (it lacks easy installing and hot corners feature), and** telescope**. (it's on arch repository, and I haven't even tried it yet.)
Maybe somebody knows how to get this feature, without using compiz-or using compiz-with low level ram usage (not like I don't have ram, but I don't like bloated things), to work on[B] XFCE environment!
[/B]Thank's for your answers, and happy holidays!

---

### Post by LewisTM on 2012-12-25
Just put the skippy-xd executable in /usr/bin (I think you can even find a .deb if you look hard enough). Then, install package brightside. Execute brightside and brightside-properties, set skippy-xd to be called from a corner. Brightside needs to be launched at every login so add it to the startup applications.

Cheers and Merry Christmas!

---

### Post by Ronalds on 2012-12-25
> **LewisTM said:**
> Just put the skippy-xd executable in /usr/bin (I think you can even find a .deb if you look hard enough). Then, install package brightside. Execute brightside and brightside-properties, set skippy-xd to be called from a corner. Brightside needs to be launched at every login so add it to the startup applications.

Cheers and Merry Christmas!
 
skippy-xd in terminal, gets this 
WARNING: Couldn't load config file '/home/ronalds/.config/skippy-xd/skippy-xd.rc

---

### Post by Ronalds on 2012-12-25
I installed brightside from here
[https://launchpad.net/ubuntu/+source/brightside/1.4.0-4.1ubuntu1](https://launchpad.net/ubuntu/+source/brightside/1.4.0-4.1ubuntu1)

I installed skippy-xd, used configuration I founded here..
[https://wiki.ubuntu.com/Skippy](https://wiki.ubuntu.com/Skippy)

started skippy with skippy-xd --start-daemon and skippy-xd --activate-window-picker
f11 doesn't start the effect, what would? how to manage it to use brightside?

---

### Post by Ronalds on 2012-12-25
> **Ronalds said:**
> I installed brightside from here
[https://launchpad.net/ubuntu/+source/brightside/1.4.0-4.1ubuntu1](https://launchpad.net/ubuntu/+source/brightside/1.4.0-4.1ubuntu1)

I installed skippy-xd, used configuration I founded here..
[https://wiki.ubuntu.com/Skippy](https://wiki.ubuntu.com/Skippy)

started skippy with skippy-xd --start-daemon and skippy-xd --activate-window-picker
f11 doesn't start the effect, what would? how to manage it to use brightside?


so I did as you sad- lounched brightside-properties- added custom action to corner- skippy-xd, and it works! but there is no windows borders, and it doesn't show all apps when I do it...

---

### Post by Ronalds on 2012-12-25
> **LewisTM said:**
> Just put the skippy-xd executable in /usr/bin (I think you can even find a .deb if you look hard enough). Then, install package brightside. Execute brightside and brightside-properties, set skippy-xd to be called from a corner. Brightside needs to be launched at every login so add it to the startup applications.

Cheers and Merry Christmas!

So, after getting it to work, compiz variant still worked better, so I added some compiz to xfce, and RAM usage is not that bad, like 7 mb... no need for skippy anymore..

---

### Post by mmutoo on 2013-01-30
Hi guys,
It has been for a while now that I am using xubuntu, and I also really missed the scale effect. Now, I installed skippy-xd and brightside and they work perfectly. There is only a small annoying thing here. When I move my mouse cursor to the corner and skippy window picker runs, the mouse jumps to the center of the active window in the thumbnailed windows. I think you understand that how much a jumping mouse can be annoying :) So, anybody knows how to trick the mouse to stay in the corner when skippy is run?

---

