---
title: "Problems with Wolfenstein Enemy-territory"
date: 2006-06-05
forum: Gaming &amp; Leisure
---

### Post by Sagotis on 2006-06-05
Hello All!

I am having major issues with Et under dapper that I did not have while using breezy. It seems that when I go in game I will see small tares on the sides of objects in game then full blown smearing of the screen if I move around in game.

I am using the same graphics card in dapper that I was using in breezy, which is a Geforce4 Ti 4800se (I also have the same 1 gig memory and 2.4ghz p4). I never once experienced this problem under breezy (or windows for that matter) and to test this I reinstalled breezy as well as the Nvidia drives and ran Et - all problems went away.

I then reinstalled dapper and on this fresh install the latest Nvidia drives, using Alberto Milone's scrips ([http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)) , but that did not resolve the issue.

At this point I am not real sure how to tackle this problem, I am still a noob to linux, but I was wondering if the issue has somethign to do with openGL based games not having full 3D acceleration not truned on by defult in dapper? If that is the case would this, [http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636), help solve the issue even though I do not have compiz installed?

If anyone could help me I would really appreciate it!

Thanks, 

Sagotis

---

### Post by init2null on 2006-06-09
I've had the same problem. While it's annoying, the simple work-around is to turn on Options-->System-->Sync Every Frame.
Hope this helps,
Wesley

---

### Post by Sagotis on 2006-06-10
init2null,

Thank you, that solved the problem. Btw I tried the fix above, which im guessing disabled gl? Then installed brezzy again - looked at the xconfig file (noted anything i didnt see it the dapper one). Installed dapper chaned the xconfig file - only to arrive here ;)

Thanks,

from the nub known as Sagotis

---

### Post by init2null on 2006-06-11
[QUOTE=Sagotis]Btw I tried the fix above, which im guessing disabled gl?[/QUOTE]
I'm not sure what you mean. Are you asking about "Sync Every Frame"? I'm not sure what it does, but I believe it synchronizes the graphics framerate with the monitor's update frequency. It reduces the framerate slightly but it also reduces visible tearing. I guess the work-around avoids a bug in the kernel, X11, or the nvidia driver. I play often, and I'm not really having problems with this work-around.

[QUOTE=Sagotis]
Then installed brezzy again - looked at the xconfig file (noted anything i didnt see it the dapper one). Installed dapper chaned the xconfig file - only to arrive here ;)
[/QUOTE]
Great detective work! I would have bought another gfx card before sitting through 3 installs! ;)
Arrive where? It's working now, right?

BTW, I play on Last Evolution's server 70.84.176.165:27961. I wouldn't mind seeing another Ubuntu user on the server!

Wesley

---

