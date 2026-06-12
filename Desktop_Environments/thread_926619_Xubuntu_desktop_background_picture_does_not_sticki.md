---
title: "Xubuntu desktop background picture does not stick/is not centered"
date: 2008-09-22
forum: Desktop Environments
---

### Post by vussvillem on 2008-09-22
**Problem**. Every single time when I restart my computer and log into XFCE4 session, my customized desktop background picture is covered with initial Xubuntu 8.04 default background picture in the left-top part of my desktop covering about 3/4 of the desktop. Curiously, there is no such a problem, when I just restart my X Window System (ctrl+alt+backspace).

When I open Xfce settings manager and look for the desktop picture source, it points to the custom desktop background picture like it should ( [http://nagi.ee/photos/photo_sizes.php?id=7878541&size=o&album_id=127405](http://nagi.ee/photos/photo_sizes.php?id=7878541&size=o&album_id=127405) ).

When I totally deleted the original Xubuntu 8.04 background picture from /usr/share/xfce4/backdrops the problem is still there, however, left-top 3/4 part of my desktop is then just covered with blue area ( [http://nagi.ee/photos/photo_sizes.php?id=7878533&size=o&album_id=127405](http://nagi.ee/photos/photo_sizes.php?id=7878533&size=o&album_id=127405) ).

I can clean up my custom desktop picture, when I point at it in the desktop settings menu and load it again. But doing that every single time when I start up my laptop is nothing that I would characterize as comfortable. 

**What I have tried, without success**.
1) I have tried to choose my custom desktop background picture from Xfce4 default background pictures' folder versus from my home folder
2) I have checked weather this is related to the resolution/size of the picture - the answer is no
3) I have unchecked "save the session" option in Xfce menu when shutting down my computer

---

### Post by x1a4 on 2008-09-22
Configure your system just the way you like, log out and make sure to check 'Save session...'.  Log back in.

Use the 'Desktop' dialog in 'Settings Manager' to set the background image and to centre it.  Make sure Xfce's desktop is running.

---

### Post by vussvillem on 2008-09-23
x1a4 thanks for reminding the basics about changing the desktop background in Xfce. However, I believe, this is not the issue in here.

---

### Post by vussvillem on 2008-11-04
With the help of user named TheSheep on #xubuntu IRC, I've found the reason and temporary workaround (OK, the problem is not really solved, but at least you can get rid of the second picture) for this bug.

The small desktop picture, covering my original desktop picture, it seems that it appears when you have edited xorg.conf file and added a line specifying S-video out (TV out) option (I had ->Option "TVDACLoadDetect" "TRUE" in Device section as suggested in [http://www.uluga.ubuntuforums.org/showthread.php?t=641998](http://www.uluga.ubuntuforums.org/showthread.php?t=641998) ; TheSheep had not only desktop picture but also panels appearing on that 4/5 part of the screen, so...). If you comment it (put # in the beginning of the line) in xorg.conf, the problem goes away. 

However, when you want to use S-video for directing picture to TV screen - and I do. a lot - you have to uncomment it and afterwards comment it again, so it is not very convenient. I've filed a bug on that, leave a comment if it affects you as well -> [https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/275747](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/275747)

---

