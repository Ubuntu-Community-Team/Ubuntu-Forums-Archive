---
title: "Gnome Desktop - Top Bar colours"
date: 2022-09-06
forum: Desktop Environments
---

### Post by col48 on 2022-09-06
Is there a way to change the white on black of the top bar?  The white comes out rather faint on my monitor.  I'd like to change the top bar colours to something like black on yellow.  And to stay with Gnome.

---

### Post by Dennis N on 2022-09-06
At least you may be able to change the font color. Look in <theme folder>/gnome-shell/gnome-shell.css for a section like this:

```
/* Global Values */
stage {
  font-size: 13pt;
  color: #eeeeec; }

```  
For pure white, code is #ffffff.
For yellow, code is #ffff00.

This also affects the font color in any top bar application menu and any other drop down menus in the top bar.
There is no single place that sets the background color, so that would be difficult. Usually its black.

---

### Post by pantazi on 2022-09-07
Try this:

[https://www.youtube.com/watch?v=8XZ2CmaLImY](https://www.youtube.com/watch?v=8XZ2CmaLImY)

---

### Post by col48 on 2022-09-07
@pantazi

Great!  This worked for me with one change.
'Tweaks' does not have the 'Extensions' menu within which I could make the choice.  Maybe that is a change for Jammy.
But there was a separate Extension called 'User themes' whose installation added my one user theme to the list.

@Dennis
Thanks for that, too - useful.

---

