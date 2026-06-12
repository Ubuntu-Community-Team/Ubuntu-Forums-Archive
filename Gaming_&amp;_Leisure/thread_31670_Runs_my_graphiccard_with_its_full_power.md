---
title: "Runs my graphiccard with its full power?"
date: 2005-05-04
forum: Gaming &amp; Leisure
---

### Post by Gags666 on 2005-05-04
Hi,

i'm the new one. :) This week I found my way to Ubuntu. Before that I primarily used Gentoo. I'm a gamer but I never concerned myself much with 3D-Acceleration and such things under Linux because i've got an original licence for WindowsXP where I used to play my games on. Linux was just my system for everything else but gaming. :) Now I've decided to begin playing some games under Linux (e.g. Unreal Tournament 2004, Doom3, maybe World of WarCraft with Wine) but I'm afraid I don't get the full power of my graphiccard. And that's already the point of my posting. ;)
I installed the nVidia-Drivers for my GeForce 6800 GT described like [here](http://ubuntulinux.org/wiki/BinaryDriverHowto) and modified the xorg.conf described like [here in point 6](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=31). Is this really everything I need or is there more to do to get the full performance out of my graphiccard? Are there more options or something else I need?
glxgears shows me about 10000FPS. Is this ok for my system (AMD Athlon XP 2800+@2187MHz, 1GB RAM, GeForce 6800 GT)?

P.S.: I'm from germany so please be patient with me and my (possibly bad) English. ;)

---

### Post by wasynyt on 2005-05-04
ok.. i dont know why your asking this...
but let me ansver my way..
first mine computer... i have amd 2600+ no overclock & asus geforce  4 mx440 128 mb (yes ive really got that  \\:D/  ) and ive got some 2000 in glxgears.. nah in windows ive played nicely with it anything up to doom3 (800*600)... so i think that the performance youve got is more than enough  :-P

---

### Post by Gags666 on 2005-05-06
In a performance test it doesn't matter if the result is enough but if it's a correct result for this system. You can't say it's enough because there's always a game for which it isn't. :)
My problem lies there that in Windows the driver automatically detects your AGP speed, if you use FastWrite and many more things. With Linux you have to set these options by yourself. I don't say that this is bad thing but I don't know and I can't find out every of these essential options and that's the cause I am afraid of not having the full performance of my graphiccard. I want Ubuntu to be a nearly complete replacement for my Windows but before it can be this for me I need at least the same perfomance like with Windows. I hope you now understand why I'm asking. :) Thanks for your answer.

---

### Post by wasynyt on 2005-05-06
I understand..
but yet in my own opinion linux is easily faster than winxp home..... in any category..
hmm yet for some info on your system can be aquired from powertweak... you can install it from apt-get reposities..
[http://www.linuxhardware.org/features/04/10/12/1725246.shtml](http://www.linuxhardware.org/features/04/10/12/1725246.shtml) performance in doom3
[http://www.anandtech.com/showdoc.aspx?i=2229&p=1](http://www.anandtech.com/showdoc.aspx?i=2229&p=1) alot of different graphic cards compared..
i hope that those links prove helpful

---

### Post by DutchLau on 2005-05-06
10,000 FPS in glxgears?? Holy crap! That's amazing!  :-| 

I was happy with my 3-4000 FPS, but that's just crazy. You should also give Americas Army a try. It's a free First Person Shooter which is developed by the U.S. military and it's great! It's for both Linux and windoze so you have MANY MANY people that play this online. Nice graphics and gameplay, but I warn you, it's VERY addictive. ([www.americasarmy.com/downloads](www.americasarmy.com/downloads))

Unt success!  :) 

DutchLau

---

### Post by Gags666 on 2005-05-09
[quote="wasynyt"]I understand..
but yet in my own opinion linux is easily faster than winxp home..... in any category..[/quote]
I agree with you but I my opinion the game performance needs some tweaking - at least in my case. :)

[quote="wasynyt"]hmm yet for some info on your system can be aquired from powertweak... you can install it from apt-get reposities..[/quote]
I'll try that.

[quote="wasynyt"]http://www.linuxhardware.org/featur...2/1725246.shtml performance in doom3
[http://www.anandtech.com/showdoc.aspx?i=2229&p=1](http://www.anandtech.com/showdoc.aspx?i=2229&p=1) alot of different graphic cards compared..
i hope that those links prove helpful[/quote]
Thanks, the links helped me a lot.

[quote="DutchLau"]10,000 FPS in glxgears?? Holy crap! That's amazing! :neutral:[/quote]
*g* Thanks. :)

[quote="DutchLau"]I was happy with my 3-4000 FPS, but that's just crazy. You should also give Americas Army a try. It's a free First Person Shooter which is developed by the U.S. military and it's great! It's for both Linux and windoze so you have MANY MANY people that play this online. Nice graphics and gameplay, but I warn you, it's VERY addictive. ([www.americasarmy.com/downloads](www.americasarmy.com/downloads))

Unt success! :)[/quote]
I know this game but I never played it. Maybe I really should give the Linux version a try. :)

---

### Post by wasynyt on 2005-05-09
in linux to gain biggest performance boost (in my knowledge) is to increase memory and i know people who has 1gb+ memory in their machines.... but yet if you want a truly gaming monster dont use kde/gnome but instead some extremly light windowing system... shutdown every other proceses than those which system needs for runing and firewall if your connected to internet.. 
use some more powerful filesystem as reiserfs..

i clad that my links proved useful... yet heres more
[http://www.tweak3d.net/tweak/geforce/](http://www.tweak3d.net/tweak/geforce/)    graphicards tweaking.. bios settings.. mainly windows though
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54)  doom3 tweaks (its one the most graphic intensive apps...)
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54)  some more about bios
[http://intmainvoid.nl/?x%20config%20tweaks](http://intmainvoid.nl/?x%20config%20tweaks)   about Xorg tweaks

---

### Post by DutchLau on 2005-05-09
[QUOTE=wasynyt]in linux to gain biggest performance boost (in my knowledge) is to increase memory and i know people who has 1gb+ memory in their machines.... [/QUOTE]

I don't entirely agree with that. With very limited memory I can run many many games very well (not the computer in my sig). Linux overall just gives much better performance than windoze.  :razz:

---

### Post by wasynyt on 2005-05-10
cannot agree more..
but yet when we are trying to reach performance beyond excelent in most intensive apps the ammount of money (quality of parts) rises alot.. 

my comp:
amd xp 2600+
epox 8rda6+ pro mobo
asus geforce 4 mx 440 128 mb (64 bit bandwith)
768 meg memory
200 gig hardrive (udma 133)

so this either isnt some monster... but in my list of what i need:
better graphic card, perhaps geforce 6600 (standart) 256 meg memory
more memory (im thinking of doubling what i have now)
and of course when my space runs out new hardrives (i have 6 sata slots free :) )

---

### Post by equilibrium on 2005-05-12
10000fps seems ok for your spec :)

I am getting 11749fps

CPU: p4 2.8c @ 3.5Ghz
GPU: nvidia 6800le 16pipes
RAM: 1gb PC3200

---

### Post by DutchLau on 2005-05-12
[QUOTE=equilibrium]
CPU: p4 2.8c @ 3.5Ghz
 PC3200[/QUOTE]

Nice overclock!  :grin:  The best I ever achieved was on my AMD Xp 1700+ (standard @ 1496 Mhz) and I overclocked it to 2075 Mhz! (166 FSB 12.5 Multiplier) Pretty nice !  :razz: (1/3 OC)

Keep on OCing!

DutchLau

---

### Post by Gags666 on 2005-05-20
I'm back with 12.500FPS in glxgears. :) Found the failure - the AGP functionality was deactivated. I chose NVAGP in the xorg.conf but I didn't know that I have to blacklist the modules for AGPGART first to get NVAGP working so I had no AGP functionality at all. After fixing this everything from Doom3 to Unreal Tournament 2004 runs fine.

---

### Post by mrbass on 2005-05-23
@Gags666

Can you please detail what exactly you did?  I can run glxgears and get 3200fps but it uses 100% of my CPU for glxgears.  That's why my games and openGL screensavers keep crashing.

---

### Post by Gags666 on 2005-05-23
Sure! :) I assume that your drivers are installed correctly so I just post the modifications I've done.

Here's the section "Device" of my xorg.conf:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800 GT]"
        Driver          "nvidia"
        Option          "NoLogo"                "on"
        Option          "NvAgp"                 "1"
        Option          "EnablePageFlip"        "on"
        Option          "RenderAccel"           "true"
        BusID           "PCI:2:0:0"
EndSection
```
That's the important part of my /etc/hotplug/blacklist:
```
agpgart
nvidia_agp
```
And last but not least the important part of my /etc/modules:
```
nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```

---

### Post by equilibrium on 2005-05-23
I thought I'd do a little research into which driver is better on my system :) just out of curiosity. So I tried both NVIDIA and AGPGART.

```
**NVIDIA**
$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
$ glxgears
57979 frames in 5.0 seconds = 11595.800 FPS
58642 frames in 5.0 seconds = 11728.400 FPS
58655 frames in 5.0 seconds = 11731.000 FPS
58813 frames in 5.0 seconds = 11762.600 FPS
58891 frames in 5.0 seconds = 11778.200 FPS
```
```
**AGPGART**
$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled
$ glxgears
58569 frames in 5.0 seconds = 11713.800 FPS
58690 frames in 5.0 seconds = 11738.000 FPS
58743 frames in 5.0 seconds = 11748.600 FPS
58805 frames in 5.0 seconds = 11761.000 FPS
```
Interesting :) both seem to be the same performance.

---

### Post by mrbass on 2005-05-24
Well I don't know but it still uses 100% CPU when I run glxgears.  I blacklisted the agppart.  What's weird is I did have it working previously.  Maybe vmware screwed it up.  No idea.

---

### Post by Gags666 on 2005-05-24
[quote=equilibrium]Interesting :) both seem to be the same performance.[/quote]
Seems the same on my system, too. Maybe a little bit better for nVidia but not really appreciable.

But I've got a problem again: Yesterday I ran *apt-get dist-upgrade* and after that my performance sunk down to 10.000FPS but AGP and everything was like before so I didn't know what to do and reinstalled the nvidia-glx drivers. After that it went up to ~11.700FPS but still not to the ~12.500FPS from the days before.

---

