---
title: "Compiz not rendering"
date: 2010-05-01
forum: Desktop Environments
---

### Post by imiunleashed on 2010-05-01
Hey guys - i am very new to Ubuntu, but i had 9.10 before and everything worked fine. i uninstalled 9.10 and installed 10.04 but i compiz does not work well. I see this when i run compiz check :
> Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


I have got an ATI 4530 card...Please help me..:)

---

### Post by Claus7 on 2010-05-01
Hello,

these things:
aiglx, xgl e.t.c. are usually found in xorg.conf file.

Does your graphical environment (without compiz) works ok? Have you enabled the right driver for your graphics card?

Maybe, you have to manually edit this file as root in terminal mode with the command X -configure...

This is what I can think...
Regards!

---

### Post by imiunleashed on 2010-05-01
Ubuntu itself found my VGA and itself installed the drivers for me.
This is what my Xorg.conf file contains:
> Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Device"
        Identifier  "Default Device"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        DefaultDepth     24


The desktop works ok in the graphical environment but compiz does not - water effects + some other do not work :(

---

### Post by sendblink23 on 2010-05-01
another minor question..

Do you have visuals set to Extra?
System > Preferences > Appearances 
Visual Effects > Extra

---

### Post by imiunleashed on 2010-05-01
This is exactly what happens :

1. I set the visual effects to extra
2. I go to compiz settings manager and enable desktop cube and rotate cube.
3. Both the cube and rotate cube work well.
4. I enable water effect - i try it out my whole screen goes dark so i disable it.
5.Again i go to visual effects but nothing is selected ( yeah the extra i choose before is not selected, infact none of the 3 options are selected)
6. Again i click on extra and select it.
7. Desktop cube and rotate cube do not work.

8. Then i try number 2 again and the cycle continues :(

---

### Post by sendblink23 on 2010-05-01
so rebooting... and only using the cube effect  and not choosing the water ripple(or anything other that gives u black screen)....  I mean does the cube keep working if you don't choose any other effects & continue using the computer?

If its fine like that....  well I wouldn't add any other effects then

another idea could be the video drivers maybe they don't work nice under 10.04  compared to what you had on your previous version...  but this is me assuming here.. I have an ati 4650 on my desktop but don't have linux installed on it.

---

### Post by imiunleashed on 2010-05-01
ya the cube does work if i do not mess around with the other settings. But i too want the other effects too :)
If all the other effects worked with Karmic, why cant they work here? :@
Please help me on this, i took the initiative to be Microsoft-free but these problems make me think twice :(

---

### Post by sendblink23 on 2010-05-01
> **imiunleashed said:**
> ya the cube does work if i do not mess around with the other settings. But i too want the other effects too :)
If all the other effects worked with Karmic, why cant they work here? :@
Please help me on this, i took the initiative to be Microsoft-free but these problems make me think twice :(

I hope a fix does come(not having to reinstall)...  but anyways... here is another thought

Upgrading to latest builds versions is not necessary you can stay happy with previous version, many users prefer to stay with a way older version since it works better according to their computer system.

Example some users prefer to use Windows XP & not upgrading to Windows 7... because for them their system works better on XP...  do you understand what I mean... same goes to users who still use Microsoft Office 2003  instead of upgrading to 2007 or newly now 2010 version... all because they liked it better how it worked on 2003 version.

You are not obligated to upgrade unless there is something very specific important that you are in need to upgrade...  having it compulsory only working under the latest build version of an OS.

So if on waiting 1 or 2 full weeks with no available fixes for your Issue...  I would downgrade to an older version instead of 10.04.

---

### Post by imiunleashed on 2010-05-01
Ya man, thank you for your help and thoughts, ill look for about 2 weeks, hopefully i guess i would be able to get a fix :)
But if you find any info on how to sort this out please let me know :)

---

### Post by Claus7 on 2010-05-01
Hello,

so first things first: I do not and never had an ATI graphics card, so what I give are speculations on the error you report above combined with the xorg.conf file you provide.

If you follow my options, you might come to a surprise with your environment, which means that you have to use terminal in order to put it back as it is now.

Specul1) The drivers are not ok...
Sol1) You have to wait and see...

Specul2) Xorg.conf file needs tampering.
Sol2) go to /etc/X11/xorg.conf and as root take a back up of this file. In case you do not, you might not be able to return easily to your current state. Now go open with your favourite text editor the xorg.conf file and add the following lines (in the end):

> Section "DRI"
Mode 0666
EndSection

Section "Extensions"
    Option         "Composite" "on"
EndSection

In section Device, just before the End Section line, add the:
Option "RenderAccel" "true"

and finally in section screen, after the Default Depth line, add the:
>      Option         "AddARGBGLXVisuals" "true"

You will add these one at a time. You will have every time to reboot in order for these to take effect. Go to compiz settings and do what you did before. Do the problems persist? Then add the next option I provide to you and see in the end if you will fix your problem.

Normally the info I provide will not do any harm on your graphical environment, yet you never now.

If all else fails, reconstruct xorg.conf.

If this does not do the trick as well, restore back the backup you have taken in the first place.

Regards!

---

### Post by imiunleashed on 2010-05-03
Hey Claus7 thanks for the help, but unfortunately it did not help. So i reinstalled Ubuntu and now everything works fine :D
THanks for your help ppl :D

---

### Post by Claus7 on 2010-05-04
Hello,

glad if I can provide some help and more glad since you were able to solve your problem.

Only one query: did you see any difference in xorg.conf for example, while you made a fresh install? If there is one and you spot it, then some people might benefit from this information.

Happy compiz-ing,
Regards!

---

