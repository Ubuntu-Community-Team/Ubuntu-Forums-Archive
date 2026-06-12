---
title: "Compiz Workspace Problem"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by Ryan H on 2007-10-07
I recently installed Gusty Gibbon 7.10 Beta. I have Compiz-Fusion all set up and everything is working perfectly. Except for one small, annoying, problem. In the program CompizConfig Settings Manager (CCSM) I have it set as:
Horizontal Virtual Size: 4
Number of Desktops: 4
With the settings like this I can use the Cube (And it has four sides) and Expose. The problem is, Gnome and Compiz treat the Workspaces differently.

I have four workspaces shown in the bottom right hand corner. Whatever workspace I currently have selected from that box is the workspace that is shown on all four sides of the Cube, and all frames of Expose. To better explain it, I could have any number of applications spread out among the Workspaces, but it would only show the current workspace. One side of the Cube would show the workspace, and the rest would show the same workspace, but with everything minimized.

Now if I move windows around via Expose or the Cube, then they show up on different sides of the Cube and Expose like they are supposed to, but they don't show up in different Workspaces in the bottom right hand corner (Which would be how Gnome does it.) They also all appear on the same taskbar, which I don't want.

Is there anyways to get these two separate Workspaces to work together? So that Workspace 1 is one face of the Cube, Workspace 2 is another, etc?

If anyone needs pictures or further explaining, I can.

Thank you for your help!

-Ryan H

---

### Post by Forlong on 2007-10-07
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) &#8594; Getting the cube

---

### Post by Ryan H on 2007-10-07
I have the cube. To elaborate, I mean that each individual Workspace in Gnome, has four Virtual workspaces in Compiz. So Workspace 1 has its own cube, completely seperate from Workspace 2. And all the applications in a virtual workspace appear on the same taskbar.

There's a diagram in the attachments of what I mean.

-Ryan H

---

### Post by Forlong on 2007-10-07
Yeah, I heard what you were saying. The guide covers that:
> we have to increase the number of the virtual desktops to **4** at **General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size**
(the other two options have to be left at **1**)

---

### Post by Ryan H on 2007-10-07
OMG!!! I LOVE YOU! :-D

That's exactly what I wanted! The only slight problem now is I can't click and drag windows to and from Workspace to Workspace. Like I used to be able to click the window from the bottom right corner and drag it to another one, now I can't. Not a big deal, but if you have some more Compiz kung fu that would fix this I would be so happy.

Edit: I just found out recently opened windows appear in the taskbar of all Workspaces. Even though I have it set to only show applications from that workspace.

-Ryan H

---

### Post by MeanderingCode on 2007-10-08
Forlong, my hat's off to you.  I just followed your guide, and i thank you verily.

Ryan, i'm having a similar problem.  What do you mean when you say that recently opened windows appear in the taskbar of all workspaces?  Where's that stated?

I can drag windows around just fine, but i have all windows listed on the taskbar of all workspaces.

Just to state it:
Compiz:
  Horiz. Virt. Size = 4
  Vert. Virt. Size = 1
  Number of Desktops = 1

KDE:
  Number of desktops: same effect for 1 or 4
  Taskbar: when 4 desktops => uncheck "show windows from all desktops"

I don't think it's relevant, but this happens whether i have "emerald" or "kde-window-manager" in the "command" text field of the "window decorations" plugin.

I'd like to solve this, for productivity's sake.

Thanks again, Forlong.

Sean

Edit: i know it says dapper in my lil' blurb corner, but that's not the machine i've got this running on.  Thx.

---

### Post by Forlong on 2007-10-08
> **Ryan H said:**
> The only slight problem now is I can't click and drag windows to and from Workspace to Workspace. Like I used to be able to click the window from the bottom right corner and drag it to another one, now I can't. Not a big deal, but if you have some more Compiz kung fu that would fix this I would be so happy.
Go to Rotate Cube and make sure **Edge Flip Move** is enabled.


I'm not sure about the *show windows from all desktops*, though. I can't confirm such behaviour here.

---

