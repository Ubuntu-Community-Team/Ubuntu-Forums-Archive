---
title: "help with xrandr and defining dual displays"
date: 2009-03-23
forum: General Help
---

### Post by sa125 on 2009-03-23
Hi - 

I just got another display for my desktop, which is identical to the one I previously had (Philips 19"). That screen is best run in 1280x1024@60 Hz. After connecting both displays, Both defaulted to 1024x768 resolution, while the previously available 1280x1024 resolution vanished from available selections. 

My graphics card is Intel 82Q35 Express Integrated Graphics Controller. It has a VGA and Digital outputs. The screen connected to the VGA display is properly recognized by ubuntu as philips 19", while the other screen is listed as unknown (but is also philips 19").

After being advised to try and use xrandr, I added the new mode (based on the man page):
```

$ xrandr --newmode "1280x1024" 109.62 1280 1336 1472 1720  1024 1024 1026 1062 
$ xrandr --output TMDS-1 --mode 1280x1024

```
I then used the grandr tool to position the screens and set the resolutions, and everything looked great. After rebooting, both displays resorted back to the degraded resolution of 1024x768, and were also mirrored. 

I tried setting the mode again to 1280x1024 using the latter command, and I got the error:
```

$ xrandr --output TMDS-1 --mode 1280x1024 
xrandr: can't find mode 1280x1024
```
So, I tried adding that mode again using --newmode, and got the error:```

$ xrandr --newmode "1280x1024" 109.62 1280 1336 1472 1720  1024 1024 1026 
X Error of failed request: BadName (named color or font does not exist)
  Major opcode of failed request: 152 (RANDR)
  Minor opcode of failed request: 16 ()
  Serial number of failed request: 15
  Current serial number in output stream: 15
```

So, two questions - 
1. how do I restore that lost mode?
2. how do I make this resolution settings permanent for both screens? 

thanks!

---

