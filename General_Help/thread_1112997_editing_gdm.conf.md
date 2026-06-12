---
title: "editing gdm.conf"
date: 2009-04-01
forum: General Help
---

### Post by CoximusPrime on 2009-04-01
Hi guys,

I've been having problems with my screen resolutions. For some reason my ubuntu 8.04 system has dropped from 1280x1024 to 1024x768 ... I've been playing around to try and fix this and here's what I've found so far.

For some reason it is a problem that has developed between my ubuntu machine and my monitor. If I plug the system into a different monitor, it detects the new monitor fine and determines the highest resolution correctly.

I then came across this link [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) which pointed me in the direction of this solution:

Connect my monitor I'm having problems.
Open a terminal window
enter the following

xrandr --newmode "1280x1024" 90.75 1280 1328 1360 1440 1024 1027 1034 1054 +hsync -vsync

xrandr --addmode VGA 1280x1024

xrandr --output VGA --mode 1280x1024 --rate 60

and all is well again with the world (atleast until I restart).

I know I can generate a simple script to do this, and that I can run it from the .xprofile file for my user account, but to me the better solution would be to have this done in the gdm.conf file. Only problem is, I don't know how. The above link states that you can just put the xrandr commands in there, but this screws up when I do so, and I have to get back in and and remove the lines I entered.

Does anyone a way to get these commands into my gdm.conf setup??

Cheers everyone

---

### Post by WilliamJenningsBryan on 2009-04-01
You can't put them directly in gdm.conf, but gdm keeps its scripts in /etc/gdm and they could be added there.

Hope this helps!

---

### Post by CoximusPrime on 2009-04-01
You're a superstar!!!

I added the following lines to the file /etc/gdm/Init/Default:

[LIST]
[*]xrandr --newmode "1280x1024"   90.75  1280 1328 1360 1440  1024 1027 1034 1054 +hsync -vsync
[*]xrandr --addmode VGA 1280x1024
[*]xrandr --output VGA --mode 1280x1024 --rate 60
[/LIST]

This made the login screen the correct resolution but once logged in the resolution was still messed up, BUT!!!, I could select the desired resolution in System->Preferences->Screen resolution.

Made a permenant fix by then adding the line

xrandr --output VGA --mode 1280x1024 --rate 60

to /etc/gdm/PreSession/Default .... logs in now with the correct resolution .... finally back to a normal system :)

cheers for the pointer

---

