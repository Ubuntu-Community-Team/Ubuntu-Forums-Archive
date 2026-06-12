---
title: "NVIDIA geForce - Input Type not supported"
date: 2009-01-03
forum: Desktop Environments
---

### Post by arluijen on 2009-01-03
Ok, I'm getting realy tired of this. After installing Kubuntu (kde 4.1), I'm having trouble finding the optimal screen resolution on my Acer AL1916W monitor.

The logon screen looks ok, after logging in I also get to see my desktop with the correct resolution but then it goes black and my monitor tells me 'Input Type not supported'

When I reset the X-server in recovery mode it starts up ok in a 800 resolution. I then manualy change the xorg.conf (as: [http://ubuntuforums.org/archive/index.php/t-202934.html](http://ubuntuforums.org/archive/index.php/t-202934.html) but with my Nvidia driver instead), resulting in the 'Input Type not supported'.

using the Nvidia driver tool tells me I should run nvidia-xconfig as root but this again tells me I should put a driver in the device line of xorg.conf. Doing this, again gives me the 'Input Type not supported'.

What realy bothers me is that the logon screen is ok, the splash screen after that too and the first two seconds I even get to see my desktop but then it stops.

I'm all out of ideas...

---

### Post by benerivo on 2009-01-03
Sounds like it is a kde4/desktop environment issue. Try installing another desktop environment such as fluxbox and then check if you can log in to that without a monitor error message. Have you made any changes to the monitor controls from within the kde4 system settings? The message may be related to a display frequency that is out of it's range, but this is just a guess.

---

### Post by arluijen on 2009-01-04
installed fluxbox, but when I run the Nvidia X server settings tool the same error (run Nvidia xconfig as root).

Using xrandr returns only the 800x600 mode and the 640x480 mode. 

I'm going to try and change the Xorg.cong again, but I'm not hopeful.

---

### Post by arluijen on 2009-01-04
Hold on, I ran the nvidia-xconfig and this time no errors. Fluxbox runs ok, I even installed Gnome and that works perfect also. I'm convinced; don't use KDE.

---

### Post by bunty on 2009-01-06
The login screen is displayed on the frame buffer, not through xserver. X is not started at the point, that's why it looks OK. It has nothing to do with X driver or resolution.

The problem with kde is that it is far more than a "desktop manager". The project aims to be like windows and as such tries to take over as much of the hardware as it can get it's hands on.

I disagree with doing things like that and prefer a DM that is a DM .

---

