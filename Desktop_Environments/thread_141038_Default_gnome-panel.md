---
title: "Default gnome-panel"
date: 2006-03-07
forum: Desktop Environments
---

### Post by peterbras on 2006-03-07
My panels are without icons and without reaction on right-click. Already tried "Killall gnome-panel" and "dpkg-reconfigure gnome-panel" without success. 
How to reactivate Default gnome-panel?

---

### Post by ComplexNumber on 2006-03-07
are there any icons on your desktop?

---

### Post by peterbras on 2006-03-07
Yes, there are, and they works.

---

### Post by ComplexNumber on 2006-03-07
i though it may have ahd something to do with nautilus not drawing the desktop, but thats obviously not the case.
what happens when you delete the panel and then create a new one to put in its place?

---

### Post by peterbras on 2006-03-07
I can't delete, on right-click there is now menu. I killed it with Ctrl Alt F2 and "Killall gnome-panel" and restarted it with a launcher (gnome-panel) on the desktop, but the result is the same, two blank panels.

---

### Post by ComplexNumber on 2006-03-07
that does seem strange. i think i'll have to get back to you on that one. after you've rebooted your PC, is it still the same?

---

### Post by peterbras on 2006-03-07
It's the same.

---

### Post by kickaha on 2006-03-07
You might have a scrambled gconf directory.
I have gone to /tmp, removed the gconfd-<username> directory, removed the .gconf* directories under the home directory and then re-logged in.

I was operating on the theory that I was hosed either way. What I got was a vanilla-default login with stock panel contents, but I could then re-customize them.

YMMV, I backed everything up to a new directory before I did it.

---

### Post by peterbras on 2006-03-07
Bingo, that helped. Thanks

---

