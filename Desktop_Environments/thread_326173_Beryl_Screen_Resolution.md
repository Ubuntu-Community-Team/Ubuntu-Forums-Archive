---
title: "Beryl Screen Resolution"
date: 2006-12-27
forum: Desktop Environments
---

### Post by Auric_Falc0n on 2006-12-27
Hello All!

I just installed Beryl/Emerald 0.1.1 onto Ubuntu Edgy following the how-to for ATI cards, and it works great. The only caveat to that is that if the screen resolution is higher than 1024x768 there is a bar on the right side of the screen that is the color of the skydome that covers the desktop. The desktop also turns white. Any ideas on how to fix this, or is it a limitation of Beryl?

---

### Post by webstar on 2006-12-28
i have the same problem.
i've tried it with XGL, which works just fine up to 1024x768. if i set a higher res, XGL won't find any display.
...and i've tried it with AIGLX, which also works fine up to 1024x768. at a higher res the screen splits in a left part, where most of the windows get screwed up and turn white ... and a right part, which repeats everything u move over it (like ms windows does if the desktop crashes). i've tried modifying my xorg.conf a thousand times now, but it didn't help. 

i suppose i have not enough video ram (32MB) on my radeon 7500. could this be the reason?
my 3d environment works fine, i get 1250fps in glxgears. 

any ideas?

---

### Post by Auric_Falc0n on 2006-12-28
I've got 32mb on my Radeon 7000 VE - I'm thinking that is probably the culprit.

---

### Post by danboarder on 2007-01-07
> **Auric_Falc0n said:**
> Hello All!

I just installed Beryl/Emerald 0.1.1 onto Ubuntu Edgy following the how-to for ATI cards, and it works great. The only caveat to that is that if the screen resolution is higher than 1024x768 there is a bar on the right side of the screen that is the color of the skydome that covers the desktop. The desktop also turns white. Any ideas on how to fix this, or is it a limitation of Beryl?

Exactly the same problem here!   I'm running a Sony 1.6ghz Viao with ATI Radeon Mobility 7500. Beryl works perfectly at 1024x768 - very smooth. 

But at the native screen res of 1600x1200 it works only on the left two-thirds of the screen, and the right is white (as mentioned above). No wallpaper shows - it's also all white. Apps will display, but they are not redrawn in the right 1/3 area - it creates a cascade of artwork in that area (kind of looks cool, but not usable :)   ... The cube does work fine, but every side has the same problem - only the left two-thirds of the screen redraws correctly.  Alt-tabbing etc works fine.

Is there any more info that might help figure this out?

---

### Post by danboarder on 2007-01-14
[QUOTE=
Is there any more info that might help figure this out?[/QUOTE]

Anyone?  I know the ATI Radeon Mobility 7500 was a popular card in laptops for several years (2002-2004 or so).  I would love to be able to use Beryl at the native 1600x1200 on this screen. 

Thanks for any ideas or direction in solving this.

---

### Post by danboarder on 2007-01-14
UPDATE - Problem Solved!  

The advice in the following thread fixed it: [http://ubuntuforums.org/showthread.php?p=2010643#post2010643](http://ubuntuforums.org/showthread.php?p=2010643#post2010643)

I added the following line to my xorg.conf, under the Device section:

   Option      "AGPSize" "32"


Also, I followed the advice here: [http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)

Hope that helps some folks!  My system now running Ubuntu, Gnome, Beryl, and Emerald themes smoothly:

Sony GRX 650 , 1.6ghz, ATI Radeon Mobility R7 7500 with 32mb video ram, 512mb system ram, 60gb HD.

If anyone needs help getting a similar system working, let me know and I can post my xorg.conf or other files as needed. Thanks to everyone on these boards for your help!

---

### Post by manutdfan2850 on 2007-01-19
edit: NVM i got it :)

---

### Post by elempoimen on 2007-01-21
> **danboarder said:**
> UPDATE - Problem Solved!  

The advice in the following thread fixed it: [http://ubuntuforums.org/showthread.php?p=2010643#post2010643](http://ubuntuforums.org/showthread.php?p=2010643#post2010643)

I added the following line to my xorg.conf, under the Device section:

   Option      "AGPSize" "32"


Also, I followed the advice here: [http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)

Hope that helps some folks!  My system now running Ubuntu, Gnome, Beryl, and Emerald themes smoothly:

Sony GRX 650 , 1.6ghz, ATI Radeon Mobility R7 7500 with 32mb video ram, 512mb system ram, 60gb HD.

If anyone needs help getting a similar system working, let me know and I can post my xorg.conf or other files as needed. Thanks to everyone on these boards for your help!

Would you? I'd love to look at your xorg.conf and your drirc. Thanks!

---

### Post by yioan on 2007-01-26
Just wanted to say Thank you. After I have set the AGPSize option everything works fine.

---

### Post by hamptone on 2007-06-16
> **danboarder said:**
> UPDATE - Problem Solved!  

The advice in the following thread fixed it: [http://ubuntuforums.org/showthread.php?p=2010643#post2010643](http://ubuntuforums.org/showthread.php?p=2010643#post2010643)

I added the following line to my xorg.conf, under the Device section:

   Option      "AGPSize" "32"


Also, I followed the advice here: [http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)

Hope that helps some folks!  My system now running Ubuntu, Gnome, Beryl, and Emerald themes smoothly:

Sony GRX 650 , 1.6ghz, ATI Radeon Mobility R7 7500 with 32mb video ram, 512mb system ram, 60gb HD.

If anyone needs help getting a similar system working, let me know and I can post my xorg.conf or other files as needed. Thanks to everyone on these boards for your help!

I would also like to see your xorg. Also I don't understand the advice > 

Also, I followed the advice here: [http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500) 
I have nothing called drirc on my computer and definataly not in my /etc/ folder

---

