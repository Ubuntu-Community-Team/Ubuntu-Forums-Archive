---
title: "Skydome Image likes to disappear"
date: 2009-03-20
forum: Desktop Environments
---

### Post by crimlaw on 2009-03-20
I have set a background image for my skydome that should appear when I bring up the desktop cube or when I unfold the cube. However, sometimes, when I restart my computer, or randomly, the image disappears.  When I go into the compiz settings, the image path still appears in the Skydome settings, but the image will not reappear until I go through the steps as if I am setting another image.  

I am running 8.10.  Any suggestions? 

Thanks!!!

---

### Post by guzz46 on 2009-04-02
I have the same problem, everytime i restart my pc the skydrome picture is not there but the path for it is still there in compiz settings manager, to re-enable it i have to untick/tick the render skydome box but i would prefer not to do that every time i start my pc.
i might try reinstalling compiz settings manager to see if that works.

---

### Post by blazemore on 2009-04-03
Is your skydome image on an ntfs partition? Maybe Compiz is trying to load the image before the ntfs partition is mounted. Try moving it to somewhere in your root partition, and having Compiz read it from there.

---

### Post by guzz46 on 2009-04-03
well its fixed now, i tried re-installing compiz but had problems with it not starting on boot so i did a complete system re-installation and everything is fine now

---

