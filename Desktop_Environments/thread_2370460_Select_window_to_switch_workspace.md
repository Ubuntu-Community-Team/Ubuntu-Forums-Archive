---
title: "Select window to switch workspace"
date: 2017-09-03
forum: Desktop Environments
---

### Post by poutrygiest on 2017-09-03
I am using Ubuntu 16.04

When I select a window from the sidebar I would like it to switch to the workspace it is on so I can use this window. Currently it will give focus to the window but if it is present on a workspace I am not on this is not useful.

Which setting allows a focused window to force the workspace switch?

---

### Post by lammert-nijhof on 2017-09-03
The force a workspace switch right click on the window title bar and select the workspace where you want to move the window to. The choices are 'move to workspace right', 'move to workspace down' or ' move to another workspace' by number.

---

### Post by poutrygiest on 2017-09-04
I mean when you switch to another application I want it to automatically switch the current workspace to the workspace that application is present on.

Currently it switches focus to the application but since the window is on another workspace I have to manually switch to the workspace to be able to use it.

---

### Post by lammert-nijhof on 2017-09-07
Well in my Ubuntu 16.04 system, when I click the icon in the launcher of a loaded program, it automatically switches to that application and workspace. However you have to start the program in the right workspace or you start it and move it to the right workspace afterwards.  You can't assign a default workspace to a program, probably you can do something with scripts. Google for "ubuntu default workspace for a program".

---

### Post by deadflowr on 2017-09-07
> However you have to start the program in the right workspace or you start it and move it to the right workspace afterwards. You can't assign a default workspace to a program, probably you can do something with scripts. 

No need for a script.
You can set apps to open in specific workspaces any time you start them.
Use ccsm (compizconfig-settings-manager) and go to Place Windows. 
Open the tab marked Fixed Window Placement.
Then go down to Windows with Fixed Viewport.
Then add the window  and set the x and y to the specific workspace/viewport.
As long as the app name is correct it'll open in that set workspace forever on after.


Per the thread, sometimes workspaces and apps can conflict if the app's window overlaps workspaces.
example: say you have a window in x1y1, the top left, but it overlaps into x1y2, the bottom left, (if we use the standard 2X2 workspace layout Ubuntu uses)
if you where in x1y2 and then tried to click on the apps launcher to move into x1y1, it will fail because the apps overlapping makes it so you where already in a workspace with the app.
And it only takes a pixel width.
If that makes sense.

Not that this is the issue at hand, but is something that can happen.

---

