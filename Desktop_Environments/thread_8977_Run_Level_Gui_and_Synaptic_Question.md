---
title: "Run Level Gui and Synaptic Question"
date: 2004-12-22
forum: Desktop Environments
---

### Post by jts on 2004-12-22
A couple of questions.  

1.)  Is there some sort of Run-Level editor to start/stop running daemons (Similar to the Services of Windows)?  RH9 and Suse have one, I believe.

2.) Are new programs automatically assigned menu icons  in Gnome (either in "Applications" or under "Computer"?  Ie. I've just installed a few programs and none of them appear.

---

### Post by randy on 2004-12-22
1.  It's part of gnome-system-tools and it is available in Hoary I think.  I know it was disabled by the developers due to a couple of bugs.

2.  No applications aren't automatically assigned menu icons.  They files that are stored in /usr/share/applications

---

### Post by jts on 2004-12-23
Stupid question, but how do I enable it (Run Level Editor)?

Also,  are there any tools/programs to would actually auto add the icon to the menu list?   

I'm not that familar with synaptic, but I can see how this would confuse new users to Ubuntu (like me  :p  ).    Especially, if you add/remove alot of programs for testing out new software.

---

### Post by varunus on 2004-12-23
Most X applications that you get from Synaptic should add themselves to your menu.  Not all applications do though...for some (terminal utilities, other window managers), it doesn't make sense.  But most stuff should add itself...try running "update-menus" from a terminal and see if that helps.  Or reload the gnome panel.

---

