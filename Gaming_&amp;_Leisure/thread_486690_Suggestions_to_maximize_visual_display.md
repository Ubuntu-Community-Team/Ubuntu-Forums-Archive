---
title: "Suggestions to maximize visual display?"
date: 2007-06-28
forum: Gaming &amp; Leisure
---

### Post by LinuxBob on 2007-06-28
I have successfully accessed the restricted nVidia driver in Fiesty. My question is whether I can improve video quality, add 3D or other enhancements by obtaining and using the Nvida driver from nVidia itself., as described in this article:

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)


Any benefit? I have a ViewSonic 17 or 19" 4:3 (not widescreen) monitor of relatively recent vintage and really want to maximize the visuals for gaming. Any recommended settings? I tried setting the max resolution at 1900+ x??? but the windows extended past the width of the View Sonic and I could not figure out how to resize the desktop accordingly. Also, would love to have 3D like game displays or anything else the card and monitor might be capable of to enahnce the visual.

THanks

---

### Post by wjp.reg on 2007-06-28
IMHO I would stick with the ubuntu restricted driver and run

 After pressing ctrl-alt-backspace

and shutting down GDM. with ```
/etc/init.d gdm stop
```

run ```
dpkg-reconfigure xserver-xorg
``` as root

Then make sure you select the nvidia driver and not the nv driver when you come to that screen.

You should be safe to select the defaults for all the other selections BUT make sure you include the resolution settings you want when you get to that screen.

I have a similar monitor and use the automatic screen adjustment to position the screen appropriately.

NOTE: the refresh rate will cause the screen to adjust somewhat as well.

You can then restart your system and check the screen resolution to see if 3D is checked.

Hope this helps

---

### Post by cogadh on 2007-06-28
If you put your correct horizontal sync and vertical refresh rates into your xorg.conf file, then you won't need to use the screen adjustment to move the screen position, it will be automatically centered. It will also mean that you can set the exact refresh rates that your monitor is capable of.

---

### Post by LinuxBob on 2007-06-28
Thanks for your post!  So I understand & do not screw things up:

1) press ctrl-alt-backspace;

2) in terminal mode type in "/etc/init.d gdm stop":

3) in temrinal mode type in "sudo dpkg-reconfigure xserver-xorg";

I am then presented with screens to choose driver?  

Then I select highest available resolution?  I am presented with this menu r something?

Use auto adjut buttonn on ViewSonic?

After reboot, go to system>preferences>resolution and there will appear a box for 3D which I can then check?

---

