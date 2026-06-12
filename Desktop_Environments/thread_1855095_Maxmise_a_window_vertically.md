---
title: "Maxmise a window vertically"
date: 2011-10-05
forum: Desktop Environments
---

### Post by Paddy Landau on 2011-10-05
I have started to use Natty. My screen is short but wide, so I often want windows to open vertically maximised, but not horizontally maximised.

If I run Window Preferences ("Windows" in the menu system), there is an option, "Titlebar Action: Double-click titlebar to perform this action". I have set it to Maximise Vertically (see screenshot).

However, when I double-click the titlebar, it maximises the entire window.

Do you know how I can maximise a window vertically without dragging its top and bottom?

Even better, is there a setting in Compiz where I can say (for example), "Always open Terminal & Nautilus vertically maximised"?

---

### Post by Copper Bezel on 2011-10-05
Yes, I just checked, and I get the same behavior under Natty as well.

One behavior I've used in the past might serve as a workaround - if you set an edge click (such as the top edge) or a keystroke in commands to run this,

```
wmctrl -r :ACTIVE: -b add,maximized_vert
```
the property still works as expected. 

This seems to be another one of those odd little tweaky features that no one seems to use and doesn't get maintained. I don't know, for instance, why windows snapped to half-screen with the Grid don't have this property set, as it would make moving them between workspaces from the Expo view much cleaner and less fidgety.

---

### Post by stinkeye on 2011-10-05
You can maximize vertically by middle clicking on the maximize button.
Right clicking will maximize horizontally.

---

### Post by Krytarik on 2011-10-05
> **Paddy Landau said:**
> Even better, is there a setting in Compiz where I can say (for example), "Always open Terminal & Nautilus vertically maximised"?
You can use Compiz' "Window Rules" plugin for that, "Size Rules". Rules set up there only take effect upon opening the respective windows, so you can still resize them if you like so.

Greetings.

---

### Post by Copper Bezel on 2011-10-05
That sets the size, though, not the property, doesn't it?

Also, with the terminal, you'd need to go into Edit > Profile Preferences and make certain that the "Custom size" option is unticked, as I think it's set by default.

---

### Post by Krytarik on 2011-10-05
> **Copper Bezel said:**
> That sets the size, though, not the property, doesn't it?
Yeah, but you can obviously set the sizes accordingly, and if you set a value higher than the available space (meaning screen size minus panels, docks, or whatsoever), the size is limited to that, so the effect is exactly like maximizing.

However, upon testing that now, I noticed that any new rules just don't take effect at my system, even not after restarting Compiz, while the existing ones still work. Damn, I love when things like that happen! #-o :D

---

### Post by Copper Bezel on 2011-10-05
Yeah, no kidding, although I've just come to expect that sort of thing in 11.04.

I do wish Compiz had a feature like Metacity's automatic mazimize, so that a window that is the size of the workspace would be treated as a maximized one (and likewise for only-vertical maximization, too.) There aren't a lot of disadvantages to windows not really being maximized, but there's the decorator clipping and the need to resize the window down manually instead of "restoring," as well as snapping when moving windows between workspaces (the latter of which applies to windows maximized only vertically as well.)

---

### Post by Paddy Landau on 2011-10-06
Wow, thanks for all the responses!

> **stinkeye said:**
> You can maximize vertically by middle clicking on the maximize button.
Right clicking will maximize horizontally.
This is next-to-perfect! I shall remember it. (Where is it documented?)

> **Krytarik said:**
> You can use Compiz' "Window Rules" plugin for  that, "Size Rules". Rules set up there only take effect upon opening the  respective windows, so you can still resize them if you like so.
This is perfect.

> **Copper Bezel said:**
> with the terminal, you'd need to go into  Edit > Profile Preferences and make certain that the "Custom size"  option is unticked
Ah. I missed that. I have ticked it and set it the right number of lines  to exactly maximise vertically. If only all applications had this  feature!

> **Krytarik said:**
> you can obviously set the sizes accordingly,  and if you set a value higher than the available space (meaning screen  size minus panels, docks, or whatsoever), the size is limited to that,  so the effect is exactly like maximizing.
Not for me! If I set a size larger than the maximum, it sets that size, so part of the window goes off the screen.

> **Krytarik said:**
> upon testing that now, I noticed that any new  rules just don't take effect at my system, even not after restarting  Compiz
Funny; on mine it works immediately, though I have to close and reopen the affected window (not Compiz itself). Are you sure that Compiz is actually enabled on your system? Did you remember to tick the "Enable Windows Rules" box?

In summary:

[LIST]
[*]Some applications (such as Firefox and Gedit) remember  their last setting.
[*]Very few (such as gnome-terminal) have specific  settings.
[*]For the remainder (such as Nautilus), I shall use the Windows  Rules in Compiz.
[/LIST]
 
Thank you again; I shall mark this as solved.

Speaking of which, perhaps you know off-hand how to disable the feature whereby a window automatically maximises when moving it to the top of the screen? I often move a window there but don't want it maximised.

---

### Post by stinkeye on 2011-10-06
> **Paddy Landau said:**
> Wow, thanks for all the responses!


This is next-to-perfect! I shall remember it. (Where is it documented?)



I only found out about this when I downloaded a unity wallpaper with
all the unity shotcut keys and mouse tips on it.
I think it was there even before unity.

> **Paddy Landau said:**
> 


Speaking of which, perhaps you know off-hand how to disable the feature whereby a window automatically maximises when moving it to the top of the screen? I often move a window there but don't want it maximised.


ccsm > window management > grid

---

### Post by Paddy Landau on 2011-10-06
> **stinkeye said:**
> ccsm > window management > grid
Ah (sighs with relief). Thank you.

---

### Post by Paddy Landau on 2011-10-06
Oh boy, more Compiz problems.

I used to be able to drag windows and objects from one workspace (desktop) to another. For example, drag a file from Nautilus one one desktop to FileZilla on another.

I have gone to ccsm > Desktop > Desktop Wall > Edge Flipping and turned on Edge Flip Move and Edge Flip DnD.

Moving windows from one workspace to another works.

But dragging an object from one workspace to another gives erratic results. Usually, it does nothing. Sometimes, it repeatedly flashes the mini-expo screen. And very occasionally, it moves the object.

Any idea what I can do to get the drag-and-drop working reliably? Perhaps two different plug-ins are conflicting?

---

### Post by Krytarik on 2011-10-06
> **Paddy Landau said:**
> Not for me! If I set a size larger than the maximum, it sets that size, so part of the window goes off the screen.
Yeah, as my new rules - apparently - didn't take effect at all, I couldn't really test that, so I wasn't too sure that it's really true. But I *was* sure about a similar thing of the "Place Windows" plugin. However, I can confirm now that the behaviour as you experience it is the same for me, too.

And now I also figured why the rules - apparently - didn't take effect at first; if a window was maximized before closing it the last time, and it remembers its state, it's opened maximized the next time, regardless of matching size rules. But it works in unmaximized state.

As for your new issue reg. the moving of objects to different workspaces; sorry, I've no idea, this is working here. I think that's yet another bug of Compiz in Natty.

---

