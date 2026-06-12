---
title: "Desktop Appearence EXPLODED"
date: 2007-03-18
forum: Desktop Environments
---

### Post by blockdude14 on 2007-03-18
I updated my "nvidia" drivers which work fine. Once the desktop loaded, everything shows up bigger? I changed the fonts to size 8 but my windows still show up bigger and so does firefox. The buttons are enlarged. The menus and panels are also bigger. Does anybody know how to switch back so that the appearece is smaller? I'm gueesing it has to do something with the resoulution. :confused:

---

### Post by blockdude14 on 2007-03-18
can anybody help? please :confused:

---

### Post by Lord Illidan on 2007-03-18
System -> Preferences -> Screen Resolution might help.

---

### Post by blockdude14 on 2007-03-18
sorry. doesn't help. Thanks anyway. Do u know any other way?

---

### Post by StSteven on 2007-03-18
I just installed ubuntu on a system I built.  It has the VIA P4M266A north bridge with built in S3® ProSavage 8 graphics accelerator.  I have the exact same problem.  And the system>prefs>screen resolution doesn't fix the problem.  I really hope someone can answer this one.

---

### Post by hikaricore on 2007-03-19
Blockdude14,

This has to do with your driver options and resolutions set in xorg.conf.

My guess is you allowed the nvidia driver installation program configure your X server for you, aka it edited your xorg.conf.

Post the contents of /etc/X11/xorg.conf here (please use the quote block for this) and someone should be able to help you.

If you know what you're doing, try adding these lines to your "Section: Screen" part of xorg.conf:

```

    Option         "UseEDID" "False"
    Option         "AddARGBGLXVisuals" "True"

```

After saving the file you will need to restart your X server.

p.s. you can only edit this file as root or with the sudo command.

---

