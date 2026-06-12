---
title: "x11vnc crashes the gnome"
date: 2011-05-16
forum: Desktop Environments
---

### Post by huntkey on 2011-05-16
Hi Ubuntu experts and veterans,

I'm new to Ubuntu world (3 month)... I could find solution for most problems in this forum except this one... It's very annoying and I really need your help!

I have a Ubuntu 10.10 64 bits installed on my desktop computer. I have x11vnc installed to remotely access my desktop (gnome). However recently it's been crashing all the time... My vnc session will just be terminated with an error "connection disconnected" and I can't access it anymore with error "connection refused". When this happened if I go to the computer, I see it's stopped at the "login screen". Once I logged in everything will work until it crashes again...

I tried both realVNC and Tight VNC client on my Windows PC and I have the same problem. 

The work around I'm using is to restart the service gdm. Since I enabled "login automatically" so everytime I restarted the gdm service (via a ssh session) it logs in automatically.

Here is the script I made for starting up the x11vnc. I also added it in the gnome startup application so it starts up automatically.](*,)

cat /usr/local/bin/sharex11vnc 
#!/bin/sh

x11vnc -noncache -repeat -nap -bg -many -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}"

I also tried to manually run it via the gnome x11vnc server utility (x11vnc gui menu). However the same problem still happens.

When I'm locally operating on the PC I don't seem to have the same problem... Of course I might just not work long enough for it to happen. It's possible that something else is causing this too...

Any ideas?

Thanks!
Difan

---

### Post by krunge on 2011-05-16
I'm not sure if this is your problem but fairly recently there has been a serious bug in the Xorg X server that makes it crash.  The workaround is to pass the "-noxrecord" option to x11vnc to prevent exercising the buggy code in Xorg.  Search these forums for "x11vnc noxrecord" for more info.

If that doesn't work consider the option "-noxfixes" and even "-noxdamage". Both of those have been used to work around Xorg bugs in the past.

---

### Post by huntkey on 2011-05-16
Krunge, Thank you very much for your QUICK reply!

I have put in the option -noxrecord. I will see if it will happen again. I will leave out another two options for now. This way I will know for sure which option could fix it. 

During the meantime I will read other thread about this option. 

thanks,
Difan

---

