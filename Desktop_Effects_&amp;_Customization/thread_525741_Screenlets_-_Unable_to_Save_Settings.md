---
title: "Screenlets - Unable to Save Settings"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by Mike_88 on 2007-08-14
I have Screenlets up and running fine on my system, and am using a variety of different screenlets that load at startup.  The only problem that I have is that a couple of them (Weather and Calendar) do not retain their settings after I change them (i.e., size and location).  As a result, after I reboot they return to their original appearance and location on the screen.  The other screenlets work fine and retain their settings upon rebooting.

As an example, here's the output I get when I try to run the Weather screenlet from the terminal:

> mike@mike-laptop:~$ /usr/local/share/screenlets/Weather/WeatherScreenlet.py
UPDATING SHAPE
UPDATING SHAPE
Unable to find settings-backend! Options will not be saved.
'WeatherScreenlet' object has no attribute 'backend'

Anybody have an idea as to what I can do to fix this?  Thanks.

---

### Post by Solvax on 2007-08-15
I got the same problem as you do,
I got the vista-bar up and running through the terminal,
though i get the same message.
To make this load at login, do I have to put it in a startup script?
And what should I put in it?

Greetz

~solvax

---

### Post by Solvax on 2007-08-15
This is how my desktop looks at the moment...
As you see i access the screenlets through the menu,
though when clicking on a screenlet it just won't start...
The only screenlet that actually works is the sidebar...
Any tips?


Greetz 

~ Solvax

[IMG]http://img483.imageshack.us/img483/9935/snapshot1ej9.png[/IMG]

---

### Post by Mike_88 on 2007-08-15
Bump.

---

