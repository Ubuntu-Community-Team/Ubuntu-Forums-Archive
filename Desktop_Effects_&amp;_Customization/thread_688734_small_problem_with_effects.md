---
title: "small problem with effects"
date: 2008-02-05
forum: Desktop Effects &amp; Customization
---

### Post by Python88 on 2008-02-05
Hey all.
I recently re-installed Ubuntu after trying various other Linux distros (Ubuntu is the best one). Anyway.
My problem: when I apply Visual Effects in System > Preferences > Appearance the top part of all my windows disappear (the bar with the title of the window and the minimize & maximize buttons). They show up when I have no desktop effects enabled but as soon as I enable any they go again. Could someone help please? :(

---

### Post by Therion on 2008-02-05
Does it help if you enable the Windows Decorations plugin? 

Also, if you have an nVidia graphics card, you MAY need to install the xserver-xgl package.

---

### Post by Python88 on 2008-02-05
> **Therion said:**
> Does it help if you enable the Windows Decorations plugin? 

Also, if you have an nVidia graphics card, you MAY need to install the xserver-xgl package.

I'm not sure how to enable the windows decoration plugin (i'm a huge noob) but I installed that xserver-xgl plugin because I have a Nvidia card. I logged out and changed my default session to GNOME instead of the run x script one and that seem to have fixed the problem.
Thanks for the help. :)

---

### Post by vikasvishnu on 2008-02-06
> **Python88 said:**
> Hey all.
I recently re-installed Ubuntu after trying various other Linux distros (Ubuntu is the best one). Anyway.
My problem: when I apply Visual Effects in System > Preferences > Appearance the top part of all my windows disappear (the bar with the title of the window and the minimize & maximize buttons). They show up when I have no desktop effects enabled but as soon as I enable any they go again. Could someone help please? :(


As you might know, the Window Decorator for Compiz is Emerald. First of all, check whether you have installed Emerald correctly.

# sudo apt-get install emerald

If you have emerald installed, and if the Window Title disappers when you enable the Desktop Effects, then try loading up an Terminal and give this command:

# emerald &

This should bring back the Window Title bar. Give it a try.

---

