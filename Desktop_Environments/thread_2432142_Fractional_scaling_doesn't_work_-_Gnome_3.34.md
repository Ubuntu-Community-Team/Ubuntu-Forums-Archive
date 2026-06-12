---
title: "Fractional scaling doesn't work - Gnome 3.34"
date: 2019-11-27
forum: Desktop Environments
---

### Post by lama1234 on 2019-11-27
Hi everyone, 

I'm struggling with the fractional scaling feature in gnome. 

My current setup:
Display1: 2736x1824  (on a surface pro 6)
Display2: 1920x1080
Display3: 1920x1080

I've configured the scale for Display1 to 200%. But the current is dissappointing.
I've tried following scenarios:

_Display1 scaled to 200%, Display2/3 to 100%, primary display = Display3:_
Windows are correctly display on Display2/3, Display1 doesn't scale anything except gnome-own applications.
The surface screen looks like this:
[IMG]https://i.imgur.com/gYE81bS.png[/IMG]

_Display1 scaled to 200%, Display2/3 to 100%, primary display = Display1:_
All looks good on the surface now, all applications are scaled correctly. But all windows on display2/3 are scaled double, except gnome own application...
The surface screen looks like this:
[IMG]https://i.imgur.com/esOEMnD.png[/IMG]

Display3 looks like this 
[IMG]https://i.imgur.com/N5qHH1P.png[/IMG]

_Display1 scaled to 200%, Display2/3 not connected:_
All is working fine!

I've already deleted the ~/.config/monitors.xml to give it try.
And the surface was rebooted many times.

Any ideas how to solve the issue? 

A friend of mine has the same setup and it works for him. We didn't find any difference in our setup. 

I'm completely lost for now, any help would be great!

Greets, 
Oliver

---

### Post by DJ_Max on 2020-01-03
Were you able to get anywhere with this? I just got a dual monitor setup, and I can't even get one monitor to run at 100% scale with the other at 200%. Don't know what I expected, I've been using Linux long enough

---

