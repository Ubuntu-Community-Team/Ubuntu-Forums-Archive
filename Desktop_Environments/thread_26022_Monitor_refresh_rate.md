---
title: "Monitor refresh rate"
date: 2005-04-11
forum: Desktop Environments
---

### Post by spencer on 2005-04-11
How can I adjust the refresh rate for my monitor in ubuntu? It is currently at 1024X768 @60Hz. I've tried the other options in screen resolution preference and still have lots of flickering.  Thanks.

-spencer

---

### Post by erkki70 on 2005-04-11
Hi,
You'll find a possible answer on the following thread, page 2.  ;-) 
[http://ubuntuforums.org/showthread.php?t=21984](http://ubuntuforums.org/showthread.php?t=21984)

Hope this helps,
Cheers,
Erkki

---

### Post by thePythonAlchemist on 2005-04-11
The best way to change the monitor's default refresh rate (vertical sync) is to just modify the xorg.conf file in /etc/X11/. Under the "Monitor" section, add (or modify) a line that says "VertRefresh x - x" where x is the refresh rate you want. Default units are in Hz, but that can be changed to MHz or KHz if you just put the units at the end of the line. I'm not sure if this will interact with the "DPMS" option, but this is the way I've always done it before.

---

### Post by spencer on 2005-04-11
Thank you! to the two of you. I'm working on it now.

-spencer

---

### Post by spencer on 2005-04-11
I really appreciate the help on this but both of  methods did not worked for me. I'm going to go blind soon if I stay on this monitor setting. Any other suggestions? Thanks.

-spencer

---

### Post by spencer on 2005-04-11
There still a little blurry but My eyes are adjusting back to normal. I was able to fix the refresh rate problem thanks to the folowing post [here](http://ubuntuforums.org/showthread.php?t=24968) and using the folowing command "sudo dpkg-reconfigure xserver-xorg" in terminal. I Went thru all the options til I made it to the display section, chose the "medium" option and added the maximum settings for this monitor, restarted computer and had a few more resolution and refresh rates to the screen resolution panel. Monitor is now much better and easier on the eyes. I hope this post helps anyone else with a similar issue. Thanks.

-spencer

---

