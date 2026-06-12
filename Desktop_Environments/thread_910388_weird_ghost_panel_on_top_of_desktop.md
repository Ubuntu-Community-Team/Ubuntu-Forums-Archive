---
title: "weird ghost panel on top of desktop"
date: 2008-09-04
forum: Desktop Environments
---

### Post by petehalatsis on 2008-09-04
I tried to search for this issue but its hard to know what to call it. I recently reinstalled Ubuntu and replaced the new home directory with my old one. Everything works great except on the desktop (maximized windows dont have this problem) there is like a ghost-panel. Icons look fine over it but the image of the icon stays there even if i move it.

I have a screenshot since i am sure my explanation sucks ^.^

---

### Post by petehalatsis on 2008-09-07
Lots of responses.... (sarcasm for those that dont get it)

I have found that if i kill nautilus that it will remove the ghost panel. I have deleted the .nautilus folder but it keeps showing up when i relogin. I have also found that the "ghost panel" does not show up if i use the 2D nv graphics card. 

Now, if someone can please explain WTH this means and how to permanently fix it, i would appreciate it.

---

### Post by Shazaam on 2008-09-07
The one along the top left, right?
It looks like two titlebars for unfocused Firefox windows to me that is slightly rotated. Are you sure that it's not part of the picture you have as a desktop background? Change backgrounds and see if it goes away.

---

### Post by kef_kf on 2008-09-08
i had the exact same problem ([my post here]("http://ubuntuforums.org/showthread.php?t=801906")) but somehow it fixed itself. im not sure but switching to binary drivers from the nvidia website for my videocard might have done the trick. you may want to try that as a last resort.

---

### Post by billgoldberg on 2008-09-08
Strange.

Are you using Compiz Fusion?

Have you tried completely removing and reinstalling gnome-panel (use alt+F2 to launch synaptic after removing the panels)?

Do you have your graphics card drivers installed?

---

