---
title: "3D Windows not working after 8.10 Intrepid Upgrade"
date: 2009-03-28
forum: Desktop Environments
---

### Post by Daddyo-613 on 2009-03-28
**My System: **I am running a nVidia Geforce 8 series on an Intel Quad Core processor and recently upgraded to Ubuntu 8.10 from Hardy but I have lost 3D windows functionality in my Compiz-fusion Settings Manager (CCSM). I am using the standard nVidia driver ver. 177 that is distributed with 8.10 and I am using Gnome 2.24. I have enabled both compiz-fusion-plugins-main and compiz-fusion-plugins-extra.

I have no problem with cube rotation or deformation using the Cube Reflection and Deformation setting in the CCSM.

**The problem:** When I try to enable 3D Windows or change the 3D Window settings they don't work and the box won't stay checked.

Any suggestions would be welcomed.

---

### Post by Daddyo-613 on 2009-03-28
I found a manual solution to my problem...which allows the previously installed 3D effect to function:

1. go to...System>Preferences>CompizConfig Settings Manager>Preferences>Plugin List
2. disable "Automatic Plugin Sorting" by unchecking the box;
3. locate 3d in the "Disabled Plugins List" and move it to the "Enabled Plugins List";
4. re-enable "Automatic Plugin Sorting" by checking the box and you're done.

There is still a problem. It appears that in the 8.10 Intrepid Upgrade the location of the files for this 3D plugin may have been changed. If someone knows where these files are located and how CCSM points to them, I may be able to get CCSM to include the 3d plugin in its Automatic Plugin Sorting.

Cheers.

---

### Post by Daddyo-613 on 2009-03-31
I have been searching for a more permanent solution to my 3D Windows problem but to no avail. If it will help here are some particulars of my system:

CPU:                      Intel Core 2 Duo E6300 1.86GHz(1066MHz) s775
RAM:                      Kingston 1GB 240-pin DDR II 533MHz/PC4200
O/S:                       Ubuntu 8.10 \n \l
Kernel: 2.6.27.11-Generic
Video Card:            Asus GF7300LE w/TurboCache128MB TVOut DVI
Video Driver:          nVidia ver. 177
Settings Manager:   CCSM ver. 0.7.8
Window Manager:    Compiz
Window Decoratior: GTK Window Decorator

I have installed all updates current to today March 31st, 2009. I have switched other CCSM effects on and off and they work fine. The 3D Window effect can still only be activated manually by opening CCSM, going to **Preferences** and disabling **Automatic Plugin Sorting** tab and adding the effect to the list of enabled plugins. Even then this temporary fix is lost on reboot.

I have tried moving the 3d effect up in the loading order but it didn't make any difference. There must be a conflict somewhere but I haven't been able to find it. I been searching threads and Googled a similar search string and the most frequent link that comes up is my previous post. I can't believe that I'm the only one on the planet that has experienced this problem.

Suggestions would be welcomed.

---

### Post by Daddyo-613 on 2009-04-12
Since I didn't get much interest in my problem, I started a new thread using more colourful language. Nothing inappropriate you understand, I just used more folksy language in the heading to try and spark some interest. 

Unfortunately that didn't work either, but the good news is that I did find a permanent solution to my 3D Cube problem on my own. And for those hapless souls who may stumble upon this thread, my answer to my own thread can be found here: 

[http://ubuntuforums.org/showthread.php?t=1123047](http://ubuntuforums.org/showthread.php?t=1123047)

Pretty sad eh! Anyway, if you have a similar problem, maybe what I discovered about conflicts of previous versions might help you figure out your own problem.

TTFN

---

