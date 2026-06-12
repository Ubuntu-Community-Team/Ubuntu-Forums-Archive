---
title: "&quot;Desktop Effects could not be loaded&quot; but they work?"
date: 2008-12-26
forum: General Help
---

### Post by BEN!!! on 2008-12-26
ok im editing this. i poked around at it and checked some other threads with problems with compiz, and found post telling to add a new service named "compiz" with command "compiz --replace". rebooted and whatnot. now desktop effects are enabled and working, so i changed my resolution in xorg.conf back to what it should be. now login screen looks correct. so far everything seems to be back to operating the way as before except for conky... my .conkyrc is set up for conky to be sticky and appear on all workstations. when i reboot, conky will only appear on one workstation, but ending the process and restarting it makes it appear on all workstations. but thats no big deal, ill hopefully figure that out unless someone knows a quick resolution. ill just leave the original post here as well:

_____________________________________________
well just like 90% of others i am somewhat new to linux. the video card being used is an nvidia 7300. 

i had troubles with the desktop effects after installing the card a while back but i just ignored it. after my windows hd crashed i decided to reformat all my drives to start off fresh. after reinstalling windows and ubuntu (2 separate drives) my desktop effects would then work. 

everything worked fine for months untill i decided to go into "screens and graphics". i noticed it said "Graphics card (VESA driver (generic))" and the drop down menu for driver had "nvidia" selected. so after also having some difficulty with graphics on certain games, i decided to poke around in the driver selection. it was defaulted "choose driver by name: nvidia". i decided to change it and selected driver for model Geforce 7 series in hopes it may correct my graphics issues. 

i rebooted. computer went to login screen that was set to like 1900xsomthing resolution so everything was shifted, but that was an easy fix. logged in. went to switch to another desktop (had desktop cube enabled) and noticed my desktop effects were no longer enabled. so im thinking it just disabled them when switching drivers. i went in to change desktop effects back to "extra" and got the unholy "desktop effects could not be enabled". then the mouse froze, screen flickered, and desktop effects were then enabled. curious about this, i rebooted,
logged in with the funky login resolution screen, and again, desktop effects were no longer enabled. so then i decide to switched the driver back to "choose driver by name: nvidia". rebooted, etc. and same result.

so i ended up using the same driver as before, but now have a login screen at a high resolution (which is not that big of a deal, ive fixed that before) and desktop effects that have to be re-enabled and all reconfigured after a reboot.

anyone know where to go with this? im not sure of what files to include in this post. thanks

---

