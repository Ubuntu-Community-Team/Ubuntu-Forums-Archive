---
title: "[SOLVED] Checking for Xgl: not present."
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by vinutux on 2007-11-13
i have Ati Radeon x700 pro after installing gusty i downloaded and install Ati driver(fglrx) from ati/amd site.after installing and restarting everything worked exept compiz ...............:(:(:(

i am try to enable it on appearence->visual effect but no luck

some infos i get
..............................................
[COLOR="Red"] fglrxinfo[/COLOR]

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

...................................................................................................
[COLOR="Red"]
glxinfo | grep direct[/COLOR]

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

..............................................................................................

[COLOR="Red"] compiz[/COLOR]

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

...................................................

Pleeeeeeeeeeeeeez help meeeeeeeeeeeeeeeee:(:(:(

---

### Post by solar george on 2007-11-13
Did you try using the restricted driver manager to install the driver.


Also try installing the xserver-xgl package.

Edit: 

Have you seen
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Rupertronco on 2007-11-13
That's because you're not using the correct driver, you no longer need Xgl so don't worry about that ATi finally got their act together. Your glxinfo shows that you're using the mesa driver and you don't have direct rendering enabled, which is required for compositing. See how it says Mesa for your driver instead of fglrx?

The best way for a user that's newer to the compiz scene to install their drivers is via envy, which is in the repos. Download envy and have it install and configure the latest ati driver, or you can use the restricted driver utility.

---

### Post by biltek on 2008-02-04
can u post the fix here so others can see it.

---

### Post by vinutux on 2008-02-05
itz just nothin install latest driver from AMD/ATi site and install "xgl-server" -> log out  --- Done :popcorn:

---

### Post by duo001 on 2008-03-31
What if you are unable to install xserver-xgl?

---

