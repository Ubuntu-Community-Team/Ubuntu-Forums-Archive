---
title: "workspace separation problem"
date: 2010-01-05
forum: Desktop Environments
---

### Post by slowtrain on 2010-01-05
My Gnome desktop has a workspace separation problem--the six workspaces I have are being treated as one running space for some purposes and this is creating problems.  For example, the Window Selector does not show windows in separate workspaces separately but all together.  Also, when I move a window partly offscreen, part of it appears in an adjacent workspace, which gets to be rather messy.  

Anyone have any ideas on what might cause this and how it might be fixed.  The problem began when I had one too many system crashes after installing a PCI wifi card in system 9.04.  I've since upgraded to 9.10, but the problem followed me.  I suspect some system preferences got scrambled somewhere.

---

### Post by tpjk on 2010-01-06
try right clicking the window selector (the little dots in the taskbar left of the list of open windows). go to properties; tick the radio button next to where it says 'only show windows from current workspace' (or something along these lines).

as for the windows overlapping into adjacent workspaces - try going through your compiz settings and see if there's an option there that'll prevent them from doing that.

hope this helps.

---

### Post by slowtrain on 2010-01-06
Hi tpjk:  These are some thoughtful suggestions, and the preference menu for the window list (buttons) is a very useful one I hadn't known about before (I love the grouping option).  Regrettably, nothing works for my problem.  The preferences are already set to showing only windows from the current space.  And, indeed, that is what happens--for the buttons.  The Window selector, however, shows an unseparated list of windows for all workspaces.

On your suggestion, I also tried altering a dozen or more different Compiz settings (running "gconf-editor" in the terminal).  One thing that helped a bit was apps > compiz > plugins > wall > screen0 > options > edgeflip_move .  Deactivating that prevents me from (annoyingly) shifting to a different workspace when I move a window to the edge of the screen.  Beyond that, I still haven't made a dent in my main problems.

I thought I had probably found the solution when I found that my apps > screen0 > options > number_of_desktops was set to 1.  I reset it to 6, but this seems to have had no effect, even after reboot.  I played a bit w/ outputs, which are currently set to 1280x1024+0+0, but I don't really know what settings that should have.

---

### Post by tpjk on 2010-01-06
do you have compiz config settings manager installed? because that's what i meant when i said go into your compiz settings ;)

if not, go into synaptic and and install the package called compizconfig-settings-manager.
alternatively, open up a terminal and type

```
sudo apt-get install compizconfig-settings-manager
```

once installed, the manager can be found under system -> preferences -> compizconfig settings manager.

in the window management section, click 'put' and then go to the 'misc options' tab. enable 'avoid offscreen'. you might also want to disable the 'snapping windows' feature.

---

### Post by tpjk on 2010-01-06
sorry, double post

---

### Post by slowtrain on 2010-01-13
Hi again tpjk:  I tried compizconfig-settings-manager.  You'd think disabling offscreen would at least stop my windows from appearing in the next workspace when they are partially off screen.  Nope, didn't affect a thing--everything is the same.

I suspect my problem may be more basic than compiz.  Here's why:  on my work ubuntu desktop, the setting in compiz that prevents my screen from flipping to the next workspace when I drag a window over the edge with my cursor is not switched on.  So, you'd think that I'd flip workspaces when I did that dragging, but I don't.  Yet, on my home machine where I'm having these workspace separation problems, I do have that problem unless the compiz alternative is turned on.  So, it looks like something is overriding the compiz settings on my work machine.  Maybe X settings?  I suspect these settings may account for the problems I'm having.

The overall problem is that my home desktop seems to be treating the workspaces as one continuous desktop, while the work machine is treating them as separate workspaces.

Sigh!

---

### Post by tpjk on 2010-01-14
> **slowtrain said:**
> So, it looks like something is overriding the compiz settings on my work machine.  Maybe X settings?

i still have my money on compiz - try playing around with the wobbly windows plugin and settings. if you haven't already you could also install the package simple-ccsm; it's another settings manager for compiz and a lot easier to use.

---

### Post by t.h.w. on 2010-03-28
Hi!

Funny, I have the problem the other way around...
I cannot disable the radio-button 'Only on this workspace'.... very annoying.

Any suggestions?

---

### Post by nndurj on 2011-05-07
I enabled 'avoid offscreen' and now the workspaces are separate. Moving a window to the screen edge will not get it to any other workspace.

To enable 'avoid offscreen', go to terminal and type 'gconf-editor' and press enter. Search for 'avoid_offscreen' (make sure you have checked 'search also in keynames'). check the option and your are done.

---

### Post by Copper Bezel on 2011-05-07
That's part of the Put plugin, but it has to be invoked by a keystroke (which arranges the open windows on the present workspace according to certain rules.) 

I think you're talking about disabling edge flipping, so that windows can't be moved by dragging them off the present workspace, but that's not really what this old thread was about. In Compiz, windows stretch from one workspace to another instead of cutting off at the edge of the workspace, and some users prefer the other way of handling workspaces. This is, however, a fundamental difference between how Compiz and Metacity/Mutter each handle workspaces and can't be changed.

---

