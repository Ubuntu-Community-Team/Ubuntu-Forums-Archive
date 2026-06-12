---
title: "Installing XGL on ATI"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by TannerLD on 2007-05-19
Hello,

I've recently upgraded to Fiesty with my dual monitor ATI 1300X card. I'd like to install XGL, but if I follow this tutorial (ignored the beryl steps):

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

I get nothing but white on the top/bottom of the screen and black on the rest. When I go back to the normal Gnome, all my panels are on the primary monitor.

How can I fix this?

Thanks
-Tanner

---

### Post by Ub1476 on 2007-05-20
You may simply follow this guide: [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29"):)

Scroll down to ..Alternate method: Using closed source FGLRX drivers from ATI.. and follow the guide from there. If you don't want to install beryl, stop here:

 * Also make this script executable: 
```

sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

---

### Post by TannerLD on 2007-05-20
Well, that worked a bit better - the little loading screen came up but never got anywhere and instead of black there was a black/white checkerboard.

I'm not sure if this will make much of a difference, but I used [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install the ATI drivers which I think uses fglrx.

Thanks
-Tanner

---

### Post by Ub1476 on 2007-05-20
Try this: 

1) Uninstall Envy drivers
2) Enable ATI graphic card in "Restricted Drivers Manager" (RDM)

I have X1400 and Envy didn't work for me. I'm using fglrx driver from RDM and XGL with beryl v. 0.2.0. Works like a charm:)

---

