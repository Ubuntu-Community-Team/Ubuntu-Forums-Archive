---
title: "Top panel shifts down when hidden?"
date: 2010-10-23
forum: Desktop Environments
---

### Post by littelbro14 on 2010-10-23
I know, minor problem. But on an otherwise clean and fresh looking desktop, that small shift down tends to throw off my chi. Also, it does tend to get in the way a bit, such as obscuring my options button in Chrome, rather than just taking up a bit of unused space on my tabs bar. Wasn't having this issue with 10.04, but started happening immediately after upgrade.
Example of what I'm talking about:
Unhidden
[http://imgur.com/rkgxJ.png](http://imgur.com/rkgxJ.png)
Hidden
[http://imgur.com/nGC62.png](http://imgur.com/nGC62.png)

---

### Post by Tamlynmac on 2010-10-23
One thought is, it appears you may have "show hide buttons" turned on in your panel  properties? The button appears in both your screen shots. I've find the  button unnecessary and turn it off. By simply moving my mouse to the top  of the screen (in auto hide) the panel becomes viewable. The delay time  is adjustable in the configuration editor.
*
right click on panel and select properties. On the general tab is there a check mark in front of "show hide buttons.
*

Just another quick thought, if you need to keep the button. Have you  checked the auto_hide_size in the gnome configuration editor?
*
menu/system/configuration editor/apps/panel/top_panel_screen/auto_hide/size
*

This particular key determines the visible number of pixels when the  panel is hidden in a corner. It will take a value lower than zero, which  may move it off the screen. Even it it drops down at least you may be  able to make it small enough that it becomes a non-issue or even move it  off the screen.

Good Luck and hope this helps

---

