---
title: "Top panel unity?"
date: 2012-07-08
forum: Desktop Environments
---

### Post by javajames79 on 2012-07-08
Back in 10.04 LTS with gnome the top panel could be edited to add and remove features from it. Now i've come across a bug in 12.04 where hitting the switch accounts button causes a system wide crash (thats seperate but if you do know a fix then please do - radeon 6870 card.) The problem is that often i'm moving around the workspaces pretty quickly and sometimes if i need to access the system settings tool or time, or just something that happens to be up there, i can nudge the mouse a little and put my whole system to death. (only curable with a restart.) 

Does anyone know how i can remove the accounts panel of the top bar in unity?

Thanks in advanced.

---

### Post by Frogs Hair on 2012-07-08
You can try the following. Install the Dconf Editor from the software center. Open the application from dash, select apps > indicator session, remove the checks from show real name in panel and user show menu. Close the application and logout and back in. I have tested this in Unity but this won't work in the Gnome environments.

---

