---
title: "blank white screen in with compiz, xgl, nvidia"
date: 2008-01-24
forum: Desktop Effects &amp; Customization
---

### Post by notatoad on 2008-01-24
i upgraded from a 7600gt to a 8800gts 512 recently. restricted hardware manager says i have no hardware which requires restricted drivers, so i downloaded the latest drivers off nvidia's website and installed them manually.  then i fired up compiz, everything worked.  next, i tried to enable my second monitor, and the only way i could see to do that was to configure seperate screens (no twinview) and use xinerama.  then compiz stopped working.  i had previously gotten compiz working by installing xgl-xserver, so i did that.

now when i logon all i get is a blank white screen.  super+e still gives me four desktops in the middle of my screen, ctrl+alt+left still rotates the cube, but all four sides are solid white.  alt-tab still cycles through the applications that run on startup, but they are all behind the white - i can just see their icons in compiz's alt-tab dialog.

and i can't reinstall compiz.  going to a terminal (ctrl+alt+F1) and doing killall compiz,  sudo apt-get remove compiz seems to have no effect.  compiz is still running after a reboot, and still white.

any ideas?

---

### Post by overdrank on 2008-01-26
> **notatoad said:**
> i upgraded from a 7600gt to a 8800gts 512 recently. restricted hardware manager says i have no hardware which requires restricted drivers, so i downloaded the latest drivers off nvidia's website and installed them manually.  then i fired up compiz, everything worked.  next, i tried to enable my second monitor, and the only way i could see to do that was to configure seperate screens (no twinview) and use xinerama.  then compiz stopped working.  i had previously gotten compiz working by installing xgl-xserver, so i did that.

now when i logon all i get is a blank white screen.  super+e still gives me four desktops in the middle of my screen, ctrl+alt+left still rotates the cube, but all four sides are solid white.  alt-tab still cycles through the applications that run on startup, but they are all behind the white - i can just see their icons in compiz's alt-tab dialog.

and i can't reinstall compiz.  going to a terminal (ctrl+alt+F1) and doing killall compiz,  sudo apt-get remove compiz seems to have no effect.  compiz is still running after a reboot, and still white.

any ideas?

HI, and can you boot into recovery mode then use the command startx, hopefully this will allow you to disable compiz and then may I suggest Envy to install your drivers for the graphics card.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

