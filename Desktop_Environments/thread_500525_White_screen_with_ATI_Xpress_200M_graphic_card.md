---
title: "White screen with ATI Xpress 200M graphic card"
date: 2007-07-14
forum: Desktop Environments
---

### Post by iamthebest22 on 2007-07-14
OKay, I just installed Beryl manager, settings manager and the other one, and now, whenever I launch Beryl Manage, the moment the red gem shows up on my top right, the screen goes totally white, and I can't switch cubes, any help is appreciate. If there is anything like this mentioned before, I would be totally happy if you can direct me to it. I'm a total noob at linux btw, also, I know this was probably mentioned before, but I just can't seem to find the drivers for my wireless Broadcom BCM43406 card to make wireless internet work on it. I really need help! Those are the only two issues I have!

---

### Post by divague on 2007-07-14
Which method did you use to install beryl?

for the wireless card check this thread

[http://ubuntuforums.org/showthread.php?t=493558](http://ubuntuforums.org/showthread.php?t=493558)

---

### Post by iamthebest22 on 2007-07-14
I just did it from the add/remove under applications in Ubuntu 7.04. I just searched and installed it. Oh and also, i fixed it now, all i did was type in beryl-manager --no-force-window-manager. I did check out that guide, but I don't think mines is in there, well my laptop doesn't seems to be supported. My laptop is a Compaq Presario R4000 series, with ATI Xpress 200M, 1GB ram, Broadcom BCM4306 wireless LAN 802.11b/g controller (rev 03)

EDIT: Btw, do you know what setting I should have to have the my beryl look like the guys in youtube? here's the link:
[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ) Thanks for the help!

---

### Post by mkoyle on 2007-07-15
This fellow has the same wireless adapter.  He got it working with bcm43xx-fwcutter.

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

Afraid I can't be so helpful with Beryl... probably a driver issue.  You might try installing an ATI driver with envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html))  Best of luck.

--Matthew

---

### Post by castoroil97 on 2007-07-15
usually when u get the white screen,
the driver is not installed.

On my laptop I run an ATI 200 mobility express.  I installed FGLRX, which is the closed source driver.

Post your xorg.conf and 

the log file in /var/log  it has xorg log in the name, but I don't remember the exact name

the log file should tell you what is going on.

Make sure the driver is installed before trying beryl again

typing > fglrxinfo|grep direct

direct rendering should be 'yes'

with mine though, once I set up XGL, it would give me a 'no' but it worked anyway and that was after xgl was installed.

If you go the open source route, it works differently

make sure you read the guides very carefully

---

