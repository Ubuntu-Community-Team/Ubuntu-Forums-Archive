---
title: "Problems with Compiz Fusion"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by jf1991999 on 2007-10-23
I have a new installation of Gutsy and installed the Compiz-Fusion files as described in the forums.  Most of the effects appear to be working correctly however I can't get the cube to display.  I have seen that others have had this issue.  My 'Cube' appears to have sides that are the full height of the screen.  I can rotate this using ctr+alt+right arrow but I would really like to see a cube come up when I push the ctr+alt keys.

I tried to increase the default number of desktops to 4 in the general settings, but found that if I set the number to 4 it showed 3 desktops in the bottom right panel of the screen.  Tapping any of these other desktops gave me a blank white screen which persisted across all desktops when I tried to rotate the cube.  If I log out with ctr+alt+backspace and log back in I can again see my desktops.  This appears to be a bug.  When I reduce the number of desktops back to 2 in the general settings this issue goes away.

I would really like to be able to see my cube if anyone can help.

---

### Post by ThrobbingBrain66 on 2007-10-23
I know it seems backwards, but number of desktops should stay at 1.  The value you want to change is the horizontal virtual size (found in the same section of advanced desktop effects settings).

---

### Post by jf1991999 on 2007-10-23
I tried adjusting the horizontal virtual size to 2 with the number of desktops set to 1 but still no cube :( What settings should I have in the workspace panel preferences in the bottom right of the screen, Could this be causing problems?

I seem to be seeing some weird behavior, sometimes rotating the panels keeps bringing the same one to the front even though I have multiple panels.

---

### Post by HMartinho on 2007-10-23
I think you should set it to 4 in order to get a cube, 2 windows will give you the two side of a piece of paper.

Cheers.

---

### Post by xluryan on 2007-10-23
I *had* the same problem. Here's how I fixed it:

1. Go into Compiz Settings > General Options > Desktop Size.
2. Click the default values buttons for all 3 options. This should set everything (from the top down) to 2, 1, and 1.
3. Right click on the virtual desktops in the bottom right (there should be 2 now) and choose Preferences. Change columns to 4 and hit Close.

Let us know if that works!

---

### Post by asgard_command on 2007-10-23
> **xluryan said:**
> I *had* the same problem. Here's how I fixed it:

1. Go into Compiz Settings > General Options > Desktop Size.
2. Click the default values buttons for all 3 options. This should set everything (from the top down) to 2, 1, and 1.
3. Right click on the virtual desktops in the bottom right (there should be 2 now) and choose Preferences. Change columns to 4 and hit Close.

Let us know if that works!

I have exactly the same problem and tried this but no change.

---

### Post by jf1991999 on 2007-10-24
> **xluryan said:**
> I *had* the same problem. Here's how I fixed it:

1. Go into Compiz Settings > General Options > Desktop Size.
2. Click the default values buttons for all 3 options. This should set everything (from the top down) to 2, 1, and 1.
3. Right click on the virtual desktops in the bottom right (there should be 2 now) and choose Preferences. Change columns to 4 and hit Close.

Let us know if that works!

I tried this and still no cube.  I can flip between the 4 virtual desktops and the effect is quite nice, However each desktop takes up the full screen when flipping.  When I hit the windows+E key I see all four panels in about a quarter the height of the screen with a nice reflection under them.  so some things are definitely working.

---

### Post by ThrobbingBrain66 on 2007-10-24
I think we misunderstood your original query.  It sounds like you have the cube now.  Am I right in assuming that you want to be able to zoom out on your desktop to see the entire cube at one time?

I have the Viewport Switcher plugin enabled and am able to use my middle mouse button to rotate the cube.  The mouse pointer must be positioned on the desktop to do this though (as opposed to being positioned over an open window).

---

### Post by CureDimz21 on 2007-10-24
As for seeing the cube from further away, isn't there a zoom-out feature or something?  Just go to "Rotate Cube" and click on it bringing up the settings options for that particular feature.  Scroll down to "Zoom".  Raising the zoom allows you to see a cube rotating where the cube is smaller than the screen (you're zooming out).

Yeah.  I'm not really sure if you have the cube at all or if you're just switching between two sides like a page (like HMartinho said).  If you can't get the cube with four sides (where, even if it's the full screen, you CAN see it as a cube), simply do the following:

1) Disable Cube, Rotate Cube, and Cube Gears (not sure but just disable this one, too)
2) Close appearance manager (CCSM)
3) Right click on the small workspaces are in the tray and select "Preferences..."
4) Change workspaces to 4 (I have all 4 horizontal)
5) Close
6) Open appearance manager again, and re-enable Cube, Rotate Cube, and whatever else you wanted dealing with the cube.  It should now at least be a cube with 4 sides.
If it works (and it did for me when I had trouble), don't thank me!  haha, someone else on these forums posted these instructions and so I'm only passing their wisdom on.

Hope this helps.

-PEACE

---

### Post by jf1991999 on 2007-10-25
I followed your instructions and still don't have the cube although let me explain what I have.  When I enable the cube functionality, I can switch between desktops using the ctr+alt+left arrow.  What I see is spinning full screen desktops.  I never see a cube shape.  I used the zoom function which helps a little.  When the panels are spinning the size reduces, however still no cube.  When I disable the cube these effects stop, so clearly I have some of the functionality.

There are a lot of different options with very little explanation.  I haven't really played with many of them so I am sure I have the default settings.

---

### Post by arunta on 2007-10-25
Just press ctrl+alt. While perssing these keys, left-click your mouse pointer on lower parts of the screen and all the while pressing the left mouse button, drag the mouse pointer slowly towards upper corner of the screen... You will see the cube :)

---

### Post by asgard_command on 2007-10-25
> **arunta said:**
> Just press ctrl+alt. While perssing these keys, left-click your mouse pointer on lower parts of the screen and all the while pressing the left mouse button, drag the mouse pointer slowly towards upper corner of the screen... You will see the cube :)

Wow I actually found my cube. Such a simple answer after I've spent so long trying to change different settings.
Is this the only way to switch desktops with the cube effect though. Not sure I have enough fingers 
ctr + alt + left click button, then trying to drag over the touchpad. Is there no simpler way.

---

### Post by jf1991999 on 2007-10-25
> **arunta said:**
> Just press ctrl+alt. While perssing these keys, left-click your mouse pointer on lower parts of the screen and all the while pressing the left mouse button, drag the mouse pointer slowly towards upper corner of the screen... You will see the cube :)

Fantastic!  Finally I see the cube.  Thanks for your help.  However is there a way to get the cube to show while it flips?  It seems like a lot of work.  I would like to see the cube when I hold ctr+altand continue to see it until I release these keys.  Left arrow would rotate the cube.

---

### Post by izak on 2007-10-26
Yes, I played around with the compiz settings last night. Must first say that it was my first time with desktop effects and its excellent everything just works!

But I agree there is too little explanation about how to see the settings once you have them enabled. For example, I could not see any water effects or motion blur - when and how are these supposed to appear?

Also I couldn't change the key bindings. For example I'd like to have Alt+Tab call shape (I mean the thing where all the windows fit onto one desktop) instead of task switcher. I've tried to disbable the task switcher and then change the bindings from the default Shift+Alt+Up, but I get a PC beep error. Any Ideas? You have to be really dexterous for some of these key combinations :)

---

