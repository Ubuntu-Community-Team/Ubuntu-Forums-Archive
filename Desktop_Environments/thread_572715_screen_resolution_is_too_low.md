---
title: "screen resolution is too low"
date: 2007-10-10
forum: Desktop Environments
---

### Post by seli on 2007-10-10
i just installed ubuntu and trying to set the screen resolution.  it's now set to 800x600 and taking up so much of unnecessary screen space.   the problem is that this is the largest setting available.

i'm very new to ubuntu and linux.  how can i set it so that i can use higher screen resolution?

---

### Post by GoranI on 2007-10-10
What kind of graphic card you have? Maybe you have to install proper driver for it (for Ubuntu).

---

### Post by To be confirmed on 2007-10-12
I'm having the same problem. I have the propriteary NVIDIA legacy drivers installed but I think they're still using VESA drivers. I had a look in /etc/X11/xorg.conf but the option's already there to use 1024x768 in 24-bit depth. Why can't I select this in the resolution menu?

The graphics card is a TNT2 mach64 which is easily capable of more than 800x600 at 60 Hz. The screen is a 17 inch CRT dell.

---

### Post by jiminy82 on 2007-10-12
I also have a problem with the resolution. I have a laptop with intel integrated graphics. I can get a windows driver, but  I would not know how to install it. 

thanks

---

### Post by sdn8904 on 2007-10-19
See those links

[http://www.albertomilone.com/latest_...sf_feisty.html](http://www.albertomilone.com/latest_...sf_feisty.html)
[http://ubuntuforums.org/showthread.php?t=467482](http://ubuntuforums.org/showthread.php?t=467482)

In my case, it was a problem with HorizSync and VertRefresh. When I put the correct values, and restarted, I was able to choose 1024X768

---

### Post by To be confirmed on 2007-10-19
I got it to work after a failed install of nvidia drivers (downloaded directly from nvidia). When I turned on the computer again, for some reason the resolution and refresh rate increased. I won't complain.

---

