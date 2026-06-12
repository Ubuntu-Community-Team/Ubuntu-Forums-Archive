---
title: "Beryl: only one face of the cube works properly"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by felipe82 on 2007-06-25
Hi, I just installed Beryl. It worked fine but then I installed "Automatix read/write NTFS and FAT32 Mounter" with automatix (duh) and then I restarted my PC. After that, only the main face of the cube works under Beryl, the other 3 look black and when you drag a window there, it leaves a "trace" all over (see pics). Basically, the 3 other worspaces don't load properly.

Screenshot 1 shows the black workspace (i hadn't setup skydome yet in this pic).
Screenshot 2 shows what happens when you drag a window there.
Screenshot 3 shows the trasnparent cube, looked from the 2nd (bad) workspace, the one on the left is the main one (the only one that works). Skydome is activated now.

Any help would be greatly appreciated.

---

### Post by Milky The Brown Cow on 2007-06-25
im not sure how to fix it, but there is a huge thread on Beryl here: [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)  hopefully you can find your answer in there.

---

### Post by felipe82 on 2007-06-25
Fixed it.

Just uncheck:

Beryl Manager->General Options->Desktop Background->Desktop Manager Supports Viewports

thx a lot

---

### Post by ammark on 2007-08-04
> **felipe82 said:**
> Fixed it.

Just uncheck:

Beryl Manager->General Options->Desktop Background->Desktop Manager Supports Viewports

thx a lot


I have been fiddling around with Beryl after installing it yesterday as well. I have the same problem in that Workspace 1 is the only one working normally... the other workspaces show a black desktop background and thus a window trail gets imprinted if I move any windows there.

When I checked "Desktop Manager Supports Viewports", Workspace 3 also worked normally along with Workspace 1.

However now that I unchecked it... Only Workspace 1 works normally.

Secondly, I tried Keyboard shortcut Ctrl+Shift+Up, however nothing happened, I couldnt see the top of the cube. I would also like to view the cube zoomed out as in Picture 1 and 3.. and am a bit clueless on which setting to fiddle with to get that working. How would I enable ripple as well?

My system:
Toshiba Satellite 2455-S305 laptop; Intel P4 2.4GHz; 512MB DDR; 32 MB Nvidia Geforce Go 420 graphics controller; 60GB Hard Disk (9GB for feisty).

---

### Post by Shaydog on 2007-08-12
Thank you very much!

This helped me to fix the same problem.

---

### Post by felipe82 on 2007-08-12
> **ammark said:**
> 
When I checked "Desktop Manager Supports Viewports", Workspace 3 also worked normally along with Workspace 1.

However now that I unchecked it... Only Workspace 1 works normally.


Why did you unchecked it? As far as I know you don't really need that option. I really don't have a clue what does it do, but I've been working without it so far with no problems.

> **ammark said:**
> 
Secondly, I tried Keyboard shortcut Ctrl+Shift+Up, however nothing happened, I couldnt see the top of the cube. I would also like to view the cube zoomed out as in Picture 1 and 3.. and am a bit clueless on which setting to fiddle with to get that working. How would I enable ripple as well?


The zoom that the cubes takes when you rotate it with the middle mouse button is defined in Beryl Manager -> Desktop -> Rotate Cube -> Behaviour -> Zoom.
In the same section, click on the Shortcuts tab and expand 'bindings'. Maybe there's something misconfigured there, but I really don't know why. Make sure the 'Rotate Cube' option is checked tough.

---

