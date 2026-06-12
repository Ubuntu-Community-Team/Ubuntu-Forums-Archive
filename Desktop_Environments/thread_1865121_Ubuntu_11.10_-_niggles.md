---
title: "Ubuntu 11.10 - niggles"
date: 2011-10-19
forum: Desktop Environments
---

### Post by Mobby on 2011-10-19
Hi,
  I was just wondering whether anyone else has seen the same sort of issues as me? Those being...

[LIST]
[*]Login Screen (lightdm) is very stuttery when changing/scrolling through accounts. Generally slow.
[*]With NVidia Driver enabled - performance is smooth except when dragging a window. If I move slowly the movement is fine. If I drag quickly the window doesn't move and then it just snaps straight to where the mouse has stopped.
[*]Dash is not always able to find applications. I've not actually seen this one in the last day or so, it may have been fixed in the last batch of updates so might be able to ignore this one. 
[*]Dash does not always react to quick typing. Sometimes I can hit super, type "chro" and hit enter and dash doesn't quite get all the key presses. 
[*]System resource usage is higher in 11.10, especially memory.
[*]Boot time is noticeably slower than 11.04
[/LIST]

In general I'm liking 11.10 over 11.04 but I must admit that 11.04 felt snappier. Hopefully the updates over the coming days/weeks will improve this and resolve some of these initial hiccups.

Cheers,
Mobby

---

### Post by Mobby on 2011-10-19
Something else I've just noticed is that when changing the mouse pointer sensitivity and acceleration (dragging the slider) I can hear my hard drive read/writing like the clappers. The HDD IO stops when I stop adjusting the slider.

Maybe a bug? Doesn't sound very healthy... Anyone else get this?

Cheers,
Mobby

---

### Post by notgoingbackto_ms on 2011-10-19
Hello,

Yes I have been experiencing some of what you mentioned. I upgraded to 11.10 yesterday. 11.4 was on par speed-wise with windows xp - dual boot.  This version works but everything has a 'delay' to it. That is my main concern at this point. I click on something and it sometimes will not start for 3-5 seconds. Basically everything about it is slower, almost as if something is running in the background that I cannot detect with the system monitor. The system monitor shows nearly 100% cpu usage, so I installed the system load indicator and the CPU usage does not show this high usage. I am starting the session with Unity 2D, and the lag is still there. I click on the Dashhome and it takes 3 to 5 seconds to start. To shut the computer down takes longer as well.   I was using classic Gnome in 11.4 - I am giving myself time to use Unity before I judge it. 

AMD Athlon Barton 2500
Abit NF7
1.25gb ram
Radeon 9600 128mb / dual monitors both at max resolution

I did not install a graphics driver, left what was installed on the upgrade. Seems it should not be this slow.

---

### Post by notgoingbackto_ms on 2011-10-20
I found that the problem was a USB issue with this old machine. I have an add on PCI USB card and a motherboard connected USB adapter. I removed the DLINK wireless adapter from the PCI USB card (which also had the mouse transmitter attached), and plugged into the other USB adapter and the 11.10 system returned to normal snappy speed - go figure. I have the latest USB drivers, but have had this problem before.

---

