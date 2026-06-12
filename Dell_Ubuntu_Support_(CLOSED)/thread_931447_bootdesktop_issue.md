---
title: "boot/desktop issue"
date: 2008-09-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by asiancowboy on 2008-09-27
I am relatively new to ubuntu, and have come across a confounding problem.  I was hoping some one here might know what I am talking about.   

I have a dell latitude d610 using a dual boot for windows XP and Hardy.  My battery died while my computer was on, and when I went to restart ubuntu, something went wrong.  After entering in my username and password, the screen went orange(same color as the login screen)  and a pointer icon appeared.  There were no menus bars, and the pointer icon was rotated 90deg clockwise.  Similarly, the mouse function was also rotated 90deg  (i.e.-moving the mouse right moves the pointer down, although that would be a rightward motion relative to the vertical axis of the pointer)  Other than being able to move the mouse, nothing else could be done.  right clicking didn't yield any menus, and the only option (seemingly) was to shut down.  Another attempted boot yielded the same result.  I am at a loss as to what to do.

---

### Post by lswb on 2008-09-27
Try starting in recovery mode and selecting the reconfigure X server option. If you have made any sustom modifications to your Xorg.conf, drop to command line first and make a backup copy.

---

### Post by jimmyhacker on 2008-09-27
hahaha  i`had like if i had same problem.

---

