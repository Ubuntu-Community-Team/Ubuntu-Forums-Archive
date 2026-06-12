---
title: "Crazy gnome panel"
date: 2005-04-28
forum: Desktop Environments
---

### Post by mdbarton on 2005-04-28
I was busy configuring the gnome panels (adding a few launches) and now it's gone crazy!  THe panels disappear then re-appear, then disappear again (flick on and off) - about 5 times, then stops - no panel.  I open a terminal and type 'gnome-panel &' and the panel re-appaers and starts flickering again, then stops with no panel and the message 'Segmentation Fault' in the terminal.

Any ideas?

---

### Post by XDevHald on 2005-04-28
Hmm, try re-installing the gnome-panel, then logout, and log back in, this will see if it rehashes it :)

---

### Post by mdbarton on 2005-04-28
thanks for the suggestion - I tried that but it's still the same.  I think that I must have corrupted some of the panel config files in the chnages I was making - do you know where I find these?

---

### Post by tread on 2005-04-28
Either .gnome2 or .gnome in your home directory .. there should be a folder called panel_something there.

---

### Post by eric71 on 2005-04-29
This happened to me too.  The only way I found to fix it was to go into the .gnome2 folder in your home directory (I did this in xfce, which i also had installed, you might have to start a terminal with GDM if you cand use gnome at all because of this problem), go into panel2.d and delete the "default folder".  Then when you start gnome it will start with a fresh panel configuration.

---

### Post by mdbarton on 2005-04-29
Thanks!  Will try tonight (at work at the mo).

---

### Post by mdbarton on 2005-04-29
yep - that fixed it - thanks!

---

### Post by mdbarton on 2005-04-30
I have found how I can re-create this - it happens whenever I add a launcher for tuxpaint to the panel.  Very bizarre!  I can add launchers for other apps without having this problem.

---

### Post by luvdemheels on 2005-04-30
Do you use a gui to edit your menus?? If so where did you get the gui and what is it??

Thanks.

---

### Post by TravisNewman on 2005-04-30
This is specifically about panel icons, not menu entries, but you can find a menu editor in the 3rd party projects section on the forums

---

### Post by eric71 on 2005-04-30
I had just installed Tuxpaint and was adding it to the panel so my daughter could find it.  I didn't make the connection that it was specifically that program that caused it.  I thought it was just some fluke.

---

### Post by neighborlee on 2005-04-30
[QUOTE=panickedthumb]This is specifically about panel icons, not menu entries, but you can find a menu editor in the 3rd party projects section on the forums[/QUOTE]
------------------
I dont recall having that problem but I wonder if what I had was related...I dont recall what I was doing unfortunately , but    whatever it was caused gnome-panel to crash as in it would not redraw right ..if I tried to access menu it would not work yet it would draw parts of a menu on top of it ..its hard to explain.

The panel of course was useless then as was the desktop....

Is gnome-panel for some reason ( seeing several other people with various panel issues) flakey , or have the gnome developers just had a hard time lately with QA ? ( jk but hey one does wonder between that, the user/dev debate and them seeming not to care ? about menu editing and silly nautilus design decisions that not even windows adheres to  )

It is not my system because I rarely have crashes in windows XP ( dont flame) meaning its not my setup nor anything I'im doing necesssarily to cause this behavior.

cheers
neighborlee

---

### Post by antwerx on 2005-06-25
Hello all -  I wanted to report the same issue of segmentation fault and corrupt gnome-panel when making a launcher on the panel for TuxPaint.

---

### Post by KenLin on 2005-06-25
I also had this problem when creating a launcher for tuxpaint. weird. I could create a drawer and add tuxpaint to it without problem.

---

### Post by xbaez on 2005-06-27
[QUOTE=KenLin]I also had this problem when creating a launcher for tuxpaint. weird. I could create a drawer and add tuxpaint to it without problem.[/QUOTE]
 I am also having that problem, I installed the ubuntu-desktop from my Kubuntu installation.

KDE works amazing, the most stable, amazing, KDE I've ever seen so far

---

