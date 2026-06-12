---
title: "Display issues!"
date: 2005-04-13
forum: Desktop Environments
---

### Post by Triton on 2005-04-13
I've been through all the posts and can't seem to fix this one!  This problem kinda falls under the same topic as "640x480 resolution only".

My problem is with VertRefresh.  My login screen is set to "1280x1024x75Hz" based on the specs of my flat panel this resolution is supposed to be this "1280x1024x60Hz", on login my monitor is set "out of range".  I edited the xorg.conf to make sure that the VertRefresh was set properly "51-76", these values are straight from the spec sheet on this flat panel (HP 1702).  Using Screen Resolution I only get 75Hz as a choice for VertRefresh.  I have also run a reconfig and this did not change anything.  Being a newbie to linux (Ubuntu) I'm clueless on this one.

Please help!   [-o<

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=Triton]I've been through all the posts and can't seem to fix this one!  This problem kinda falls under the same topic as "640x480 resolution only".

My problem is with VertRefresh.  My login screen is set to "1280x1024x75Hz" based on the specs of my flat panel this resolution is supposed to be this "1280x1024x60Hz", on login my monitor is set "out of range".  I edited the xorg.conf to make sure that the VertRefresh was set properly "51-76", these values are straight from the spec sheet on this flat panel (HP 1702).  Using Screen Resolution I only get 75Hz as a choice for VertRefresh.  I have also run a reconfig and this did not change anything.  Being a newbie to linux (Ubuntu) I'm clueless on this one.

Please help!   [-o<[/QUOTE]

My wife has a flat panel (Cornea CT1702T), and when configuring xorg for her machine I just comment out the vertical and horizontal refresh lines; they might not be necessary for LCDs, and X runs fine without them.

---

### Post by kuleali on 2005-04-13
post youre xorg log.

---

### Post by bluefreak on 2005-04-14
yeah when i upgraded from hoary preview to the final one i had this problem too, the monitor said out of sync.

thanks stormy eyes, i followed your advice and removed the vert and hor refresh, and now the display is working as per normal.

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=bluefreak]yeah when i upgraded from hoary preview to the final one i had this problem too, the monitor said out of sync.

thanks stormy eyes, i followed your advice and removed the vert and hor refresh, and now the display is working as per normal.[/QUOTE]

No problem. I'm glad it helped. Personally, I think the vert. and hor. refresh are settings specific to CRT displays; I have to set them for my display if I want it to work, but I have to get rid of them if copying an xorg.conf file from my machine to my wife's.

---

