---
title: "Gnome3 slow rendering"
date: 2011-05-13
forum: Desktop Environments
---

### Post by duo_pendulum on 2011-05-13
Hi,
I've problem with Gnome3 installed in Ubuntu. Historically it was ubuntu 10, then I've made dist-upgrade to 11 (Natty). 
Gnome(Unity) was working fine at that time.
Next I've made decision to switch to gnome3 and my problem was started.

GNOME-Shell: starts but desktop and application view rendering is working veeeeeeery slow
GNOME-classic: desktop rendering don't work at all (desktop refreshing) is not working. Compiz is running (but of course no visual effects I can observe). Applications rendering works fine.
GNOMR-classic (without visual effect): works properly

But it looks problem is not conected with cpu usage or memory consumption. Below are several processes order descending by cpu consumption:

 5.7 /usr/bin/gnome-shell
 2.5 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-Ekmlpy/database -nolisten tcp vt7
 0.5 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
 0.4 [kworker/0:0]
 0.2 -bash
 0.1 /usr/lib/policykit-1/polkitd
 0.1 /usr/bin/python /usr/bin/gwibber-service

I can also press CTRL+ALT+F1 and navigate in console with easy. 
Probably it is not conected stricly with gnome3 because compiz not working properly too
Plymouth - is switched off
Maybe it is something with GLX X Serever drivers. I've checked log files and NVIDIA starts fine except one thing:

in '/var/log/Xorg.1.log' I've found 
> 
	xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call
	Please consult the The X.Org Foundation support


If you need more information about upstart events or full list of processes or NVIDIA log I can of course provide it.

My hardware configuration:
AMD 64 3200+
1.5 GB RAM
NVidia GeForce 6600(128MB) PCIExpress(x16)

My linux config:
kernel 2.6.38-8-generic
XServer resolution: 1280x1024

---

### Post by afrodeity on 2011-11-07
I've noticed that applications run slower in Gnome3 than in Unity. Also, there are often freezes and delays when switching activities. Not sure what this has to do, will take a look in my system logs.

---

