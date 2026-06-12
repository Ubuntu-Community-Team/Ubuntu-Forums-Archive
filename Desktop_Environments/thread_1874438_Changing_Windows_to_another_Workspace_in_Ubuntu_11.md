---
title: "Changing Windows to another Workspace in Ubuntu 11.10"
date: 2011-11-03
forum: Desktop Environments
---

### Post by lads on 2011-11-03
Dear all,

In the previous versions of Ubuntu I was used to move windows across Workspaces by right-clicking the top bar and choosing *Move to Another Workspace* > *Workspace X*. This option still exists in Ubuntu 11.10 but if I use it the window simply disappears (though I suspect the corresponding process remains active). I tried to activate the Put plug-in for Compiz so I could define keyboard shortcuts for these actions. I tried with several different key combinations but it doesn't work. The only way I can move windows across workspaces is by dragging them with the mouse, which only allows to move windows from workspace 1 to 2 and from workspace 3 to 4.

So the question is: how can one move windows across workspaces in Ubuntu 11.10 without dragging them.

Thank you.

---

### Post by lynrock on 2011-11-03
This is still working fine for me in 11.10. My only thought is that I have changed virtual desktops to Horizontal Size 4; Vertical 1, which is the traditional Gnome 2 setting. (This is in General Options in CCSM). Perhaps it makes a difference.

---

### Post by lads on 2011-11-08
I also tried to set these shortcuts in the traditional Keyboard menu, again to no effect. I tried these shortcuts in different workspaces and there's simply no reaction.
 
But the most enigmatic thing of all is the right click -> Move to Another Workspace mouse command closing the window (or sending it to some sort of limbo). This worked very well on Ubuntu 11.04, also with Compiz, why has it changed to the newer version?

---

### Post by PineGroveDave on 2011-11-08
I've got the same problem. Fixed it by changing the "Number of Desktops" to 1 instead of 4 under the General Options of CCSM. Keeping the Horizontal Virtual Size to 4 still left me w/ 4 desktops.

---

### Post by lads on 2011-11-09
Thank you Dave that solved my issues too. 

I have been having a host of similar problems since I updated to Ubuntu 11.10 and they all seem to be caused by an overlapping of configurations between CCSM and the traditional Settings menu. In further versions it would will nice if the window manager is configured at a single place.

Best.

---

