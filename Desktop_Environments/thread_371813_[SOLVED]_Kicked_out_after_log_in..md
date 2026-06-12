---
title: "[SOLVED] Kicked out after log in."
date: 2007-02-27
forum: Desktop Environments
---

### Post by anyoneseenmypenguin on 2007-02-27
Hi all has anyone had this problem before? When I log into my Gnome desktop just as the background picture loads it kicks me out and back to the log in screen. I've noticed the lower panel loads correctly but the upper panel does not then back out again to the log in screen. At first I thought maybe a video card problem because the colours would be way off then the computer might even freeze,so after trying another (ATI) video card and rebooted the system worked ok for the rest of the night. The next night back to the same thing. Here is my specs AMD Duron 1.3 Gig 384 Mb ram ECS K7s5a motherboard HP dvd rw and 6.4 Gig Quantum hard drive using a ati rage 128 video card.I'm running Ubuntu 6.10 


Also wondering if I could check some kind of a log file to troubleshoot this problem?


Thanks.

---

### Post by taurus on 2007-02-27
At the GUI login screen, press <Ctrl><Alt>F2 to get to a virtual console.  Log in with your name and password.  Then, look at the output of ~/.xsession-errors.

```
tail -20 ~/.xsession-errors
```
Otherwise, post the output of this command here.

```
df -h
```

---

### Post by anyoneseenmypenguin on 2007-02-27
Hi thanks for the reply I'll try the output log bit when I get home. I did use the df -h it's ok showing only 47% used on my drive.

---

### Post by anyoneseenmypenguin on 2007-03-01
ok here is some of the output from /.xsession-errors log 

/etc/gdm/PreSession/Default: running : /usr/x11R6/bin/sessreg -a -w /var/log/wtmp
-u /var/run/utmp -x " /var/lib/gdm/:O.Xservers"
-h " " -l ".O" "username"
/etc/gdm/Xsession:Beginning session setup...
/etc/profile :20: [[:not found
SESSION_MANAGER =local/username-desktop:/tmp/ .ICE-unix/4347

Looks like gnome can't find my profile? how can I fix that? Or how did that happen?:confused:

---

### Post by scxtt on 2007-03-02
/etc/profile doesn't do much that is important - wouldn't worry about that ... i'd try deleting anything ~/.gnome* related to start your gnome user configs anew ... note: this may "mess up" some specific gnome-centric configs you have, nothing life changing tho ... and you can always back it up 1st ...

---

### Post by anyoneseenmypenguin on 2007-03-02
Hi thanks for the reply I did find some info about your suggestion So I logged in using gnome failsafe and went into the home directory and deleted the .gnome folder and renamed the .gnome2 folder to .gnome as previously recommended by someone else. Now when I log in the first time it kicks me out after about 20 seconds then the next time I log in it seems to work. What I found out is the .gnome2 folder is automatically recreated again at the next login. What I don't understand is why this happened in the first place. Here is what I did to lead up to this problem I did a fresh install (because of the same problem) then I installed some apps. amsn,frostwire,sun java 5.0,wifi radar,and a wireless network manager also gnome baker cd burning app. I set the top and lower panel to transparent and added launchers for these apps to the bottom panel (like a Mac) and when I shut down and re-started the problem was there. I tried another video card and ran the memory testing utility for a long time no errors?:confused:

---

### Post by anyoneseenmypenguin on 2007-03-03
OK... just a thought is it possible that after installing new programs and features the default video driver has become corrupted. What I notice is on first login (when I can't get in) the background picture colours are distorted then I get kicked out to the log in screen again. How can I check the installed driver (default) used by Ubuntu edgy and find out if I should use a better one? I'm using a older ATI video card (I have 2 of them) Rage 128 and a Radeon 7000 DDR TVO

---

### Post by scxtt on 2007-03-03
do this:

cat /etc/X11/xorg.conf | grep Driver

you'll probably get some mouse/keyboard items returned - but should be able to easily tell which one is the video driver (something like 'vesa', 'ati', 'radeon' - most likely 'vesa')

then do a "sudo dpkg-reconfigure xserver-xorg" and select something else (out of that list of 3 above)

---

### Post by anyoneseenmypenguin on 2007-03-04
Hey thanks for  all the help my problem was the video settings. The driver seemed to work ok but when I ran the reconfigure xorg and rebooted my problems are gone. A BIG THANK-YOU to all.:) :) :) 

P.S. To anyone interested when using the failsafe gnome option the pop up window message "There was an error starting the gnome settings daemon etc..... you know the rest...." is normal for failsafe mode.

---

