---
title: "The 3D Cube Desktop Effect doesnt work"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by OscarWabbit on 2007-09-28
hi

i cant get the feisty 3d desktop cube to work.

when i activate Desktop features, the windows will wobble, but i cant get any 3d cube.

ive installed beryl from synaptic and still cant get the cube to work.

ive tried pressing ALT CTRL + direction keys, but nothing happens.

please help.

thanks

---

### Post by SendDerek on 2007-09-29
Your settings probably just got a little messed up.  It happened to me (and others) all the time.  Basically, it set itself to have "1" workspace.  So, it's working, but it doesn't have any other workspaces to switch to.

I recommend an installation of gnome-compiz-manager.  Type this into the terminal:
sudo apt-get install gnome-compiz-manager

Then, go into System -> Preferences -> GL Desktop and click on the "Workspaces" tab and set the number of workspaces to 4.

This is the best utility to get the most out of compiz for now.  Just wait until compiz-fusion on Gutsy!  That'll be cool!

---

### Post by OscarWabbit on 2007-09-29
hi

thanks for the advice, i'll take it on board.

i just did a re-install of ubuntu from CD and the cube works again... im still very new to linux, so im expecting to have to do a few re-installs when i break things.

but its working now, cheers

---

### Post by jean noel on 2007-09-29
That's what is great about ubuntu.Had it been windows, you would have had to buy another activation code :-)

---

### Post by OscarWabbit on 2007-09-29
> **SendDerek said:**
> Your settings probably just got a little messed up.  It happened to me (and others) all the time.  Basically, it set itself to have "1" workspace.  So, it's working, but it doesn't have any other workspaces to switch to.

I recommend an installation of gnome-compiz-manager.  Type this into the terminal:
sudo apt-get install gnome-compiz-manager

Then, go into System -> Preferences -> GL Desktop and click on the "Workspaces" tab and set the number of workspaces to 4.

This is the best utility to get the most out of compiz for now.  Just wait until compiz-fusion on Gutsy!  That'll be cool!


hi

i would just like to give an extra thanks for this post.

i was using VLC player which wasnt working properly, and i read somewhere that you should disable Desktop Features to get VLC to work, which did the trick.  however, when i tried to re-enable desktop features, the cube no longer worked, no matter what i tried.

so i did as you instructed and installed compiz-manager and using this program got the cube working again.

much obliged, very grateful for your help.

thanks

---

### Post by Linicks on 2007-09-29
OK, here's how to fix the desktop issue.

Turn on desktop effects (wobble and cube).

Turn off cube.

Now go to the panel->prefences and increase workspaces to four

Now go back to desktop effects, and select the cube option again.

It will now work.

Nick

---

