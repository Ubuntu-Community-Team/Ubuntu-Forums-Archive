---
title: "Workspace switching actions al out of sync, losing workspaces and windows"
date: 2009-05-14
forum: Desktop Environments
---

### Post by seanmacaodha on 2009-05-14
A Chairde,
 I've recently made the switch from the nagging overly complicated bloated windows Vista to ubuntu. It was my intention on switching to opensolaris, but live cd wouldnt boot into 64bit mode for me.. anyway, ive been happy with the whole experience up until a few hours ago.

Heres the situation, for some reason (maybe a bug?) , each time i use different ways to move windows to different workspaces, i seem to loose workspaces/windows/panels on the way.

Heres a sample scenario.

On workspace 1, ie the first one loaded up on boot.
I start netbeans
using the Ctrl+Alt+Right sequnce i move to the workspace 2, imediatly to the right of it,
i start banshee
i then start mysql query browser, i right click on the application icon in the title bar and click "send to workspace -> desktop 3"

at that point mysql query browser, disappears. if i use the keyboard sequences to move to workspace 3, there is no windows there.

now, lets make this worse,

using other methods of moving windows, say dragging to the edge, then using the panels workspace switcher to move to a workspace then start another app there, 
i loose access to all the other workspaces.

i can sometimes get back to my applications by changing the window list preferences to show all windows on all workspaces, but sometimes, actually, more often, the list doesnt update to show all the windows. 

its as if the whole virtual workspace system is out of sync. or one set of tools is working with oneset of workspaces and the other with another...

in the past hour, ive had to restart 3 times!

so in short, has anybody else experienced this? is there a known bug? (i googled to no ends)

Le Meas, 
Seán

Details:
Ubuntu 9 (Jaunty) [just installed]
NVidia GeForce Go 7400 (driver installed with compiz enabled, 512MB dedicated)
Intel Core 2 Duo @ 1.5Ghz (in 64bit mode)
1GB RAM

---

### Post by john.nicholls on 2009-05-15
This may or may not help, but Compiz can give strange results with workspaces unless you use the following settings in CompizConfig Settings Manager:

In General | General Settings | Desktop Size,
Horizontal Vertical Size 4 (if you're using 4 workspaces)
Vertical Virtual Size 1
Number of Desktops 1

---

