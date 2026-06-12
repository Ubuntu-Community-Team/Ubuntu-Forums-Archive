---
title: "I think I deleted the stuff I need for compiz"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by spetsacdc on 2008-01-19
Hello, I am trying to get compiz fusion on my machine (gutsy). But, I think I delete some of the files I need to get it to work. I ran a lot of commands I found online and screwed something up. Right now I think I got all the compiz files off my computer, and I am trying to reinstall.

When I put this in terminal 

sudo apt-get install compiz compizconfig-settings-manager 

I get the error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz has no installation candidate


Any advice?

Thanks

---

### Post by Ub1476 on 2008-01-19
Are sources enabled in System>Administration>Software Sources?

---

### Post by spetsacdc on 2008-01-19
Thanks! That worked, but now when I put effects at anything but none (via the change desktop screen thing) all my windows don't have the minimize, small window and close bar. Plus, I can't drag windows around.

Any ideas?

Thanks again!

---

### Post by Ub1476 on 2008-01-19
Open CCSM and make sure Window Decorations and Move Windows is enabled.

---

### Post by spetsacdc on 2008-01-19
I turned them on, but that still didn't fix it.

---

### Post by alamarco on 2008-01-19
> **spetsacdc said:**
> Thanks! That worked, but now when I put effects at anything but none (via the change desktop screen thing) all my windows don't have the minimize, small window and close bar. Plus, I can't drag windows around.

Any ideas?

Thanks again!

Tip: You can drag windows around by holding down the 'ALT' key and clicking and dragging anywhere in the window.

As per no window decorations (minimize, maximize, close) it's probably because emerald didn't load properly. If you can get the run dialog to pop up (I couldn't) by pressing the alt+f2 shortcut type in the following command: 'emerald --replace'. That should reload emerald with window decorations present.

If you can't, open a terminal window (I have one as a quick launch icon for convenience and times like this) and type 'emerald --replace&'. If you close the terminal you'll lose the window decorations so now get the run dialog open again (alt+f2) and type 'emerald --replace'. This will again replace emerald so you can close the terminal window without losing your window decorations.

I hope this helps.

---

### Post by spetsacdc on 2008-01-19
Hmm. I used alt to drag stuff. It turns out all the windows have the title bar (they were just hidden perfectly under the system tool bar at the top of my screen. When I use alt f2 to say emerald --replace it can't find the file. Also, it just closed the terminal when I put it in there. something is still messed up though b/c all windows open with the title bar in the upper left (hiding their title bar) and I cannot resize any windows by draggin the corners.

Thanks

---

### Post by Ub1476 on 2008-01-19
Emerald is not necessary. You just need to edit the plugin, "Place Window", for it to work.

---

