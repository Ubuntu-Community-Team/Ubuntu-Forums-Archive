---
title: "Change Screen Resoulation"
date: 2006-09-03
forum: Desktop Environments
---

### Post by m.h.shams on 2006-09-03
dear friends,

i can't access locally to my ubuntu linux. i use vncviewer from 
Win XP to connect ubuntu. my ubuntu has no monitor, keyboard, and mouse,

when i connect it remotely, screen resoulation is 640 * 480 and
i can't change normally, when i use screen resoulation, it seems that my linux only support 640 * 480,

can i change this resoulation manually from a config file ?

plz help me.
Thanks All

---

### Post by goatflyer on 2006-09-03
I'm assuming your video is misconfigured to a resolution not supported by your monitor.

Try this:

Power on your Ubuntu box, if you see text characters fine but later nothing when it goes to video, then try this:

Wait for the usual time it takes to get to the login screen (even though you can't see anything).

Hit Ctl-Alt-F1  you may see a text login prompt.

Login as normal.

sudo dpkg-reconfigure xserver-xorg

choose 'safe' resolutions for now.

reboot, you should have video now.

---

