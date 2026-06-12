---
title: "KDE window manager problems"
date: 2008-03-04
forum: Desktop Environments
---

### Post by distortedskies on 2008-03-04
Hi everyone this is my first post here and I am looking for some help with a problem I am currently having. The other night I downloaded chkrootkit and ran a test, at the end of the test it gave me something like this:

The tty of the following user process(es) were not found
in /var/run/utmp !
! RUID PID TTY CMD
! myusername 4053 tty7 X :0 -auth /home/mattih/.serverauth.4027 -nolisten tcp -nolisten tcp

for some reason I decided to kill the PID and as soon as I did my window manager screwed up and now I have no titlebars on any windows, my icons for network manager, kwallet, beagle, etc. that were in the lower right corner of my taskbar all disappeared and I can't move any windows, they all pop up in the bottom right corner of the screen with half the window not visible. These problems are for the whole system, even if I log in as root, I even tried making a new user and the same thing happens. I have tried updating my Xorg and KDE files with yast and it didn't help. Have tried killing X and restarting many times as well as running kwin --restart and still no luck. The funny thing is that I run NXserver (nomachine) and when I connect remotely it all looks fine. Also when I start from a command prompt and type startx it also works fine, it just seems to be when I login in from the main login screen that I get these problems. Anybody have any ideas? I'm stuck on this one. I am using opensuse 10.3 installed from the DVD with kde 3.5. I really don't want to have to reinstall my whole system since I have a lot of stuff setup on here and I don't want to have to go through the whole process of manually editing all my ssh and nx config files again and reinstalling my programs. Any Ideas???

---

