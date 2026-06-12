---
title: "Matlab in 12.04"
date: 2012-08-13
forum: Education &amp; Science
---

### Post by Lucretia on 2012-08-13
I have recently upgraded to 12.04. Previously, I was running Matlab R2011a in 10.10 without any problems, other than a printing bug that I managed to circumvent using the advice posted [here]("http://ubuntuforums.org/showthread.php?t=1071524&highlight=matlab+printing"). I have installed Matlab R2011a again. It runs, but there are two problems. The first is that menus don't open properly in the main terminal window (but they work fine in the editor window); if I click on a menu, it flashes up and disappears again. The second is once again the same printing problem. However, I can't use the old workaround because there doesn't seem to be any user control over the printer settings anymore.

Has anyone here had any success with Matlab in 12.04 regarding these two issues? Not necessarily with R2011a, since I can probably get access to a newer version if necessary.

And before anyone asks, yes, I have tried Octave before, but Matlab has some features that Octave doesn't have that I need, plus Matlab is provided by my workplace anyway.

---

### Post by PC_load_letter on 2012-08-14
I have 2011b and I'm running it with Linux Mint 13 under Cinnamon. I never use Matlab GUI so I never experienced any of these problems before now. If by terminal you mean the main GUI, then I have the same problem with menus but only when I use the mouse.

If you use ALT + [letter] the menus stay down and navigating with the arrow keys gets the job done.

---

### Post by Lucretia on 2012-08-16
Okay, I found the workaround again. To get more access to printer settings, I had to run system-config-printer from terminal. For some reason it was inaccessible through the dashboard thing.

---

### Post by xwilliam on 2012-08-24
I have the same problem in using the GUI with Ubuntu 12.04 and Cinnamon. Nevertheless no problem with Unity. 

I guess it is a specific problem of Cinnamon (or gnome shell), maybe due to java?

---

### Post by lethalfang on 2012-08-31
> **Lucretia said:**
> I have recently upgraded to 12.04. Previously, I was running Matlab R2011a in 10.10 without any problems, other than a printing bug that I managed to circumvent using the advice posted [here]("http://ubuntuforums.org/showthread.php?t=1071524&highlight=matlab+printing"). I have installed Matlab R2011a again. It runs, but there are two problems. The first is that menus don't open properly in the main terminal window (but they work fine in the editor window); if I click on a menu, it flashes up and disappears again. The second is once again the same printing problem. However, I can't use the old workaround because there doesn't seem to be any user control over the printer settings anymore.

Has anyone here had any success with Matlab in 12.04 regarding these two issues? Not necessarily with R2011a, since I can probably get access to a newer version if necessary.

And before anyone asks, yes, I have tried Octave before, but Matlab has some features that Octave doesn't have that I need, plus Matlab is provided by my workplace anyway.

I have the menu disappearing problem, too. 
The menu disappearing is "fixed" if I do not maximize the MATLAB windows. 
It's not really a fix, but it keeps me sane.

---

### Post by lethalfang on 2012-09-29
By the way, I upgraded to MATE 1.4, and this problem went away.

---

### Post by northcamel on 2013-01-15
Same problem in linux mint 13

---

