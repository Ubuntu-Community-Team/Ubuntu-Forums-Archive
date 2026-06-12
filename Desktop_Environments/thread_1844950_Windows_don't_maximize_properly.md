---
title: "Windows don't maximize properly"
date: 2011-09-16
forum: Desktop Environments
---

### Post by deltaPrime21 on 2011-09-16
I have a dual monitor setup on Ubuntu 11.04 with the Unity interface. I am currently experiencing two problems with maximizing windows:
 
1. On my primary display, a maximized window will show up behind the launcher. I set the launcher to never hide. The interesting thing is if I only have one monitor, the maximized window will only take up as much of the screen not occupied by the launcher.

2. On my secondary display, a maximized window will fill all screen space vertically, but only a tiny column on the left side of the screen.

The attached image shows a maximized window on the primary display (right side) and a maximized window on the secondary display (left side). I have recently been tweaking some settings in Compiz (CCSM) and Ubuntu Tweak. I wonder if one of the changes caused this behavior. I've tried to undo all of it to no avail.

Any ideas?

---

### Post by Frogs Hair on 2011-09-16
Hi and Welcome 

I have found with Unity that when application widows exceed a certain size on my monitor it wants to use the whole screen . My work around has been to manually resize the window close and open the application . Once done the applications open normally . The only applications that are affected in my case are the web browsers . It is possible experimenting with Ubuntu Tweak has caused a problem , but you would need remember what you did to correct it .

---

### Post by deltaPrime21 on 2011-09-16
Thanks for the reply. I ended up restoring every setting in Ubuntu Tweak to the default (Desktop Recovery -> click Reset for each Category). Then I reset unity and unity launcher icons:

```
unity --reset
unity --reset-icons
```After a reboot, the problems were fixed. So I went back to changing some settings to see what was causing the problem. I found out it was the Launcher Autohide/Never hide options. When it's set to Autohide (or Dogde), I have no problems. But, when it's set to Never hide, the secondary monitor won't maximize the window properly (it fills up a thin column on the left side of the screen when maximized). That answers issue #2.

As I mentioned before, issue #1 is only a problem with dual monitors as well.

It seems like I found two bugs related to the Unity launcher being set to never hide and having dual monitors. Is this something I should report? If so, how would I go about doing that? 

Note: In case you are wondering, I set the launcher autohide/dogde/never hide property is CCSM > Desktop > Ubuntu Unity Plugin.

---

### Post by Copper Bezel on 2011-09-16
You can file a bug [_here_]("https://bugs.launchpad.net/ubuntu/+source/unity"). The problem on the lefthand, secondary display is unusual. The problem on the righthand display, that the primary desktop's work area size isn't set properly when using a second monitor on that side and thus that windows extend behind the panel, is an old one in Gnome 2 and apparently hasn't been fixed, so with the shift to Gnome 3 in the next Ubuntu release, I wouldn't have much hope for it being fixed.

---

### Post by deltaPrime21 on 2011-09-17
Thanks.

---

### Post by deltaPrime21 on 2011-09-23
Another follow-up to this: I found that when my left monitor is set to primary, windows maximize correctly on both monitors. The problems I was having seems to only happen when the right monitor is set to primary.

---

