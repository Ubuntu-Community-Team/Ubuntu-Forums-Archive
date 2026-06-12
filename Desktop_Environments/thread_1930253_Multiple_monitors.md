---
title: "Multiple monitors"
date: 2012-02-23
forum: Desktop Environments
---

### Post by sefs on 2012-02-23
Hi I have a laptop with an external LCD monitor attached.  

I want to use the external as primary display.  So I have extended the desktop with the external on the left (primary), and laptop screen on the right (extended).

The problem is when some dialogs appear they appear in the extended area first and not the primary area.  I then have to open the laptop cover drag them over, close laptop cover, rinse and repeat.

I really want to only use the external.  I had to do the expand desktop to get a proper resolution on my external monitor.

The question is, is there someway to force all windows to open up in the primary screen by default? 

Thanks.

---

### Post by cortman on 2012-02-23
If you really do have the external set as primary, windows should open in it by default.
I have an identical setup- I have my laptop (15.6") on the right, and a 24" external plugged into HDMI on the left. I wrote a little bash script that detects if my HDMI monitor is plugged in, and if so, sets it to primary. I added it to my "Startup applications" (System Settings>) to run on boot.

Note: This assumes you're connecting your monitor via HDMI. If it's VGA or DVI, change the grep accordingly.

```
#!/bin/bash

chdmi=xrandr | grep "HDMI1 connected"

if [ -n $chdmi ] ;
then xrandr --output HDMI1 --primary ;
else
xrandr --auto
fi
```

---

### Post by sefs on 2012-02-23
How would I adjust this script for vga?

I tried running the script and it puts now my top bar on the extended monitor the laptop screen. 

instead of on the external primary screen.

---

### Post by cortman on 2012-02-23
> **sefs said:**
> How would I adjust this script for vga?

I tried running the script and it puts now my top bar on the extended monitor the laptop screen. 

instead of on the external primary screen.

That's because you have your monitor plugged into VGA. The script as written tests the HDMI port, finds that nothing is plugged in, and thus sets the primary screen to the laptop. For VGA it'd be

```
#!/bin/bash

chvga=xrandr | grep "VGA1 connected"

if [ -n $chvga ] ;
then xrandr --output VGA1 --primary ;
else
xrandr --auto
fi

```

---

### Post by sefs on 2012-02-23
Hi thanks,

I tried the script at bootime, but some dialog boxes are still appearing in the extended area.

I wonder if this is a bug.

---

### Post by cortman on 2012-02-23
I guess it could be. I've never experienced this that I can recall.

---

