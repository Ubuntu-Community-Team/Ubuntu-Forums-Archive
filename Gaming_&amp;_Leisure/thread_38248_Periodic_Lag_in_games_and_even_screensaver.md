---
title: "Periodic Lag in games and even screensaver"
date: 2005-05-30
forum: Gaming &amp; Leisure
---

### Post by TheChaos0 on 2005-05-30
Hey, I noticed thins wierd problem. Whenever I play games...or if the screensaver is running...it lags...Well every 10 seconds the picture stops for couple miliseconds and then continues...and so on. 

It's pretty annoying. Any suggestions?

---

### Post by dolny on 2005-05-30
I have the same problem with ATI Radeon 9600 Pro and latest drivers. PLEASE HELP!!! :( Thats extremely annoying when I want to play and online game :(

---

### Post by rider343 on 2005-05-30
[QUOTE=dolny]I have the same problem with ATI Radeon 9600 Pro and latest drivers. PLEASE HELP!!! :( Thats extremely annoying when I want to play and online game :([/QUOTE]
 [http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati+drivers](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati+drivers)

---

### Post by dolny on 2005-05-31
Erm, how is that supposed to help? I have the drivers installed, I just get the lag in games :/

---

### Post by foxy123 on 2005-05-31
it may be that something causes it on the background... in my case it is gdesklets, when I close it, everything is running almost smooth...

---

### Post by Moobert on 2005-05-31
install htop to stop overly cpu using programs

then run from a terminal and press shift + p.. it will list by cpu useage (shift + m does memory useage).. then just press k followed by an action to kill the program... (you wil need to sudo to kill root things... but avoid X and gdm ect :) then just press q to close htop.

---

### Post by dolny on 2005-05-31
Thanks to your advice I have found the source of the problem, but it looks bad because the process is:

[img]http://www.echostar.pl/~dolny/ubuntu/freezes.png[/img]

I was playing Quake in the window mode to check the freezes and the freezes occur exactly when this progarm jumps from about 0.7% cpu usage to like 15-20% suddenly for a second. Then it works okay for some time and it happens again.

Help, help, help - PLEASE! I can't play online.

---

### Post by dolny on 2005-06-04
I BEG YOU. HELP!!! 

I'm having this damn periodic hardware lag on almost (if not all) every game I play :( It is not a huge problem in single player but I can't play Jedi Academy or any other online game - PLEASEEEEEEEEEEEEEEEEEEEE!!!!!!!

I'm so depressed ;(

---

### Post by crane on 2005-06-05
I'm having the same problems. I have tried to see if the problem exists on another distro or if it is maybe just Xorg and nvidia.

 I Didn't have this problem when I first moved to Hoary though. What nvidia driver is everyone using?
Also what is the easiest way to install newest driver? I know there is a how to but I can't find it.

---

### Post by dolny on 2005-06-05
I'm using ATI Radeon. I also didn't have that problem earlier. Maybe its because of some new kde files? Kde-libs, kdenetworkconf? Dunno. Somebody must give us the answer :(

---

### Post by crane on 2005-06-05
[QUOTE=dolny]I'm using ATI Radeon. I also didn't have that problem earlier. Maybe its because of some new kde files? Kde-libs, kdenetworkconf? Dunno. Somebody must give us the answer :([/QUOTE]

Ok if your running ATI then my guess it's not video card related. I'm running nvidia. I'm also not KDE because I don't have it installed either.

 It has to be some process running that is causing it.

---

### Post by dolny on 2005-06-05
Well I mentioned the process thats taking up to 45% of my cpu every 10-15 seconds. I mentioned it before (you can find the screen couple of posts earlier). Unfortunately its the X server.
 
I installed the newest KDE: 3.4.1
I tried almost every possible fglrxconfig configuration

Still no change :( I can't play games on Kubuntu. This SUCKS!

---

### Post by dolny on 2005-06-05
After spending the whole day on checking everything, installing new KDE, configuring fglrxconfig in different ways and reading many pages in the net, I **SOLVED the problem** :D

I killed the 'kicker' process in KDE (even though it wasn't even using 1% of cpu, according to kde system guard and htop) and checked the performance. No hardware LAGS! Then I switched 'kicker' on - again - 10 seconds of good performance, 2 seconds of lag (45% cpu occupied by Xorg) etc. 

So... I have to find another taskbar... or turn it off when I play.

Check if killing the 'kicker' process (from root) worked for you. If it did - we can send the bug to bugzilla.

Edit: On my kicker, an 'mbar' applet (custom) was probably causing it. But it as well may be for example kmix on your kicker.

---

### Post by crane on 2005-06-05
[QUOTE=dolny]After spending the whole day on checking everything, installing new KDE, configuring fglrxconfig in different ways and reading many pages in the net, I **SOLVED the problem** :D

I killed the 'kicker' process in KDE (even though it wasn't even using 1% of cpu, according to kde system guard and htop) and checked the performance. No hardware LAGS! Then I switched 'kicker' on - again - 10 seconds of good performance, 2 seconds of lag (45% cpu occupied by Xorg) etc. 

So... I have to find another taskbar... or turn it off when I play.

Check if killing the 'kicker' process (from root) worked for you. If it did - we can send the bug to bugzilla.

Edit: On my kicker, an 'mbar' applet (custom) was probably causing it. But it as well may be for example kmix on your kicker.[/QUOTE]

I'm running gnome and I don't see kicker running. I think I'm going to install Xfce and see if the problem is there as well.
I do have a notification aplet running. I wonder if that could be it.

So all you Q3 players, what servers do you play on? Would be cool to meet up wit other Ubuntu users for some fraggin!

---

### Post by Gnobody on 2005-06-09
I had this problem only it was gamin in Gnome.

---

### Post by crane on 2005-06-09
Just recently installed the latest Nvidia drivers. Will play tonight and see it I notice a lag.

---

### Post by cofko on 2008-04-20
I was having the same periodic lags in normal desktop usage (not gaming or whatever) -  it was gDesklets . I was using 0.35.3-4ubuntu2 version from gutsy gibbon repos. I removed it and installed this 0.36 deb package : [http://greenie.sk/ubuntu/gdesklets-0.369_i386.deb]("http://greenie.sk/ubuntu/gdesklets-0.369_i386.deb") 

Now it works with no problem :)

---

