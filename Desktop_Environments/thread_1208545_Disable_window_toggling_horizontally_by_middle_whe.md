---
title: "Disable window toggling horizontally by middle wheel button"
date: 2009-07-09
forum: Desktop Environments
---

### Post by chang5562 on 2009-07-09
I removed all the shortcut keys on this action.  But the middle wheel button on  a mouse still can toggle the workspace left and right. It is annoying. How can I stop it?

The slidepad mouse on the Notebook will not show this, because there is no middle wheel button.

I tried the xmodmap -e "pointer = 1 2 # # #" with various number , none of the combinations worked. I also want to disable the right button.

Because I am creating my customerized Live CD of the Ubuntu 8.10 and 9.04, so I need the set-up can be transferable.  The change of xorg.conf will not serve the purpose.

---

### Post by chang5562 on 2009-07-09
I played more with the mapping number inside the "pointer = 1 2 ..." and found the solution.  

However, I am not satisfied with the solution. because the scrolling of the page up/down by the wheel button won't work within a large document.

Also tried to set the num_workspace to 1 inside the gconf-editor /apps/metacity/general/, but no change.

---

### Post by chang5562 on 2009-07-10
My solution:
   xmodmap -e "pointer = 1 6 2 7 8 3 4 5"
works well on Ubuntu 9.04 , but not with the 8.10.  On 8.10 hardy, if I plug in a mouse after the system is on, the xmodmap set up rolls back to default.

   the settings above disables the middle wheel button and only gives the right button with "paste" function. 

   In order to meet all different mouse types, one can swap more mapping number up to 32.

---

