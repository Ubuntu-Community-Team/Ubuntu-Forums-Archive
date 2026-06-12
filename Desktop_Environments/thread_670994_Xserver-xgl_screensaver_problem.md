---
title: "Xserver-xgl screensaver problem"
date: 2008-01-18
forum: Desktop Environments
---

### Post by PhaderSYD on 2008-01-18
I am experiencing very annoying glitches
I have a radeon 9550 runing on 7.10 propri drivers compiz works better than ever with xgl installed
but every ten mins into a movie the screensaver kicks in and i have to move mouse to get it off
is there any way to stop this.

i have changed my screensaver and power management setting no luck also 
tried chmod a+x screensaver no luck
also edited xorg.conf with commands of "0" no luck

sorry about the messy post.

---

### Post by DrFreeze on 2008-01-29
Bump

I've got the same problem

running ubuntu 7.10, vid card is an ati mobility radeon x1100 (rs485) running the frglx (or however thats spelled) driver.

screen saver and power management are set to the slackest positions on screensaver, but still every ten minutes i get a black screen

EDIT: fixed it, found the following trick on a dutch forum:

add the following to your xorg.conf:

```

Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection

```

to be honest i didnt figure it out myself, as im a total noob when it comes to xorg.conf, but setting these options solves the problem for me

---

