---
title: "xorg.conf question"
date: 2006-01-14
forum: General Help
---

### Post by newclique on 2006-01-14
I have successfully compiled and added the latest ATI drivers (built the packages for my kernel) for my 9250 card and started xorg. However, I notice in the xorg.conf file that my driver line is set to: driver="ati". Should it be: driver="fglrx" for OpenGL / glx support?

Thanks.

---

### Post by vruum on 2006-01-14
If you want to use the closed source drivers from ATI, then yes, it should be fglrx, also make sure, that in your xorg.conf all glx and dri lines are uncommented, you can use either 
```
 sudo dpkg-reconfigure xserver-xorg
```
or 
```
 sudo fglrxconfig
``` 
to create a valid xorg.conf.
That said, if you want to tinker, I think the 9250 is one of those cards blessed with open source glx support, you might wanna look into that, as it should give some extra benefits, (eg. better support for stuff like EXA and composite)
I'm not sure how much work, if any, it requires  to get it working,
anyways to check if glx is activated type
```
 glxinfo | grep direct
``` 
it will say either "direct rendering  yes" or "direct rendering no"

---

### Post by newclique on 2006-01-29
I gave up on this card and installed an ATI 8500DV. Still no luck. I have moved to another thread regarding the 8500. I believe the problem to be related to only getting one entry when issuing "cat /proc/mtrr" that reports 512MB RAM. My system only has 256 and the video card another 256, I believe.

---

### Post by newclique on 2006-01-30
For anyone completely frustrated with trying to get all of their hardware to work with Ubuntu, I would urge them to try another distro's live eval CD to see what their results are. I sank probably 50 hours into Ubuntu trying to simply get 3D support with an ATI 9250 and 8500DV to no avail. First boot of a live eval of PCLinuxOS ([http://www.pclinuxos.com/](http://www.pclinuxos.com/)) came up with full glxgears running and fglrxinfo showing my card handling direct rendering.

Heed a warning from someone who gave this distro every opportunity: shop around.

---

