---
title: "Compiz and video drivers problem"
date: 2011-09-07
forum: Desktop Environments
---

### Post by fnadde42 on 2011-09-07
Hello Forum!
I have searched and searched for a solution for this problem but I can't find it anyware, so I'm posting my problem here.

I have just recently bought a new computer and wanted to run Ubuntu on it. I booted it up for the first time and logged in with Unity. However, a pop-up warned me that drivers needed to be installed in order to make Unity work. So it logged me in using "*Ubuntu classic (no effects)*" and right after that I installed the driver via the built-in hardware drivers application.
I restarted the computer and Unity started to work. But as many Ubuntu users I wanted effects with Compiz so I started it and turned on the "Cube". A new pop-up told me that*

"*Plugin Desktop Wall provides feature largedesktop which is also provided by Desktop Cube*"

Then I got to choose between: "*Don't enable Desktop Cube*" and "*Disable Desktop Wall*"

Of course I want the cube so I clicked "*Disable Desktop Wall*". Then my window frames are suddenly gone and the cube are still not enabled. When I try to enable it the second time, this shows up:

"*Desktop Cube requires the plugin OpenGL*." With these choises:
"*Don't enable Desktop Cube*" and "*Enable OpenGL*"

I click "*Enable OpenGL*" and ANOTHER pop-up says "*OpenGL requires the plugin Composite*". Anternatives: "*Don't enable OpenGL*" and I click "*Enable Composite*"

Well now (I thought) the Cube is enabled with the cost of my window frames. But it shows that the Cube still wouldn't work and I realized that my keyboard commands stoped working too.

I guess the video card is the one causing the problems

I am using **Gigabyte Radeon HD6950 1024MB OC Windforce** on **Ubuntu 11.04**

---

### Post by Frogs Hair on 2011-09-07
Hi and Welcome

Restart the computer and enter the code from the recovery console found on the session menu that includes the desktop options .```
unity --reset
```

Here is a link to enable the cube , it looks similar to what you have tried  .
[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

