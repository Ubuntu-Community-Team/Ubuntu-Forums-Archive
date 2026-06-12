---
title: "Drag Window Under Panel"
date: 2009-07-21
forum: Desktop Environments
---

### Post by dmclennan on 2009-07-21
With the standard Ubuntu desktop, there is a top horizontal panel across the screen.  Every once in a while I find a window caption/title/menus placed under the panel.  To move this window, I've had to add the hide/show buttons to the panel and move the offending window from under the panel.  I find this happens about 1-2 times per day.

It is interesting what is happening - if you simply drag a window to the top panel, it will stop when it reaches the panel area.  As such, you can not drag a window under the panel.

However, if you resize the same window, it is possible to resize the top part to under the panel, resulting in the top part of the window from being visable/available.  To see this, simply mouse-click, hold the top edge or corner and drag/resize over the panel. The window is conveniently resized but now under the panel.

Any way to prevent this?  With the fixed top horizontal panel, the drag/move is prevented, but the drag/resize is not.  I don't see any logical reason why we'd want the ability to resize a window under the panel, effectively making it hard to get to/move.

I appreciate any comments or suggestions on how to prevent this. Thank you

---

### Post by SecretCode on 2009-07-22
I see that too. I don't know how to prevent it. It does seem odd.

But you don't have to hide the panel to move the window: if you hold the Alt key you can drag the window by clicking on any part of it. 

(I just checked this with the original metacity window manager, no compiz effects, and it works ... but the resizing by dragging the top edge doesn't go past the panel edge. Do you have compiz enabled? I wonder if this is a bug/feature of the relevant component of compiz.)

---

### Post by dmclennan on 2009-07-22
Hi,
Your suggestion of using the Alt key to move the window works great (didn't know that!).  Yes, I have compiz 1:0.8.2 installed with the "Extra" visual effects.  I disabled the extra visual effects and the window drag DOES NOT move under the panel.  Looks like a strange interaction with the visual effects and panel.  Is this a bug? Thanks for your suggestions.

---

### Post by drs305 on 2009-07-22
> **dmclennan said:**
> Hi,
Your suggestion of using the Alt key to move the window works great (didn't know that!).  Yes, I have compiz 1:0.8.2 installed with the "Extra" visual effects.  I disabled the extra visual effects and the window drag DOES NOT move under the panel.  Looks like a strange interaction with the visual effects and panel.  Is this a bug? Thanks for your suggestions.

I believe that you can prevent windows from initially opening under the menu bar by going into the CompizConfig Settings Manager and selecting Place Windows > Placement Mode > either Smart or Centered. You can still *move* the window under the menu bar but I don't think it will open there.

If you have one particular window that is doing this, try going to the "Fixed Windows Placement" tab of the same section > Windows with Fixed Positions, Grab the window when it is properly placed, set the placement values and then tick the "Keep in Workarea" option.

---

### Post by SecretCode on 2009-07-23
> **dmclennan said:**
> Is this a bug?

It probably is a bug! I'm not sure whether it's a bug in Compiz, or in Ubuntu's package of Compiz, or in something else like X.org ... and I was going to leave it up to you :) to decide where and how to report it ... but lookee here: [Bug #302440 in compiz (Ubuntu): “Compiz allows you to resize windows under gnome-panel”](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/302440). You might want to add to that report!

---

### Post by peterzh on 2009-08-02
> **dmclennan said:**
> Hi,
Your suggestion of using the Alt key to move the window works great (didn't know that!).  Yes, I have compiz 1:0.8.2 installed with the "Extra" visual effects.  I disabled the extra visual effects and the window drag DOES NOT move under the panel.  Looks like a strange interaction with the visual effects and panel.  Is this a bug? Thanks for your suggestions.

By default the alt drag ability is restricted to the upper panel edge. You can remove this constraint by going: **CompizConfig Settings Manager > Window Management > Move Window**, then untick **"Constrain Y"**

---

