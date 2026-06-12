---
title: "Vsync?"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by tpettit on 2007-10-24
Hi!
I'm using ubuntu gutsy 7.10 with an nvidia 6800 ultra. everything works fine except for video playback, window dragging and anything that requires any graphics acceleration : everything tears up really bad. cant find anything in nvidia-settings that helps. Is there any way to enable VSync?
thanks

---

### Post by FuturePilot on 2007-10-24
Go into Nvidia settings and make sure SyncToVblank is enabled under Xserver XVideo Settings and under OpenGL settings.

---

### Post by tpettit on 2007-10-24
ok now the 3d cube works ok, but windows still look completely teared appart when dragged

---

### Post by Toffeeapple on 2007-10-24
I'm assuming you are using compiz thingie.. you mentioned 'cube'

in the compizconfig settings manager (System/Preferances/Advanced Desktop Effects Settings) 

under General Options/Display Settings.... check everything,

it worked for me even though the detected refresh rate shows 50 (for me) and I'm assuming its in actual fact 60... (I have an LCD thingie)

..no tearing :)

hope that helped.

---

### Post by FuturePilot on 2007-10-24
> **Toffeeapple said:**
> I'm assuming you are using compiz thingie.. you mentioned 'cube'

in the compizconfig settings manager (System/Preferances/Advanced Desktop Effects Settings) 

under General Options/Display Settings.... check everything,

it worked for me even though the detected refresh rate shows 50 (for me) and I'm assuming its in actual fact 60... (I have an LCD thingie)

..no tearing :)

hope that helped.
Yes, you can also check SyncToVblank in Compiz. Uncheck the Detect Refresh rate though, because it almost always gets it wrong with Nvidia cards. However, if you do this Suspend will no longer work correctly on Resume. Neither will switch user. You will be stuck at a black screen.

---

### Post by screaminj3sus on 2007-10-24
> **FuturePilot said:**
> Yes, you can also check SyncToVblank in Compiz. Uncheck the Detect Refresh rate though, because it almost always gets it wrong with Nvidia cards. However, if you do this Suspend will no longer work correctly on Resume. Neither will switch user. You will be stuck at a black screen.

Yeah I really hope this gets fixed. Right now I have it enabled because I just can't stand the tearing. Vista and OSX have never have tearing and you get reminded of how nice it was when you are using it with sync off.

---

### Post by FuturePilot on 2007-10-24
> **screaminj3sus said:**
> Yeah I really hope this gets fixed. Right now I have it enabled because I just can't stand the tearing. Vista and OSX have never have tearing and you get reminded of how nice it was when you are using it with sync off.

Yes, supposedly the next driver from Nvidia will fix this. I also have it enabled, just because I can't stand the tearing. I just have to be careful about switch user and suspend.

---

### Post by screaminj3sus on 2007-10-25
> **FuturePilot said:**
> Yes, supposedly the next driver from Nvidia will fix this. I also have it enabled, just because I can't stand the tearing. I just have to be careful about switch user and suspend.

Luckily it's a single user PC and I can go without suspend for now :)

---

### Post by Loevborg on 2007-10-30
> **FuturePilot said:**
> Yes, you can also check SyncToVblank in Compiz. Uncheck the Detect Refresh rate though, because it almost always gets it wrong with Nvidia cards. However, if you do this Suspend will no longer work correctly on Resume. Neither will switch user. You will be stuck at a black screen.

If I'd only known this when gutsy was released! (Good info!) Do you have a bug report at hand?

---

