---
title: "How do i change my resolution?"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by nephron222 on 2007-07-02
I have a Dell Inspiron 630m and i only have one resolution setting and i know it can go higher than that. Every time i mess with the xorg.cfg it wont even let me login. I dont know what to do anymore! Can anyone help  me?

---

### Post by nephron222 on 2007-07-03
anyone?

---

### Post by pandion on 2007-07-30
Hi,

Have you searched through some of the other resolution problem posts on here?  There are a lof of them, and there may already be an answer to your problem in another thread.  I haven't looked yet myself, but maybe this can be of some help.

Is it the desktop screen resolution that you are trying to change, and if so what version of Ubuntu/Kubuntu/Xubuntu are you using?  I have seen Ubuntu Edgy Eft v6.10 on a desktop PC (not a laptop/notebook like yours) only show one screen resolution and refresh rate availabile when trying to change it through the GUI.  This was because it did not detect the make and model of the monitor.  In this case, I looked up the refresh rates of the monitor being used and manually edited the XORG.CONFG file (added a section for the Monitor with the proper refresh rates etc.) to allow changing the resolution as well as the refresh rate.  That PC also has an nVidia video adapter, which required some additional work to get that supported properly before dealing with the monitor (using the nVidia legacy driver).  I did find that Kubuntu allows you to change the resolution more easily within System Settings/Monitor and Display since it has a list of many manufacturers and models of monitors.  If the monitor is in the list, just select the Monitor model and you can change the resolution right there in the GUI without having to do any manual editing (you will need to click on the Administrator Mode button and enter your password to make these changes).  I have not tried changing the resolution on my notebook PC yet, but it is running Xubuntu Feisty Fawn v7.04 (it does not have any other resoluitons listed in the GUI).  I assume it can still be changed by manually editing the XORG.CONF, but I haven't tried it yet. 

If you post your XORG.CONF on here along with the modes your laptop display supports etc. (I'm not sure what modes mine supports yet) maybe we can figure it out.  I don't think changing the XORG. CONF should prevent you from  logging on unless there is something wrong with it.  When this happens, the easy fix is to keep a backup copy and switch it back by booting with a Live CD.

If you need info on XORG.CONF, this is a good reference:
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by splintercellguy on 2007-07-30
Try sudo dpkg-reconfigure xserver-xorg?

---

