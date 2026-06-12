---
title: "Please help with Setting Screen Resolution  PLEASE"
date: 2008-05-09
forum: Desktop Environments
---

### Post by rayinvan on 2008-05-09
Hi all, 

I go Unbuntu 8.04 installed and updated and all is looking good. However I had to download the Nvidia drive because I could not set my screen resolution. 

So I did that and all went well.  I can not access preferences>screen resolution and I can select 1440 x 900 which is correct for me. I ran this with Ubuntu 7.1

The problem however is that the display window to set the resolution is so big that I can not access the accept button at the bottom of the menu to set confirm the resolution. 

So in the end I can not change the resolution.  Can I edit a file somewhere to do this?  Or how can I get this window to resize so I can select the accept button. 

Ray

---

### Post by MaindotC on 2008-05-09
You can press the tab button and when you think it is highlighted you can press the carriage return.  It should be the first button on the lower right, so probably the first ctrl + tab from the top of the pop-up window.

If that doesn't work, you could press ctrl + f2 to open up a terminal, log in as root, and edit the xorg.conf file:

```

sudo nano /etc/X11/xorg.conf
[code]

Look for a section that says something like mine (which is ATI):

[code]
Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1600x1200"
        Horizsync       31.5-74.7
        Vertrefresh     56.0 - 65.0

```

When you're done editing this file, press ctrl + x to exit and save changes.  Restart your x-server by pressing ctrl + alt + backspace.

---

### Post by MaindotC on 2008-05-20
rayinvan what's the status on this?  Are you still having problems?

---

