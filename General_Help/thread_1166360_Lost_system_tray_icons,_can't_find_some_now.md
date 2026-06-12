---
title: "Lost system tray icons, can't find some now"
date: 2009-05-21
forum: General Help
---

### Post by burvowski on 2009-05-21
Hi,

I got myself my first netbook (an Asus eee 1000HE), selling my Macbook Pro in the process (the one with the incompatible x1600 graphics card), and after checking to see if it booted, clicking "No" to the XP EULA, proceeded to install UNR 9.04 on it. I really love it, even though for some reason it seems to be reporting less battery life than I expected it would.

Anyway, I tried to install this program: [http://greg.geekmind.org/eee-control/#install](http://greg.geekmind.org/eee-control/#install) in the hopes that it would fix the battery life, but after trying to do that through Terminal (something I am new to), I got a bunch of errors while trying to install the .deb package. After it failed, there was the EEE controller icon in the system tray, but I had lost a bunch of others, including my Pidgin icon, my battery icon, and my network/wireless icon. Again, despite the eee icon being there, it did not work.

I went into Synaptic Package Manager and completley uninstalled the EEE app, and went into "Add to Panel" to try to get the icons back. Thing is, the network icon isn't exactly the same. It's just that typical network icon you see across different OS's, instead of a set of bars to show me how strong of a wireless signal I have, which I would prefer to be able to see how strong my connection is at a glance. I also added the battery icon, but it is slightly different than the original one. Not a huge deal, but I REALLY preferred the original one that was there.

The weirdest thing is Pidgin's icon. I had it set in Pidgin's preferences to always show, and even when it dissapeared, it still said that in Pidgin's preferences. I tried turning off the icon and turning it back on, but no luck. I then went into Synaptic again and tried to completley remove Pidgin and install it again, but that hasn't worked either.

So, does anyone know how I can get Pidgin's, the battery, and the wireless icon back? Also, if anyone has tips to succesfully install that original EEE app, I would really appreciate that as well.

Thanks in advance for any help given!

---

### Post by mcduck on 2009-05-21
Sounds like you have removed the Notification Area-applet from your panel. Just add it back and all those icons will appear again. (they are not applets of their own, simply running programs that place their icons in the Notification Area).

(by the way, x1600 works just fine with Ubuntu. My laptop has one and I've never had any problems. ;))

---

### Post by gsingh on 2009-05-21
right click the panel > add to panel > Notification Area

Add that and you should see your icons appear.

Let us know the out come.

---

### Post by gsingh on 2009-05-21
right click the panel > add to panel > Notification Area

Add that and you should see your icons appear.

Let us know the out come.

---

### Post by burvowski on 2009-05-21
> **mcduck said:**
> Sounds like you have removed the Notification Area-applet from your panel. Just add it back and all those icons will appear again. (they are not applets of their own, simply running programs that place their icons in the Notification Area).

(by the way, x1600 works just fine with Ubuntu. My laptop has one and I've never had any problems. ;))

Awesome! Thanks for the help! That worked perfectly, including for Pidgin.

I know the x1600 works, but I couldn't get 3D functionality (fancy compfiz effects and gaming) to work because of ATI moving the drivers to legacy support. It's not a big deal. It was a great laptop, but too much overkill for what I need.

Any tips on installing the eee applet? 

I am so glad the OS is coming together the way I'd like. If I can get the eee icon installed (assuming that will fix my battery life...it's *supposed* to get 9.5 hours, but is reporting 5 hours left), and if I can get sound working in my mp4 movies, I will be a hampy camper.

---

### Post by lozenceto on 2009-09-05
McDuck, you are the greatest. Thanx a lot about the tip to redisplay the notification area?
Good

---

