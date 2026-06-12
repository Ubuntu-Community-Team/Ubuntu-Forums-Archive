---
title: "Can't get Valves Steam running"
date: 2014-05-01
forum: Gaming &amp; Leisure
---

### Post by beeemceearts on 2014-05-01
Hi, i've been trying to run Steam on my Ubuntu 14 all yesturday and it doesnt work for some reason. When i start steam launcher a window pops up saying "verifying installation", its there for a little while and then its gone and gone with it are any lifesigns of the process. The steam process stays idle in the background and can be found and terminated in the system monitor. If i start steam from the terminal here is what heppens:

> Running Steam on ubuntu 14.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
[0501/155510:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
Installing breakpad exception handler for appid(steam)/version(1398287272_client)
Generating new string page texture 12: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 13: 256x256, total string texture memory is 311.30 KB
Generating new string page texture 14: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 15: 384x256, total string texture memory is 835.58 KB

At the last line it freeses and nothing happens. Anyone can point out what may cause this?

---

### Post by MikeCyber on 2014-05-01
I would check 
- enough space
- not root user
then delete and reinstall. 
Search online for dependencies, install instructions. Maybe someone with the same computer specs has found online a solution, last ask in steam forum for help.
You have an error, so probably reinstall fonts or google for alike.
Try also the installer from the steam website.

---

### Post by beeemceearts on 2014-05-01
Ok guys, believe it or not but i have solved my own problem...Which is not usually how things go for me when it is Linux related.
But since i've wasted a lot of time on this i thought i could share with anyone who might be in the same situation so here it goes:

I've already lost all hope of running steam when suddenly i've noticed that **glxgears **test stopped working for me. I poked around a bit and because i am not a good Linux user it ended up with me deleting the fglrx package and damaging the xorg xserver process. Of cource i had no idea about that until i rebooted, and boy was i surprised to see nothing on the screen instead of a booting logo. 

Anyways, once i pinpointed that the xserver is not working i used **apt-get install xorg **and it installed a whole bunch of packages one of which must have been the xserver. After that there was no problem with the steam launcher. Didnt need to reinstall, didnt need to delete appcache folder, worked like a charm.

[B]Brekdown of my actions:
[/B]1) Removed **fglrx **and all related packages(like ccc and update ones). Did it via the synaptic package manager.
2-a) Removed xserver-xorg (well, not really removed, but my actions caused it not to work. Pretty shure if you just remove all xserver related packages with synaptic the result will be same if not better)
2-b) Rebooted.
3) Reinstalled the whole xorg package. Did it with terminal(obviously).

In conclusion i want to point out that this information should not be taken as a solution. Dont be an idiot about removing things like i did. **Try this at your own risk and ONLY if your glxgears test fails**. Also the video **card was of Radeon family **so if you are rocking an Nvidia thingy this is probably completely inapplicable to you.

---

### Post by MikeCyber on 2014-05-02
Good, if you have low fps check that the proprietary AMD driver is installed.

---

