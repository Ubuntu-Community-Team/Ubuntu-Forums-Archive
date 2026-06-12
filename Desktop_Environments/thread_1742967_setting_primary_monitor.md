---
title: "setting primary monitor"
date: 2011-04-29
forum: Desktop Environments
---

### Post by kaiseroskilo on 2011-04-29
I use two monitors,my problem is that I want to change the setup,so that the other monitor becomes default.
There's no problem with my BIOS settings and I have tried every GUI tool that could help me(to my knowledge).Well I've found this
[http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions](http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions)
that helps a lot but I want to execute the command every time I boot before the splash screen(so that the login screen appears on the right monitor).I've tried rc.local but had no success.Any ideas on how to execute the command at boot time?Thanks in advance.

---

### Post by CastleBrav0 on 2011-04-29
I'm running into the same (?) problem.  

I have a dual monitor setup, I installed 11.04 and the Unity panel is always on the wrong monitor.  I tried plugging each monitor into a port on the back of my video card but that didn't work either.

I did some digging and came across a similar solution using xrandr.  I put all of the commands into a BASH script and it works fine.  I just can't find a way to execute the script automatically upon boot (or even login).

Any ideas?

---

### Post by KegHead on 2011-04-29
Hi!

system...preferences...monitors

KegHead

---

### Post by teachop on 2011-04-29
> **CastleBrav0 said:**
> I'm running into the same (?) problem.  

I have a dual monitor setup, I installed 11.04 and the Unity panel is always on the wrong monitor.  I tried plugging each monitor into a port on the back of my video card but that didn't work either.

I did some digging and came across a similar solution using xrandr.  I put all of the commands into a BASH script and it works fine.  I just can't find a way to execute the script automatically upon boot (or even login).

Any ideas?
This isn't much of an idea.  I had the same experience that the xrandr setting for primary monitor swapping would be lost after reboot.  Then I made the change with xrandr, and went back into the settings application for monitors in gnome, and fooled around.  That seemed to trigger saving the current state, and made it stick, don't know how?

---

### Post by Krytarik on 2011-04-30
See this guide on how to add the 'xrandr' commands to the startup script of GDM, to get run upon loading the login screen:
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts)

Greetings.

---

### Post by themainliner on 2011-04-30
> **KegHead said:**
> Hi!

system...preferences...monitors

KegHead

Easy...where is Preferences then?

---

### Post by KegHead on 2011-04-30
Hi!

click on system..you'll see preferences

click on preferences...click on moniyots.

KegHead

---

### Post by geoffm on 2011-05-02
1. There is no "System" to click on in Unity
2. The "Monitor Preferences" doesn't allow you to choose which monitor is primary.

use xrandr to find the monitor's identification then xrandr --output $monitor --primary

I don't know how to automate this at every logon though

---

### Post by Blasphemist on 2011-05-02
The tells you how to make the change dynamically, static and by session. I'm sure you want it to stay changed and this shows the 3 ways to do it. The previously shown command is one of them.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Krytarik on 2011-05-02
> **geoffm said:**
> 
use xrandr to find the monitor's identification then xrandr --output $monitor --primary

I don't know how to automate this at every logon though
See my post #5 in this thread.

---

### Post by tommyg562000 on 2011-05-02
I'm new to ubuntu, just downloaded 11.04. I'm having this same issue. Is everyone being serious when you say I have to run a script or do some command line just to choose a primary monitor? Seriously?!

---

### Post by waspbloke on 2011-05-02
> **tommyg562000 said:**
> I'm new to ubuntu, just downloaded 11.04. I'm having this same issue. Is everyone being serious when you say I have to run a script or do some command line just to choose a primary monitor? Seriously?!

I didn't have to. Just launch Monitor Preferences (gnome-display-properties from terminal) and click "make default" for the one you want to be primary.

Alternately, another way I noticed the same effect previously (assumes HDMI) was to just boot up with the one monitor you want to be primary then hot-plug the secondary monitor.

---

### Post by KFlannigan5 on 2011-07-20
> **themainliner said:**
> Easy...where is Preferences then?

^^ I like this guy :) ^^

---

### Post by mr.scotty on 2011-08-08
Hi guys,

i have found an other way to solve the prob (because i have no option to set the primary monitor in gnome-display-properties)

My setup: a ATI HD 5570, one monitor pugged in the dvi (supposed to be the primary) and one in the hdmi
EDIT: using ubuntu 11.04 natty

1. i run "xrandr" in a terminal to get the names of the monitors
in my case it showed a DFP1 and a DFP2
2. i tried the command xrandr --output $monitor_name --primary until the right monitor was set as primary
e.g. xrandr --output DFP1 --primary
still the wrong primary monitor. so i tried:
xrandr --output DFP2 --primary
bingo! But this will only set the primary monitor until the next reboot!
3. I opened the monitors.xml file (located in ~/.config/monitors.xml) in a texteditor
e.g. gedit ~/.config/monitors.xml
I changed the value of the primary tag (of the monitor I wanted to be primary) to yes (<primary>yes</primary>) and saved the file
4. reboot
5. happy end :)

Greetz
scotty86

---

### Post by vaquerito on 2011-08-30
ohhh... at last :) Thank u

> **mr.scotty said:**
> Hi guys,

i have found an other way to solve the prob (because i have no option to set the primary monitor in gnome-display-properties)

My setup: a ATI HD 5570, one monitor pugged in the dvi (supposed to be the primary) and one in the hdmi
EDIT: using ubuntu 11.04 natty

1. i run "xrandr" in a terminal to get the names of the monitors
in my case it showed a DFP1 and a DFP2
2. i tried the command xrandr --output $monitor_name --primary until the right monitor was set as primary
e.g. xrandr --output DFP1 --primary
still the wrong primary monitor. so i tried:
xrandr --output DFP2 --primary
bingo! But this will only set the primary monitor until the next reboot!
3. I opened the monitors.xml file (located in ~/.config/monitors.xml) in a texteditor
e.g. gedit ~/.config/monitors.xml
I changed the value of the primary tag (of the monitor I wanted to be primary) to yes (<primary>yes</primary>) and saved the file
4. reboot
5. happy end :)

Greetz
scotty86

---

### Post by keithclark on 2011-11-12
> **mr.scotty said:**
> Hi guys,

i have found an other way to solve the prob (because i have no option to set the primary monitor in gnome-display-properties)

My setup: a ATI HD 5570, one monitor pugged in the dvi (supposed to be the primary) and one in the hdmi
EDIT: using ubuntu 11.04 natty

1. i run "xrandr" in a terminal to get the names of the monitors
in my case it showed a DFP1 and a DFP2
2. i tried the command xrandr --output $monitor_name --primary until the right monitor was set as primary
e.g. xrandr --output DFP1 --primary
still the wrong primary monitor. so i tried:
xrandr --output DFP2 --primary
bingo! But this will only set the primary monitor until the next reboot!
3. I opened the monitors.xml file (located in ~/.config/monitors.xml) in a texteditor
e.g. gedit ~/.config/monitors.xml
I changed the value of the primary tag (of the monitor I wanted to be primary) to yes (<primary>yes</primary>) and saved the file
4. reboot
5. happy end :)

Greetz
scotty86

Thanks a bunch!

---

