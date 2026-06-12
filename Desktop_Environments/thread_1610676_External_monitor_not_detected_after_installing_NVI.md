---
title: "External monitor not detected after installing NVIDIA accelerated graphics driver"
date: 2010-11-01
forum: Desktop Environments
---

### Post by jacob.david on 2010-11-01
I have installed Ubuntu 10.04 LTS on a Lenovo SL500. I have attached a 22 inch Samsung LCD monitor to the Nvidia graphics card. Everything works fine with a default display driver. But if I install a NVIDIA accelerated graphics driver then the external LCD monitor is not detected at all. Could someone please help me out?

---

### Post by P4man on 2010-11-01
Have you tried enabling the external monitor with your laptop hotkey (usually Fn+some function key) ?

---

### Post by efflandt on 2010-11-01
How is the external display connected (VGA, DVI, HDMI)?  Did you try booting with the external display already connected and on?  Or if you connected it later, try logging out of X and back in (if your laptop Fn hotkey or NVIDIA X Server Settings cannot find it).

If it is connected with DVI (or possibly HDMI) the nvidia drivers sometimes assume VGA (CRT) instead of digital (DFP).  So you might try adding the following  to Screen or Device section of /etc/X11/xorg.conf (use sudo before whatever editor):

Option "UseDisplayDevice" "DFP"

That should not interfere with your laptop display which is considered DFP.

---

### Post by jacob.david on 2010-11-16
My secondary monitor is enabled and working perfectly with default driver. So I think it is already enabled.
As for the connection, it is already connected through a VGA cable.
Please let me know whether there are any other option?

---

### Post by nova2wl on 2011-02-04
Anyone find a fix for this? I am having the same problem. 

From a fresh install of 10.10 my external VGA monitor works fine. Well it only mirrors my main laptop monitor but it does detect it. However, after install the Nvidia driver which allows me to use desktop effects my external monitor isn't even  detected.

---

### Post by andrejt on 2011-02-22
I have exactly the same problem on HP 8540p, and am using a docking station with the notebook lid closed, so I use only external monitor. With the default driver all is OK, after installing the nvidia driver, the monitor shuts down, I suspect for trying to use invalig resolutions which are auto-detected.

---

### Post by 130s on 2011-02-25
I think I used to have a similar/the same phenomenon, but now I'm able  to use external monitor via nvidia driver. Here's my solution & its reaction in order:

** Step-1**. I had following 2 issues.
 Iss-1. No image shown on VGA external display after log-on concole is  shown, even though it shows something during booting process.
 Iss-2. "Monitor" tool says following msg:
> 
"It appears that your graphics diver does not support the necessary  extensions to use this tool. Do you want to use your graphics driver  vendor's tool instead?"
So I added the followin single line to /etc/X11/xorg.conf and reboot.
> 
    Option "TwinView"
[B]

Step-2[/B]. Step-1 resolved Iss-1, and now both 2 displays (local,  external) shows desktop, but still needs configuration (eg.  layout/resolution of either/both monitors) Then execute on terminal:
> 
% gksu nvidia-settings
**Step-3**. "NVIDIA X Server Setting" window appears. Clicking "X Server Display Configuration" will show configuring screen

It took me a long time to realize the letters are clickable on "NVIDIA X Server Setting" window in Step-3. And the key to me was that NVIDIA's window already showed my external monitor (as "CRT-0"), which implied the NVIDIA's driver recognized my monitor. So I guessed it just needed a proper configuration since it's recognized. I might have been right.

Hope this helps.
Isaac
- Env: Ubuntu 10.04 LTS, Sony Vaio VGN-FS92S

---

