---
title: "Compiz has messed with all of my window settings"
date: 2008-04-18
forum: Desktop Effects &amp; Customization
---

### Post by MedellinManDem on 2008-04-18
Hi, since I've had Compiz fusion on my PC (most of the boxes are now unticked) it makes most of my windows open above the panel at the top, so I have to move them before I can minimize/maximize/close them. Also it makes it so, when enlarged, I have to move them to access the bottom buttons e.g. help or close. 

It's really annoying, and I'm beginning to realise that Compiz was just a waste of time tbh. Any help on how I can get my window settings back to normal?

---

### Post by pietjanjaap on 2008-04-19
start ubuntu in safe mode,
Then sudo dpkg-reconfigure xserver-xorg   

Choose vesa driver
choose the screen resolution you use, the other disable.
save xorg file

your screen settings are now on default(like windows safe mode)

reboot

installOr reinstall
xgl server and compiz

then install video driver(i did this with envy)
video driver must be last installed.

---

