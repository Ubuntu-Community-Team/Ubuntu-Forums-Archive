---
title: "Screen Resoloution Problems"
date: 2009-04-30
forum: General Help
---

### Post by jackhe22 on 2009-04-30
Hello everybody,

I'm using Ubuntu 8.04 LTS, and I have a Nvidia GeForce 7600GS graphics card. The screen resoloution options I get are:
640x480 and 800x600, when usually I should be getting 1280x1024!
When I installed the Restricted Drivers it got worse:
640x480 and 320x240, which is really wrong. So is there some way of forcing 1280x1024 without breaking anything?

Any help would be appriciated,
Thanks
Jack.

---

### Post by jackhe22 on 2009-04-30
Bump :-)

---

### Post by sdowney717 on 2009-04-30
I do think you have to run a nvidia config setup after installing the driver.
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/chapter-03.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/chapter-03.html)

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/index.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/index.html)

---

### Post by CatKiller on 2009-04-30
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by jackhe22 on 2009-05-01
Sorry, but whats xorg? and do I type the top two commands into terminal?

---

### Post by CatKiller on 2009-05-01
> **jackhe22 said:**
> Sorry, but whats xorg?

[http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)

 > and do I type the top two commands into terminal?Yes.

The first command makes a backup of your configuration, and the second command opens it for editing.

---

### Post by jackhe22 on 2009-05-08
Okay, heres a problem, there's nothing in xorg. Just 100% blank. Don't know why, can somebody help there?

---

### Post by Tipped OuT on 2009-05-08
Well no wonder, try reseting it to its default state.

---

### Post by CatKiller on 2009-05-08
> **jackhe22 said:**
> Okay, heres a problem, there's nothing in xorg. Just 100% blank. Don't know why, can somebody help there?

I suspect you've opened a new file. Case is important. Capital X for X11, lower-case x for xorg.conf.

---

