---
title: "More than 1 Cairo Dock"
date: 2014-09-12
forum: Desktop Environments
---

### Post by WB0HYQ on 2014-09-12
I am extremely happy with my move to Xubuntu (xfce4) from plain-jane Ubuntu.  I've installed Cairo-dock and love what I can do with it.  I am stumped for the reason I have more than one Cairo dock when I boot up or logout/logon.  When I do either of those, I end up with Cairo-dock and another (sometimes two) UNDER the primaryu Cairo dock.

I can easily grab one of them and, using Alt-Drag, pull it (them) out of the way and use "Quit" to kill it (them).  What I don't understand is why I have more than one.  I've gone to the "session and startup" and unchecked every instance of "Cairo-dock" (there were two - one just labeled as 'Cairo Dock' and the other labeled as "Cairo Dock the wonderful, animated, etc, etc.).  Both are now unchecked, yet I still get two (or more) of these docks.

Any idea what is happening, or where to look for other instances of this great dock starting when I don't want it to?

Bill

---

### Post by Frogs Hair on 2014-09-12
I had a similar problem in XFCE with Dockbarx. I found that if I cleared any saved desktop sessions in window manger tweaks the duplicate dock would be removed on restart. I am currently in the Cairo Dock session but using Ubuntu.

---

### Post by WB0HYQ on 2014-09-12
Hmmm.  I can't find anything having to do with sessions in 'windows manager tweaks' nor are there any I can find in 'Ubuntu Tweaks'.  The only thing I can find is called session and startup.  There is a tab named 'sessions' that has a 'clear all saved sessions'.  I've used that, but I always have two (or more) cairo docks when I restart/logout-login.

Bill

---

### Post by Frogs Hair on 2014-09-12
> [COLOR=#000000]The only thing I can find is called session and startup. There is a tab named 'sessions' that has a 'clear all saved sessions' [/COLOR][COLOR=#000000]Excuse me, that is what I was thinking of .[/COLOR]

[COLOR=#000000] Back when I started using Ubuntu I remember the same thing happening and removing the Cairo Dock profile file folder in hidden folders and reinstalling the dock solved the problem. The folder is located in .config in Nautilus but I'm not sure about Thunar. There might be a better way so you might want to wait for others to respond before doing that.[/COLOR]

---

### Post by WB0HYQ on 2014-09-12
I have been fiddling around with the 'clear all saved sessions' button.  I have managed to clear all the sessions, make sure that there is ONLY one Cairo Dock, and then click the "Save session" button.  Then, in the "General" tab, I've UNchecked 'automaticall save sesson on logout'.

When I logged out, and logged back in, I had ONE Cairo dock.  I rebooted and still had only one.  So, maybe I've managed to fix it.  But, in the 'Application Autostart' tab, there is no mention of Cairo Dock - yet one starts up.  I wonder where that command is coming from.

I am in the process of examining several .config and startup files to see if it is contained there.  I agree that maybe someone else will drop in here and give me a heads-up.

Bill

---

