---
title: "title bar went away on gnome - intrepid - please help"
date: 2009-03-12
forum: Desktop Environments
---

### Post by green69 on 2009-03-12
Hi everybody!

I'm running on ubuntu 8.1 (with gnome environment). Some days ago I believe after a screen resolution change or after an actualization, title bar (including minimizing, maximizing and closing buttons) disappear in all kind of windows when these are maximized. This is very unpleasen as everytime you have to minimize a windows you have to alt-click-and-drag... so' unconfortable.
In CompicConfigSettingManager the windows decoration is already checked. I even try reinstalling compiz but doesn't work.

I notice there are several people in the forum with exactly the same problem, but nobody found a general solution (without re-installing).

PLEASE can anybody help us?

---

### Post by green69 on 2009-03-27
> **green69 said:**
> Hi everybody!

I'm running on ubuntu 8.1 (with gnome environment). Some days ago I believe after a screen resolution change or after an actualization, title bar (including minimizing, maximizing and closing buttons) disappear in all kind of windows when these are maximized. This is very unpleasen as everytime you have to minimize a windows you have to alt-click-and-drag... so' unconfortable.
In CompicConfigSettingManager the windows decoration is already checked. I even try reinstalling compiz but doesn't work.

I notice there are several people in the forum with exactly the same problem, but nobody found a general solution (without re-installing).

PLEASE can anybody help us?

Please?

---

### Post by patchoro on 2009-03-27
A little more info would be helpfull.
What is your videocard?
What error do you get when you start compiz from the terminal?
try:
compiz --replace && gtk-window-decorator --replace

What error do you get? If you get a message concerning a missing XGL you'll just need to reinstall your video drivers.

---

### Post by gsp8181 on 2009-03-27
I'd say this was a compiz problem, Try typing 'sudo compiz' into a terminal

---

### Post by casaredondo on 2009-03-27
I created this problem for myself by playing around in System, Preferences, Appearance. When I selected the Extra option under Visual Effects, my title bars got all messed up. Selected 'None' and the title bars are fine.

I have Nvida video, and the recommended Nvida driver for 8.10.

If you upgraded from a previous version of Ubuntu, maybe you had a higher setting of visual effects and they don't work so well under 8.10? Go to System, Preferences, Appearance, select the Visual Effects tab and pick "None".

---

### Post by green69 on 2009-03-27
> **patchoro said:**
> A little more info would be helpfull.
What is your videocard?
What error do you get when you start compiz from the terminal?
try:
compiz --replace && gtk-window-decorator --replace

What error do you get? If you get a message concerning a missing XGL you'll just need to reinstall your video drivers.

If I type "compiz --replace && gtk-window-decorator --replace"
It doesn't terminate the task and I get:
# 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
#



If reinstalling video drive would solve the problem I'll do it. Please can you explane me a bit how to do it? (I'm sorry but I'm relatively new ubuntu user).

Thank you very much!

---

### Post by green69 on 2009-03-27
> **casaredondo said:**
> I created this problem for myself by playing around in System, Preferences, Appearance. When I selected the Extra option under Visual Effects, my title bars got all messed up. Selected 'None' and the title bars are fine.

I have Nvida video, and the recommended Nvida driver for 8.10.

If you upgraded from a previous version of Ubuntu, maybe you had a higher setting of visual effects and they don't work so well under 8.10? Go to System, Preferences, Appearance, select the Visual Effects tab and pick "None".

I've already tried to disable the effects but this doesn't sovle the problem!

Any other suggestions?

---

### Post by Nero147 on 2009-03-27
I would say that one easy way of checking would be to create a new user and see if it has the problem. If it doesn't you can just copy over your files.

---

### Post by heffo_j on 2009-03-30
I've had this problem before and I found a solution on this forum somewhere. It has just today (months later) started again. I did an upgrade to FF3.0.8.

A simple and annoying solution is to press F11 which restores the top window menu bar.

Its seems to be a regression to me.....

Regards
John

---

### Post by green69 on 2009-03-31
> **Nero147 said:**
> I would say that one easy way of checking would be to create a new user and see if it has the problem. If it doesn't you can just copy over your files.

Unfortunaly if I create a new user the problem follows there.
Anybody can explane me how can I re-installing video drive?

---

