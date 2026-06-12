---
title: "Loss of control during gameplay."
date: 2009-10-05
forum: Gaming &amp; Leisure
---

### Post by myromance123 on 2009-10-05
Hi there, experiencing an odd problem that only arose since my upgrade to Ubuntu 9.04.
 This only happens when I play games and when those games are in fullscreen.
This is what happens:
 1.From fullscreen the game goes windowed.
 2.Loss of control from keyboard and mouse completely.
 3.Game then continues to play as per normal but in windowed, and I have no control(forced to restart to gain any control back).

These are the games that I experience this:
1. AssaultCube (obtained from playdeb.net).
2. Smokin Guns (obtained from playdeb.net).
3. VDrift (obtained from playdeb.net).
4. Urban Terror 4.1
5. Shadow Grounds Demo (obtained from LGP).

*Usually happens after 10-15 minutes of gameplay but Urban Terror lasts longer.


This occurs more frequently on my HP Pavilion dv3500 than my Desktop computer (custom made). 

The crime scene:
  Lappy (laptop):
         -HP Pavilion dv3500
         -Nvidia 9300M GS
         -Nvidia 185.18.36 driver (obtained from Nvidia site).
         -Up-to-date Ubuntu 9.04 desktop edition.
         -Core 2 Duo 2GHz
         -4GB DDR2 RAM

  Desktop (custom):
         -Intel Pentium 4 2.8GHz
         -1.5GB DDR1 RAM
         -Nvidia 9400 GT
         -Nvidia 185.18.36 driver (obtained from Nvidia site).
         -Up-to-date Ubuntu 9.04 desktop edition.
         -Samsung Sync Master (old skool CRT monitor).

In the background I have compiz on normal I believe and Cairo Dock on both but the presence of Cairo dock doesn't have anything to do with it...
Since I have tried the games with and without Cairo dock and the same thing happens nonetheless.

 Do you want me to try the games by running them through the terminal?
 Although I doubt I will be able to copy and paste or even select the terminal to view it when this happens as the computer doesnt respond to any input...
 So far when I run the games in windowed it holds up (although VDrift almost managed to make me lose all control even in windowed... somehow because I left a hanged firefox on in the background it saved me...).

What could be the root of this evil?

---

### Post by Perfect Storm on 2009-10-05
> 1.From fullscreen the game goes windowed.
2.Loss of control from keyboard and mouse completely.
3.Game then continues to play as per normal but in windowed, and I have no control(forced to restart to gain any control back).

Try this:

```
sudo apt-get install compizconfig-settings-manager
ccsm
```

General ---> General Options

In General tab
----------------
unselect "Unredirect Fullscren Windows"

---

### Post by myromance123 on 2009-10-05
Thank you for replying so fast!

 I don't mean to be rude or anything but what does that do?

Im installing it now.

 Oh it opens the manager.
Should I turn off Compiz everytime I want to run games?

---

### Post by Perfect Storm on 2009-10-05
No just unselect "Unredirect Fullscren Windows" if it's enabled, then compiz won't try rendering while apps/games are in fullscreen.

---

### Post by myromance123 on 2009-10-05
I could not find "Unredirect Fullscreen windows" anywhere in the manager.
 I did find Resize Window under Window Management and its enabled.
Should I disable that?

---

### Post by Perfect Storm on 2009-10-05
I have taken some screenshots, hope it helps.

---

### Post by myromance123 on 2009-10-05
Wow cool.

 Thanks for handling my query professionally AI :D

Pics helped a lot.

---

### Post by myromance123 on 2009-10-05
Ok even with the changes it happened again...

  Sorry I marked it as solved...it seemed as though it was working..

It just took longer to happen this time..

 Also this time the windowed size was larger than last time

nonetheless I had to restart my computer all over again....

Any ideas folks as to why this is happening?

---

### Post by Perfect Storm on 2009-10-05
It may be the screensaver/power manager that kicks in. Try disable the screensaver.

---

### Post by myromance123 on 2009-10-05
Yeah I think it might be the screen saver too but I'll try it now and post here afterwards.
 I'll re-enable the Unredirect Fullscreen and just disable the screensaver and see what happens.
 Brb in 20 mins maybe..

---

### Post by myromance123 on 2009-10-05
Okay this time it just hanged...

Game was still in Fullscreen though but it hanged completely..

 This cant be a hardware problem can it?

 It happens on both my laptop and my desktop?
Desktop is from 2004 but lappy is this year, only 4 months old...

Mmm I'll try other games and see what happens.

---

### Post by Perfect Storm on 2009-10-05
> **myromance123 said:**
> Yeah I think it might be the screen saver too but I'll try it now and post here afterwards.
 I'll re-enable the Unredirect Fullscreen and just disable the screensaver and see what happens.
 Brb in 20 mins maybe..

Try with both disabling screensaver and Unredirect Fullscreen

---

### Post by myromance123 on 2009-10-06
Ok it looks like it works now AI, after an hour of playing Assault Cube ;).

 Thanks again.

 For those who read this and have the same problem this is what I did to get things to work(summarized):

 Installed ccsm, and unchecked(or unticked) Unredirect "Fullscreen" from General Options and I also disabled Screensaver (which can be located from System->Preferences->Screensaver).
 Just unselect(or untick) "Activate ScreenSaver when computer is idle".

It doesnt matter if compiz is on or if you have Cairo Dock on :D

 Off to some gaming hehe

---

