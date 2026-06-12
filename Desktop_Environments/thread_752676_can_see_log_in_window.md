---
title: "can see log in window"
date: 2008-04-11
forum: Desktop Environments
---

### Post by sleggy_allen on 2008-04-11
when i start my computer it would go through the normal process of loading ubuntu...and after the ubuntu logo  instead of displaying the log in window it would display  horizontal lines with weird colors...and sometimes it would display black screen and the cursor at the center of the screen...but i can't move my cursor...it seems that my screen is freezing...it will stop doing it after a few reboot...does anyone encountered this issue before?

---

### Post by warp99 on 2008-04-12
What is you video card? Can you do the following at a command prompt:

```
lspci -v |grep VGA
```
and this
```
dmesg |grep AGP
```

and post the output of both commands to this thread.

---

### Post by sleggy_allen on 2008-04-12
i just used my onboard graphics card...here are the outputs:

lspci -v |grep VGA

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) (prog-if 00 [VGA])
sleggy@sleggy-desktop:~$ dmesg |grep AGP

**********************
dmesg |grep AGP
[   48.254585] agpgart: AGP aperture is 128M @ 0xe0000000

---

### Post by warp99 on 2008-04-12
I think this will work, try the following:

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the video driver as 'vesa' and a simple resolution such as 1024x768 or 800x600. Make sure the file is written then reload the xserver, crtl+alt+backspace. Does the display come back?

If so this is the default fall back driver if nothing works, but it does not have all of the graphics features for you Intel on-board card, You can also experiment and run 'sudo dpkg-reconfigure xserver-xorg' again and choose 'intel' as the video driver to see if this works. Hope this helps.

---

