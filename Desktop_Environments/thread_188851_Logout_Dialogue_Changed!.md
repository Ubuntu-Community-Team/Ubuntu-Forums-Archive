---
title: "Logout Dialogue Changed!"
date: 2006-06-04
forum: Desktop Environments
---

### Post by joshpelkey on 2006-06-04
Hello,

I recently did a "dpgk-reconfigure xserver-xorg" and everything was fine except for my logout dialouge (the one that comes up when you choose System > Quit).  So I copied my old xorg.cfg over my new one and restarted X to see if the problem would go away.  It did not.  I wish I could attach a screenshot of what the dialogue looks like, but print screen doesn't work after I select quit.  I'll try to describe it:

The window comes up with Log out, Lock Screen, and Switch user in the top half.  On the bottom half is Suspend, Hibernate, Restart, Shutdown.  The only one that has an icon with it is Lock screen.  None of them appear as buttons unless you hover over the word.  Finally, in the lower right hand corner is cancel and it appears fine (just like a regular button).

Any ideas? Thanks.

Josh

---

### Post by sarbor77 on 2006-12-06
It seems that this is a common problem - with no solution!!!

I have tried: *"Go to the top menu - system - preferences - sessions. The pop up window should have a check box labeled "Ask on logout"."* with no luck...

I have tried editing "/etc/X11/gdm.conf-custom" and "/etc/X11/gdm.conf" according to: 


> The fix (from [http://forum.beryl-project.org/topic-4863-1](http://forum.beryl-project.org/topic-4863-1) ) was to add to **/etc/gdm/gdm.conf-custom**:

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

and to make two changes in **/etc/gdm/gdm.conf**. 
First replace "0=Standard" with "1=Standard" 
then set GdmXserverTimeout=50 (around line 200). 

The catch is that this takes away your ability to fallback on a non Xgl login.

from [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")
 (Many people have left comments in this blog to him).

**Do I have to do something to activate the changes??? **(I remember something from using RED HAT 6, about a command that had to enter, after doing changes. Maybe it was only after making kernal changes...)


I also found "SIMONN" comment at: [http://www.ubuntuforums.org/showthread.php?t=188162]("http://www.ubuntuforums.org/showthread.php?t=188162")
which looks almost the same... I haven't tried it yet.

---

### Post by sarbor77 on 2006-12-06
Problem solved... I don't know how, but read: 
[http://www.ubuntuforums.org/showthread.php?p=1851910]("http://www.ubuntuforums.org/showthread.php?p=1851910")

Good Luck to all others!

// Sara

---

