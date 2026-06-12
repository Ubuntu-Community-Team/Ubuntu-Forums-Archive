---
title: "messed with resolutions and now no desktop effects"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by waldorf on 2007-11-19
I tried to get a dual monitor setup to work and it failed. I've got a laptop (1200x800) with an intel card and an external monitor ACER P221w 22 inch with 1600 x 1050 resolution.

I manged to get back to a situation where each screen has the correct resolution but now there is no compiz. No dektop effects. No visual effects.

When I bought the screen and plugged it in it worked fine. Right resolution and all the effects.

Is there a way to get compiz back?

Thanks in advance.

(I knew I shouldn't have tampered with the dual screen business :) )

---

### Post by waldorf on 2007-11-19
terminal output after typing compiz

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by Brian96 on 2007-11-22
> **waldorf said:**
> terminal output after typing compiz

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

I get the same output when I try to run Compiz on my custom Gutsy install. Compiz worked fine on a full install of Gutsy on this system. I, too, would like to find out what the solution may be.

---

### Post by Chen Jun on 2007-11-23
I got the same issue with my Intel 945GM on Dell D620. With a single monitor, destop effect works fine, as long as I enable dual monitor, the destop effect broke.

---

### Post by fahim on 2007-11-24
I got exactly the same problem. Does anybody find a solution?

---

### Post by ethanhunt on 2007-11-26
Same here. I have Intel 915GM on Dell 610. I got dual external monitors setup with xrandr. Now my DRI si disabled and i cannot use compiz/desktop-effects

---

### Post by Ice_cone on 2007-11-26
try 
sudo apt-get install xserver-xgl

---

### Post by fahim on 2007-11-26
Thanks that works fine. Compiz works now, but really slow... needs about 3 seconds to switch to my second desktop. Any idea?!

---

### Post by fahim on 2007-11-28
With XGL my system works really slow. I ad do remove it now. Is there any other possibility?

---

### Post by Ice_cone on 2007-11-28
> **fahim said:**
> With XGL my system works really slow. I ad do remove it now. Is there any other possibility?

I want to know as well

---

### Post by Chen Jun on 2007-11-29
I truly believe this is intel driver issue. I try to set the following line
in my xorg.conf
"virtual 2560 1024" 

After I config that, I am able to do a dual monitor with xrandr, however, as long as I add this line, the desktop effect is not able to enable, and glxinfo showing "direct rendering" is No.

I guess pretty much we have to wait for new intel driver. :-(

---

