---
title: "Type bug after update to 13.10"
date: 2013-11-14
forum: Desktop Environments
---

### Post by mikhailovav on 2013-11-14
Hi,
after updating to Xubuntu 13.10 I have this annoying type bug: some random characters in most apps can sometimes randomly scatter into pixels. You can see it with 'u' in the center of the picture. It can't be put on a screenshot (on the screenshot everything is ok), so I had to take a photo.
At first this effect even remained when scrolling page in browser or moving window. But it was possible to restore characters by selecting a text.  Now characters restore themselves when scrolling the page or moving the window.


[ATTACH=CONFIG]247817[/ATTACH]

---

### Post by ajgreeny on 2013-11-14
Try changing the font rendering settings in xfce4 settings manager, particularly the anti-aliasing, to something slightly different to what you have now.  Here's a screenshot of my settings, just to give you some idea.

---

### Post by brainwash on 2013-11-14
It looks like the corruption caused by the Intel graphics driver (gen4).

[https://launchpad.net/bugs/1098334](https://launchpad.net/bugs/1098334)

---

