---
title: "[SOLVED] Everything's going wrong!!!"
date: 2008-12-17
forum: General Help
---

### Post by Cadeyrn on 2008-12-17
I don't know what is happening to my system (Ubuntu 8.10 on a x32 Intel iMac)--ever since I first ran the Update Manager, which, by the way, keeps telling me my system is up-to-date when I know at least 100 things need updating, tons and tons of various problems have been sprouting up and it's so frustrating!!! I'll list a few here:

-Terminal refuses to start. I click on it under the apps list, the "Launching Terminal" window shows up on my window bar, and then it disappears and nothing launches.
-Biggest one: my graphics drivers are sooooooo messed up. 3D acceleration suddenly doesn't work, 2D accel is really laggy, none of the screen savers show up (which I reeeeaaaally need because I can't figure out how to turn the monitor off when I'm inactive and when it's left one, my monitor's spreading of stuck pixels (already three vertical lines of broken transistors from top to bottom of screen) gets worse)
-The graphics drivers being messed up also causes Firefox toolbars being broken and Customize having no dragging option, and it also causes me to have 0 Desktop effects, which means no dragging to other workspaces and whatnot.
-The well known methods of installing iSight and the Logitech G11/15 keyboard drivers that work for everyone else don't work for me. I know I've done them perfectly, but I'm still getting errors.
-A virtual copy of Windows XP inside of VirtualBox gets an error at every startup.
-WINE can almost never launch a program.
-THE LOGIN SCREEN IS MISSING. I cannot log out and the only way to get into any account is to set it to automatically log in and restart the computer.

That's all I can think of right now. I know there's more and there's bound to be yet more than I haven't seen yet. And these problems didn't show up all at once. They've been happening gradually, starting with the graphics drivers problem. In fact the Terminal was working fine a few minutes ago, and 3D acceleration, despite the driver problems going on at the same time, had absolutely no issues before today.

I have heard that installing the Restricted ATI Proprietary Driver fixes all of this nonsense at once (except maybe the Update Manager not updating), but whenever I install it, my computer gets stuck at a resolution of 320xsomething, and Screen Resolution claims the computer doesn't know I even have a monitor, and yes, it does know I have one without that specific driver. I have to go into Recovery Mode and use xfix to remove the driver just to get my res back. And by the way, when I do run xfix, it says nothing about anything besides a fatal change to my xorg.conf file. I think that ATI Proprietary Driver is screwing with files it doesn't understand.

EDIT: Oh! I remembered another problem: my TTY's won't start.

EDIT2: I remember another: the only website that my Linux Internet Client can handle uploading to is deviantART. I've tried many others, including ImageShack and Photobucket.

---

### Post by shane8002 on 2008-12-17
I would run a rescue reinstallation of ubuntu that might solve your problems if you start with a fresh install but remember to back up all your data that you need to keep before doing so

---

### Post by Cadeyrn on 2008-12-17
That's what I was thinking too, but resetting all of my Firefox stuff would be a huge pain. And I don't have the internet speed to spend 24 hours downloading all of the Add/Remove Programs Programs I want AGAIN.

---

### Post by Ms_Angel_D on 2008-12-17
Sorry I can't be of assistance to your main problem however I can suggest three great extensions for firefox that I use to keep backups of my settings, bookmarks, & form information.

[Foxmarks]("http://www.foxmarks.com/") (Backs up your bookmarks online)
[FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109") (Will back up your entire firefox profile including all your installed extensions, preferences, Bookmarks, Search Engines and themes)
[Sxipper]("https://addons.mozilla.org/en-US/firefox/addon/4865") (Password form fill manager with backup and restore feature)

Trust me those 3 extensions alone will save you a lot of headache in the long run.

Good luck and I hope you can get some help in resolving your main issue.

---

### Post by Cadeyrn on 2008-12-17
Hmm... Well, alright. Maybe I should backup all of my stuff and reinstall Ubuntu. I can always wait a few days for when I'll have faster internet to regrab my programs, not to mention this way I'll be forced to install through Boot Camp, so Mac should recognize the Linux side.

---

### Post by Cadeyrn on 2008-12-19
The reinstall made it perfectey :D

---

