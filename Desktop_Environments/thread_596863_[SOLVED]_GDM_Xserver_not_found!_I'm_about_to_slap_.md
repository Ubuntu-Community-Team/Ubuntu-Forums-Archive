---
title: "[SOLVED] GDM: Xserver not found! I'm about to slap my gnome around."
date: 2007-10-30
forum: Desktop Environments
---

### Post by DaGrimReefah on 2007-10-30
I was trying to get halflife2 working, then when I restarted, POOF! my xserver no longer worked. I tweaked around, and ran
```
dpkg-reconfigure xserver-xorg
```
and
```
dpkg-reconfigure gdm-session
```
and even tried reinstalling xserver and gnome. I get this persistent error message everytime I try to "gdm start". The error in full is:
> GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx: pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/ :0. Xauth -nolisten tcp vt7 Error:Command could not be executed. Please install the X server or correct GDM configuration and restart GDM.gdm[4974]: WARNING: gdm-server-spawn: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx: pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/ :0. Xauth -nolisten tcp vt7 ^Y

Keep in mind that I did try reconfigure xserver and gnome-session, as well as reinstalls. I also have an E-machines 2.93 GHz Celeron-D processor, with a NVIDIA GeForce 6200 and 1 GB RAM. And just in case, yes I did try changing "DisallowTCP" to false in my gnome.conf. I of course changed it back, as it didn't appear to be the problem and it is apparently a security issue when not set to "true". Please help!

---

### Post by DaGrimReefah on 2007-10-30
Also that error message is in the torrid but comforting blue and white key-prompt screen, when it asks me to view the xserver error log for details.

---

### Post by DaGrimReefah on 2007-10-30
So... has anyone out there ever encountered this before?

---

### Post by Thyme on 2007-10-30
Hi DaGrimReefah,

I have never encountered this before but it seems that its not executing "/usr/bin/Xgl". Maybe try going throught the /etc/gdm/gdm.conf and gdm.conf-custom files and look under the "[servers]" section (and everything below that) to see what is being started. Maybe you have to change the X server from xgl to standard?

Hope you mange to sught this out :)

Oh, and also check that your xorg.conf file is loading the "glx" module in the "modules" section ..

---

### Post by DaGrimReefah on 2007-10-31
Thank you so much for your reply Thyme! 

It was the gdm.conf-custom file the whole time. I guess I unwittingly entered a script in my gdm-custom file thru terminal whilst trying to get HL2 working. Your suggestion really helped me out of a jam. I appreciate you and the generous folks in these forums, and my Xserver is as healthy as before. Cheers!

---

### Post by Thyme on 2007-10-31
No problem at all man. I'm glad you managed to sought it :)

---

