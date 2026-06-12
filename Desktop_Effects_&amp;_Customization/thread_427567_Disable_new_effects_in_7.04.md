---
title: "Disable new effects in 7.04?"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by zirconx on 2007-04-29
My wife just upgraded to 7.04, and her system is now so slow its pretty hard to use.  It looks like this new version is doing some fancy effects like fading the windows in and out.   How do we turn this stuff off?  I looked in sereral items in prefences (thought I would have found it in 'Desktop Effects' or 'Windows') but couldn't find anything.

Thanks for any help.

---

### Post by Kobalt on 2007-04-29
The desktop effects are not enabled by default when you install Ubuntu (for that matters because you need to install your graphic card drivers first). If it's enabled, you can access and disable it from System > Pref. > Desktop Effects.

---

### Post by zirconx on 2007-04-29
I don't think our problem is with the effects listed under Desktop Effects.

The problem is every window that is opened or closed 'fades' in or out of appearance. I don't see a setting for this under Desktop Effects.

The old version (6.something) did not do this, it appears to be new in 7.04.  Every time she double clicks a mail message or does anything that causes a new window to open, there is a delay of almost a second before the window appears.  I can see it fading in or out, I think this is whats causing the slow down, but I'm not positive.

We would have just stayed on 6.x but her computer would lock up randomly, I was hoping the new version would fix that.

---

### Post by Kobalt on 2007-04-30
> **zirconx said:**
> I don't think our problem is with the effects listed under Desktop Effects.

The problem is every window that is opened or closed 'fades' in or out of appearance. I don't see a setting for this under Desktop Effects.

The old version (6.something) did not do this, it appears to be new in 7.04.  Every time she double clicks a mail message or does anything that causes a new window to open, there is a delay of almost a second before the window appears.  I can see it fading in or out, I think this is whats causing the slow down, but I'm not positive.

The settings can be made through gconf-editor or gnome-compiz-manager (to be installed, not installed by delfault).
It's definetly the Desktop-Effects doing this, not the default settings in 7.04. Windows open and close, minimize and maximize just the same way they did in 6.10 if you don't enable Desktop-Effects.
Also : did you install the drivers for your graphic card ? which one ? how ?

---

### Post by zirconx on 2007-05-01
Thank you, I will look at gconf-editor or gnome-compiz-manager.

I don't think we did anything special with the video card drivers, just put in the 7.04 CD and followed the prompts.  My wife did it herself so I'm not sure.

> It's definetly the Desktop-Effects doing this, not the default settings in 7.04. Windows open and close, minimize and maximize just the same way they did in 6.10 if you don't enable Desktop-Effects.

I made sure both checkboxes in the Desktop Effects panel were both unchecked, but that did not help. The windows still fade in and out.  Also the button in this panel says "Enable Desktop Effects", leaving me to believe they are off.  Wouldn't it say Disable Desktop Effects if they were on?  You'd think so, but I pressed this button many times just to see, and it never said anything other than Enable Desktop Effects.

But we've had this problem since we installed 7.04, before we even knew there was such a think as a Desktop Effects control panel.

---

### Post by scanez on 2007-05-01
If desktop effects is enabled, the button will still read "Enable Desktop Effects" but it will be pushed in. Click it to disable desktop effects. Or, if you want to use desktop effects but just not have windows fade in/out, disable the fade plugin under compiz in gconf-editor. Let us know if you need help with this if this is indeed what you want to do.

---

### Post by zirconx on 2007-05-22
Thanks for posting the note about the button being pushed in, that was it.

Why does X windows/Gnome/whatever insist on creating new, awkward user interfaces?  Why not a checkbox, or an on/off radio set?  A 'pushed down' big button?  It just looked like the button was a different color to me.  Its not like you can click it on and off and watch it change.  One click and the system locks up for a few seconds, then the screen blinks - I never noticed the shading had changed slightly.

I've tried switching from Windows to Linux 2 or 3 times, and each time I end up going back to windows, frustrated with the linux gui experience.  There are lots of little things that are just annoying.  Its extreemely hard to resize a window.  I don't know why - I put my cursor on the corner, click the mouse button, and drag.  But it always ends up switching focus to the window behind it.  Like it takes a few milliseconds to recognize I've pressed the mouse button, and by the time it recognizes it, the cursor is already over the other window.   This is a 1.8GHz machine that always ran XP just fine, but its not enough horsepower for Linux to pick up a click event in real time?  If I do this over again slowly, it always works.

Looking forward to getting a mac....

---

