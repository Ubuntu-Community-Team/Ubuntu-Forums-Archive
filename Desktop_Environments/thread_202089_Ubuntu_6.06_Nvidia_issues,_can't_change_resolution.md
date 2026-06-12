---
title: "Ubuntu 6.06 Nvidia issues, can't change resolution!"
date: 2006-06-22
forum: Desktop Environments
---

### Post by scottylans on 2006-06-22
Ubuntu 6.06 Nvidia issues, can't change resolution!

** I have a habit of ranting, a quick summary is at the bottom, sorry!**

Hi chaps,

I installed Ubuntu 6.06 from CD fresh 3 weeks ago or so in safe graphics mode, regular mode scrambles the graphics and crashes.

I couldn't change the damn resolution, when I chose 1280x980 or 1152x864 or 1024x768 they all don't work, it kind of kicks me out of the session and I have to log back in at 2048x1536 :(   (22" CRT, 130khz horizontal clock)

Now, I followed some instructions and ran

> sudo dpkg-reconfigure xserver-xorg

I followed ALL default prompts except I unticked 2048x1536, 1920 and stuff then I only chose the resolutions I wanted, 1440x1050 (iirc?)  1280x960, 1152x864 etc.

When I re-boot it's screwed, the small Ubuntu logo in the middle is scrambled it won't boot up to gnome and basically hangs.(just like when I boot from the CD without choosing safe mode)



**SO!**

I followed a tutorial to install the latest NV drivers, took a while but it worked! AWESOME, admitedly only 85hz mode instead of 100 or 110 like my screen can do but none the less, happy with that!! not too small and 85hz is better than 60!


**HOWEVER**


Seems the people higher up decided to release a flawed update, which hosed installs of Ubuntu with the new Nvidia drivers.
See these threads.
[http://www.ubuntuforums.org/showthread.php?t=197484](http://www.ubuntuforums.org/showthread.php?t=197484)
[http://www.ubuntuforums.org/showthread.php?p=1168472](http://www.ubuntuforums.org/showthread.php?p=1168472)
[http://www.ubuntuforums.org/showthread.php?t=197308&highlight=resolution+6.06](http://www.ubuntuforums.org/showthread.php?t=197308&highlight=resolution+6.06)
[http://www.ubuntuforums.org/showthread.php?t=187225&highlight=resolution+6.06](http://www.ubuntuforums.org/showthread.php?t=187225&highlight=resolution+6.06)   <- this one specifically


**_SO to summarise, I'm like a rock in a hard place! :(_**


If I use 6.06 install CD, apply all the updates and stick with the STOCK nv driver, it will work but ONLY in 2048x1536@60hz - OUCH OUCH UGH! :( :(

**OR**

If I use 6.06 install CD, install the NV updated drivers then apply all released updates, it will hose my install like the links above.



What's the solution, I'm so tired of re-installing from scratch, I just want to keep a copy for more than a month :(

---

### Post by scottylans on 2006-06-24
[QUOTE=scottylans]Ubuntu 6.06 Nvidia issues, can't change resolution!

** I have a habit of ranting, a quick summary is at the bottom, sorry!**

Hi chaps,

I installed Ubuntu 6.06 from CD fresh 3 weeks ago or so in safe graphics mode, regular mode scrambles the graphics and crashes.

I couldn't change the damn resolution, when I chose 1280x980 or 1152x864 or 1024x768 they all don't work, it kind of kicks me out of the session and I have to log back in at 2048x1536 :(   (22" CRT, 130khz horizontal clock)

Now, I followed some instructions and ran



I followed ALL default prompts except I unticked 2048x1536, 1920 and stuff then I only chose the resolutions I wanted, 1440x1050 (iirc?)  1280x960, 1152x864 etc.

When I re-boot it's screwed, the small Ubuntu logo in the middle is scrambled it won't boot up to gnome and basically hangs.(just like when I boot from the CD without choosing safe mode)



**SO!**

I followed a tutorial to install the latest NV drivers, took a while but it worked! AWESOME, admitedly only 85hz mode instead of 100 or 110 like my screen can do but none the less, happy with that!! not too small and 85hz is better than 60!


**HOWEVER**


Seems the people higher up decided to release a flawed update, which hosed installs of Ubuntu with the new Nvidia drivers.
See these threads.
[http://www.ubuntuforums.org/showthread.php?t=197484](http://www.ubuntuforums.org/showthread.php?t=197484)
[http://www.ubuntuforums.org/showthread.php?p=1168472](http://www.ubuntuforums.org/showthread.php?p=1168472)
[http://www.ubuntuforums.org/showthread.php?t=197308&highlight=resolution+6.06](http://www.ubuntuforums.org/showthread.php?t=197308&highlight=resolution+6.06)
[http://www.ubuntuforums.org/showthread.php?t=187225&highlight=resolution+6.06](http://www.ubuntuforums.org/showthread.php?t=187225&highlight=resolution+6.06)   <- this one specifically


**_SO to summarise, I'm like a rock in a hard place! :(_**


If I use 6.06 install CD, apply all the updates and stick with the STOCK nv driver, it will work but ONLY in 2048x1536@60hz - OUCH OUCH UGH! :( :(

**OR**

If I use 6.06 install CD, install the NV updated drivers then apply all released updates, it will hose my install like the links above.



What's the solution, I'm so tired of re-installing from scratch, I just want to keep a copy for more than a month :([/QUOTE]


Sorry to bump guys but I really wanna use this OS :(

---

### Post by patrickfromspain on 2006-06-24
have you tried install the nvidia propietary drivers?

go into synaptic, there install nvidia-glx and the linux-restricted-modules for the kernel you're running.

After that's installed, sudo gedit /etc/X11/xorg.conf and search Section device, there, in Driver, change "nv" to "nvidia".

You can also, in the Screen Monitor, put your resolution.

        SubSection "Display"
                Depth           24
                Modes           "2048x1536_100" "1024x768" "800x600" "640x480"
        EndSubSection

That should word. If after rebooting you get no X, sudo nano /etc/X11/xorg.conf and undo all changes you've made.

Hope that helps.

---

### Post by tseliot on 2006-06-24
1) Follow my guide to install the Nvidia (proprietary) driver:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

2) Then try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

