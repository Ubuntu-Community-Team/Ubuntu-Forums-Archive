---
title: "How do I ditch workspaces in 12.04"
date: 2012-04-30
forum: Desktop Environments
---

### Post by shieldw0lf on 2012-04-30
I find workspaces to be nothing but an annoyance.  I'd like to remove the extra workspaces and remove the workspace switcher from the dash.  How can I do this?

---

### Post by StApnea on 2012-04-30
I would recommend setting the number of workplaces to 1 and disabling the Expo short-cut key. You can't disable expo it self because the Unity plug-in depends on it. I don't have the faintest clue how to remove the Dash key. Probably somewhere out there in a file there is a line that specifies, but I don't know what it is.

Pardon me if you already know the below.
To do above use Compiz Config Settings Manager The package is ccsm if you like to install with apt-get. You can find it in the software centre by searching Compiz.

Compiz controls a large portion of your desktop, so you want to be careful. When you open it, it warns you about not touching stuff and it means it. If something goes horrible wrong open a terminal window (or if things are so terrible that you can't do that, press control-alt-F1) and enter unity --reset. That should fix everything.

To make there only one window, open Compiz Config Settings Manager and click on General settings. The last tab is desktop size. Change the horizontal and vertical size to 1. 

To disable keyboard shortcut click on Desktop (above Effects) and click on Expo. Top choice is Expo key, click on the keyboard shortcut box and uncheck expo. Don't disable the plugin, bad things will happen.

---

### Post by shieldw0lf on 2012-05-01
Thanks.  Now if I can just get rid of that useless button...

---

### Post by mc4man on 2012-05-01
> **shieldw0lf said:**
> Thanks.  Now if I can just get rid of that useless button...
If you are referring to the workspace switcher icon in the 'launcher' then after setting Ws's to 1 just log out/in. It will be gone

---

### Post by przekop on 2012-05-31
Is there any other way to hide switcher? Spread no longer works after setting 1 workspace.
[https://bugs.launchpad.net/compiz-core/+bug/996604](https://bugs.launchpad.net/compiz-core/+bug/996604)

---

