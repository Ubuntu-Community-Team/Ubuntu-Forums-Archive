---
title: "How to have 3d desktop displayed"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by s.jesudasan on 2008-01-19
Hi i installed gutsy in my aspire 4520
and then i installed compiz 
now im able to turn on all the effects but not the 
3d desktop in which we can see all the desktops at a time
how to do that.I tried ctrl+alt + left click
but nothing happened

---

### Post by FuturePilot on 2008-01-19
> **s.jesudasan said:**
> Hi i installed gutsy in my aspire 4520
and then i installed compiz 
now im able to turn on all the effects but not the 
3d desktop in which we can see all the desktops at a time
how to do that.I tried ctrl+alt + left click
but nothing happened

```
sudo apt-get install compizconfig-settings-manager
```
Then you can configure all the plugins including the cube.
System>Preferences>Advanced Desktop Effects Settings

---

### Post by gspat on 2008-01-19
try F10... although I may have changed the default...

look in the ccsm and see what you have as default for "Window Picker" in the scale plugin

---

### Post by s.jesudasan on 2008-01-19
> **FuturePilot said:**
> ```
sudo apt-get install compizconfig-settings-manager
```
Then you can configure all the plugins including the cube.
System>Preferences>Advanced Desktop Effects Settings

ive installed compiz and ive the advanced settings tab
ive turned on everything that says 3d cube 
still im not able to get that 3d desktop
is there any key that i should press

---

### Post by Ub1476 on 2008-01-19
Have you enabled Compiz in System>Preferences>Visual Effects?

Make sure that 4 desktops are enabled in General Settings>Desktop Size.

---

### Post by s.jesudasan on 2008-01-19
> **gspat said:**
> try F10... although I may have changed the default...

look in the ccsm and see what you have as default for "Window Picker" in the scale plugin

in rotate cube i have ctrl+alt+button1 disabled
how to turn on that

---

### Post by Ub1476 on 2008-01-19
> **s.jesudasan said:**
> in rotate cube i have ctrl+alt+button1 disabled
how to turn on that

It's they **Key** combination which is disabled, however the **Button** combination is (by default) enabled

---

### Post by s.jesudasan on 2008-01-19
> **Ub1476 said:**
> Have you enabled Compiz in System>Preferences>Visual Effects?

Make sure that 4 desktops are enabled in General Settings>Desktop Size.

i dont have visual effects in preference
i have enabled 4 desktops in advanced settings

---

### Post by Ub1476 on 2008-01-19
> **s.jesudasan said:**
> i dont have visual effects in preference
i have enabled 4 desktops in advanced settings

Sorry it was **System>Preferences>Appearance>Visual Effects**.

---

### Post by s.jesudasan on 2008-01-19
> **Ub1476 said:**
> Sorry it was **System>Preferences>Appearance>Visual Effects**.

i have enabled custom visual effects
everything like windows preview is working but 3d desktop

---

### Post by s.jesudasan on 2008-01-19
> **Ub1476 said:**
> Sorry it was **System>Preferences>Appearance>Visual Effects**.

even when i click on a window and drag it to the next desktop it shows as if im 
inside a cube but im unable to view the cube from outside the cube

---

### Post by Ub1476 on 2008-01-19
Alright, make sure that:

Desktop cube is enabled
Rotate cube is enabled
See if ctrl+alt+left (or right), will rotate the cube.
You might as well try ctrl+alt+down to unfold it.
Remember you have to hold down all the keys.
If nothing there works, revert all settings in these two plugins.

EDIT:
> even when i click on a window and drag it to the next desktop it shows as if im
inside a cube but im unable to view the cube from outside the cube

You have been messing with the cube settings (nothing wrong with that). To get the default just revert the settings.

---

### Post by gspat on 2008-01-19
find an open spot on your desktop and click your middle mouse button... if all is setup, that should lift the cube... if you have a scroll wheel, you can flip from face to face by scrolling on an empty spot on the dektop.

ok, just read your last post... there is a checkmark for "inside cube", make sure there is no checkmark in it!


that would be desktop cube plugin > behavior > first item... "inside cube"

---

### Post by s.jesudasan on 2008-01-19
> **s.jesudasan said:**
> even when i click on a window and drag it to the next desktop it shows as if im 
inside a cube but im unable to view the cube from outside the cube

Now im able to view the cube desktop from inside by usin ctrl+alt+button1

but how to view it from outside the cube

---

### Post by gspat on 2008-01-19
that would be desktop cube plugin > behavior > first item... "inside cube" 

make sure there is no checkmark there!!!!

---

### Post by s.jesudasan on 2008-01-19
> **gspat said:**
> that would be desktop cube plugin > behavior > first item... "inside cube" 

make sure there is no checkmark there!!!!

thats working great 
thank u so much gspat

---

### Post by biyouboogie on 2008-01-21
I am having the same problem. None of my effects are working and neither is the cube. When i try to click custom for the visual effects, it gives me an error saying the composite extension is not available. I have tried loading my ATI drivers using envy, and i get an error when doing that also.

---

### Post by s.jesudasan on 2008-01-21
> **biyouboogie said:**
> I am having the same problem. None of my effects are working and neither is the cube. When i try to click custom for the visual effects, it gives me an error saying the composite extension is not available. I have tried loading my ATI drivers using envy, and i get an error when doing that also.

Check out ur /etc/X11/xorg.conf file
to see whether drivers for ur ATI card 
is installed and which ubuntu r u 
using gutsy or fiesty or dapper

---

