---
title: "help with beryl setup"
date: 2006-11-17
forum: Desktop Environments
---

### Post by jornahow on 2006-11-17
I would appreciate some help configuring beryl.  I am using edgy amd64 on an MSI P965 neo, Intel 6400 core 2 duo and Nvidia 7300GS with a Samsung 940BW currently set to 1440 X 900.  My first beryl install with XGL was a fiasco - it took me more than a day to find and figure out conflicting guides and install - it worked for all of 1/2 hour before crashing, necessitating a fresh install of edgy64.  This time I installed Nvidia 9742 Beta drivers (as it turned out hardly a trivial task for a linux newbie).  I installed beryl without XGL or AIGL. It works and seem stable, smooth and speedy but for a brief period when inexplicably, windows borders disappeared and then returned. Fortunately with this install I can revert easily to Metacity.

The beryl effects work; wobbly windows, cube rotation and zoom, but my problem is that I can't figure out how to reduce the size of my desktop and show the 3D cube with top and bottom faces.  My desktop is always full size, except when I rotate the cube.  The desktop shrinks to less than full screen and rotates, using the zoom function, but then returns to full screen. At no time are the top and bottom faces visible.  For the life of me I can't figure out how to set this up further.  I have spent hours searching through the beryl project forums, how to's and FAQ's with no solution.  Someone else must also have grappled with this and any help would be appreciated.  The beryl settings manager menus and help are unhelpful. providing mostly circular definitions.  If you have an answer I look forward to a reply.

Thanks

jornahow

---

### Post by d3v1ant_0n3 on 2006-11-17
I *think* the default keybindings for manually rotating the cube are CTRL +ALT+Mouse1 . I can't confirm this as I've changed mine.

You can check them by opening Beryl Settings Manager (either from System>Preferences> or by right clicking on the Beryl icon in the notification area and selecting Beryl Settings Manager). Go to the 'Rotate Cube' plugin in the left hand pane, and select 'Mouse'. The one you need to check is the top one ('initiate'). Make sure its checked as well.

Have fun with Beryl!

*edit* I have trouble explaining GUI's. I've marked the options in the attatched screenshot.

---

### Post by jornahow on 2006-11-17
Thanks for that suggestion. I found that rotate "up" and "down" are separate entries under rotate cube "screen edges and corners" and they were disabled.  I'll keep fiddling.  

jornahow

---

### Post by d3v1ant_0n3 on 2006-11-17
The best way to get to grips with the somewhat cryptic settings in Beryl is probably to keep the settings manager open, and just play with stuff and see what it actually does.

If you look down in the bottom left corner of the settings window, theres an optin to restore to default settings, or import a saved settings profile, in case you break stuff;)

---

### Post by trogbot on 2006-11-18
I found this on the Beryl Wiki:

Hold down <Cntrl><Alt> + Click Left Mouse Button.

This shrinks the cube down & allows you to rotate/view cube at any angle as long as you keep the mouse button down.  Once you have the 3D Cube you can let the <Cntrl><Alt> keys go & the Cube will stay up viewable as long as you keep mouse button down.  Once you get to a side you want to view, let go of mouse button & it will bring that desktop back to fullscreen.  This is the only way I've found so far.

---

### Post by jornahow on 2006-11-18
Hmm. :-? Ctrl + Alt + left mouse button does nothing on my machine even though beryl setup shows this combo as the setting to initiate cube rotation.  I now rotate with scroll wheel, or by moving mouse pointer to screen edges.

jornahow

---

