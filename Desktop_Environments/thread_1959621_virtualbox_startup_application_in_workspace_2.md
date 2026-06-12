---
title: "virtualbox startup application in workspace 2"
date: 2012-04-16
forum: Desktop Environments
---

### Post by madhusudana y n on 2012-04-16
Hi all,

I have virtualbox running on my ubuntu 11.10. I have created virtual windows 7. I want to start windows 7 in full screen mode in workspace 2 on system startup. How to do it?

I have compiz installed. I did enabled "place windows" and added an entry in add viewport place with option like "windows_xid=virtualbox --fullscreen --startvm win7"

it did not start win7 on reboot.

then I added an entry for same command in "startup applications" window. on reboot, win7 started, with one launch icon in workspace 1 and another in workspace 2. i went to workspace 2 and clicked on launch icon, the window switched to workspace one and opened win7.


I removed all above config and installed devlspie. configured throuh gui as "set_workspkace" to 2, spawn_sync to "virtualbox --fullscreen --startvm win7". i did not work.( i assume its because of existence of compiz).

i installed wmctrl. it was too complex to understand and configure so i did not do anything on that.


pls someone help me getting over this:). 

thanks,
Madhu

---

### Post by mcduck on 2012-04-16
The "Place" plugin in Compiz is not even supposed to start anyhting for you. It simply matches a window ID (or other appropriate identifier) and places an existing window based on that. So, to use it, you need to add the command you use to start Virtualbox into Startup Applications, and then add a correct line to match with the window in the Place plugin.

---

### Post by madhusudana y n on 2012-04-18
> **mcduck said:**
> The "Place" plugin in Compiz is not even supposed to start anyhting for you. It simply matches a window ID (or other appropriate identifier) and places an existing window based on that. So, to use it, you need to add the command you use to start Virtualbox into Startup Applications, and then add a correct line to match with the window in the Place plugin.

I have done that. But as i said above, it doesn't work as intended. though virtual win7 starts up, it doesn't move to workspace 2 automatically. only the dock launcher moves to workspace2. on clicking the launcher, the window switches back to workspace 1 and then opens up.

---

### Post by mcduck on 2012-04-18
> **madhusudana y n said:**
> I have done that. But as i said above, it doesn't work as intended. though virtual win7 starts up, it doesn't move to workspace 2 automatically. only the dock launcher moves to workspace2. on clicking the launcher, the window switches back to workspace 1 and then opens up.

What kind of entry you acxtually have at the moment in the COmpizx plugins to match the window and move it to right place?

If it's the one you mentioned in your first post, that's not going to work. The window ID is not the same as the command you use to start a program. Actually, CompizConfig Settings Manager should have a button you can click and then click on the window you want to automatically grab the coprrect code to match to that window...

---

