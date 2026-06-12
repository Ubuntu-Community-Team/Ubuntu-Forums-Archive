---
title: "Dual monitor &amp; workspace window dragging"
date: 2008-05-21
forum: Desktop Environments
---

### Post by csocean on 2008-05-21
Hi guys

This is my first post here, I'm a new convert to Ubuntu from Vista, and I'm utterly blown away by it!

One thing I'm trying to get working is to have dual monitors, whereby I can display one workspace on one monitor, and a separate workspace on the second. Ideally, this would extend to compiz fusion, so I can have one side of the cube on each monitor.

I'm using a nvidia.  Any suggestions would be welcomed!

---

### Post by bobjenkins on 2008-05-21
First try this Go to Compiz, under desktop Cube General Tab, Multi Output Mode, set one big cube.

I do not know how to do this personally, as I only have one monitor. I did find this though which might be helpful

[http://forum.compiz-fusion.org/showthread.php?t=4393](http://forum.compiz-fusion.org/showthread.php?t=4393)


If you get it to work it seems that each monitor will display the opposite side of the cube. (So you can't rotate the cube independently on one screen)

Pulled this off, [http://ubuntuforums.org/showthread.php?p=4836532](http://ubuntuforums.org/showthread.php?p=4836532)

> I looked at the new X configuration but since it did not have a way to add a second screen, I just went with the usual way when dealing with nvidia cards... which is a pretty nice and easy way too.

So, anyway, what you got to do (since you already have the drivers installed) is to simply open up a terminal and write "sudo nvidia-settings".

Then just go to "X Server Display Configuration" and enable the second monitor by pressing Configure and selecting TwinView. Then just set whatever resolutions you want, etc.
Finally, press Apply to see whether the configuration is how you wanted it. Notice the menu bars and any maximized windows may stretch across both monitors. Don't worry about it though, when you save the settings and restart X everything will be normal.
So, now, if you see everything is OK, simply click "Save to X Configuration file", click "Save" again, and finally, close nvidia-settings, log out, and press CTRL+ALT+BACKSPACE to restart X. Then log back in and hopefully enjoy your dual monitor set up.

---

### Post by csocean on 2008-05-21
Thanks, that's very nearly exactly what I wanted :)  It turns out it's not possible to move the cubes separately just yet, let's hope it comes in the future :)

---

