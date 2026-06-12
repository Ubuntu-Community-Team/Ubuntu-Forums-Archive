---
title: "Gutsy / XGL / ATI after a couple hours, high cpu utilization help!"
date: 2007-10-19
forum: Desktop Environments
---

### Post by fizz on 2007-10-19
I upgraded to gutsy from feisty last week and must say the upgrade was seemless and painless for the most part. I started to, however encounter a bothersom problem. It seems as if after a couple hours, XGL starts to just eat cpu cycles. I notice it because the fans in my laptop start going nuts (Macbook pro ati). When this occurs, wobbly windows become more like sticky windows and its like watching playdough morph or something. I usually have to ctrl-alt-backspace to restart x and it goes away for a while. Today I had to actually reboot.

Im running Gutsy with the compiz from gutsy (after i upgraded i apt-get remove --purge compiz-fusion* and then reinstalled)

Im also running avant-window-navigator (compiled from bzr myself) with the system mon applet (this is how i watch the cpu when it starts to happen)

Any clues or insights to this? I think this is the "only" problem i have with gutsy right now.

Thanks in advance.

---

### Post by nw_raptor on 2007-10-21
A friend is experiencing the same problem with his Gutsy + ATI + XGL laptop. So far I haven't found any solution to this, other than going back to X.org. Damn, I can't wait for ATI to release the AIGLX capable drivers...

---

### Post by damir_1105 on 2007-10-21
i had same problem with my radeon 9200SE and Xgl. Lastnight i solved problem.
try this:

to disable Xgl:
```
mkdir ~/.config/xserver-xgl
```
```
touch ~/.config/xserver-xgl/disable
```

i set this options in /etc/X11/xorg.conf for Section "Device"
```

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "8"
        Option          "BusType"       "AGP"
        Option          "EnablePageFlip"        "true"
        Option          "AccelMethod"   "XAA"
        Option          "AccelDFS"      "true"
        Option          "DRI"           "true"
EndSection
```

now compiz work fine.

---

### Post by nw_raptor on 2007-10-21
> **damir_1105 said:**
> i had same problem with my radeon 9200SE and Xgl. Lastnight i solved problem.
try this:

to disable Xgl:
```
mkdir ~/.config/xserver-xgl
```
```
touch ~/.config/xserver-xgl/disable
```

i set this options in /etc/X11/xorg.conf for Section "Device"
```

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"       "8"
        Option          "BusType"       "AGP"
        Option          "EnablePageFlip"        "true"
        Option          "AccelMethod"   "XAA"
        Option          "AccelDFS"      "true"
        Option          "DRI"           "true"
EndSection
```

now compiz work fine.

In other words you dumped Xgl and switched back to the 'ati' driver. That's great, but why did you go with Xgl in the first place, since your card has no trouble with AIGLX?

I only go with Xgl when AIGLX is no go. With that said, the above solution is no fix for those who need Xgl...

---

### Post by damir_1105 on 2007-10-21
i agree, but i saw many people who had this problem with radeon below 9500. On my radeon 9200 i don't need Xgl session because work fine with ati driver. When Xgl is activated cpu usage is 100%, compiz running but direct rendering is off and sometime X crash on loading GNOME.

> That's great, but why did you go with Xgl in the first place, since your card has no trouble with AIGLX?

I upgrade from feisty to gutsy and after that Xgl is default option.

---

### Post by fizz on 2007-10-22
Good to see I'm not alone on this issue..

---

### Post by fizz on 2007-10-22
was just able to reproduce this 3 times in a row!

Try to resize your window from the side (not a corner).. Thats when it starts to go apeshit.. Not sure why the window turns blue during a resize, but im gonna play with that compiz setting if i cant find it. I noticed when using a scrollbar because i accidently clicked the border..

---

### Post by say2sky on 2007-10-23
I have Gutsy /no XGL / ATI. When I run both mplayer and FF for more than one hour, cpu usage usually reach 100%.  And after closing and rerun mplayer or FF, the CPU mediately go back to 100%. Now it seems only reboot system can let CPU  run again in normal usage.

Is there any application can force the system into initial state just as reboot?

---

### Post by fizz on 2007-10-23
Since disabling resize in compiz, I havent had the problem occur again.. just thought I'd share..

---

### Post by nw_raptor on 2007-10-26
after installing ati's aiglx-enabled fglrx driver everything seems to be okay now. since we reinstalled gutsy i'll note this however:

we installed gutsy from a beta cd. it would boot into live and install *with* desktop effects working (yes, with aiglx on open source ati driver). when i downloaded the updates to bring it to gutsy final, the desktop effects no longer worked, and the card was blacklisted. skipping checks didnt do much either, so i am rather puzzled with this one.

fortunately the timing was good and we went with the fresh aiglx-enabled ati driver and now everything works nicely and most of all, the aiglx way...

---

### Post by ba5e on 2007-11-11
Im having this problem too, its really annoying!! will try x restart & test further. is there a bug for XGL about this?

---

### Post by rooijan on 2007-12-28
I have similar problems but using Nvidia drivers.  Compiz.real start running at really high cpu utilization until I disable and re-enable desktop effects.  Sometimes Epiphany, Rhythmbox or Firefox will crash and everything comes back to normal automatically.  

I also do have the resize effect enabled currently.  I will disable that effect and report back what happened to me.  I have GLX enabled in xorg.conf.

---

### Post by rooijan on 2008-01-02
Update:

I have not had the same lockups since I disabled the resize effect in compiz.  I can't currently resize my windows however :)

---

### Post by linuxer101 on 2008-01-02
i see this similar trend of peoples who machines work fine in feisty who upgrade or install feisty and encounter problems, from small to very big problems. quality control compatibility and testing needs to be looked at.


btw alot of people will say its the compiz in gutsy. but that is not true. compiz works fine in pclinuxos 2007. it has to do with the gutsy distro itself.

---

### Post by ph@3drus on 2008-01-15
<quote>I have not had the same lockups since I disabled the resize effect in compiz. I can't currently resize my windows however</quote>

<quote>Since disabling resize in compiz, I havent had the problem occur again.. just thought I'd share..</quote>

I had the exact same problem (Gutsy, ATI Radeon X800XL, fglx driver and compiz fusion). 

I was able to reproduce the problem consistently by resizing a window. While playing around with the resize options (Advanced desktop effects|Uncategorized|Resize Window), I changed the resize effect from 'rectangle' to 'standard'. Since then, I've had no problems with the CPU utilization spiking upon a resize. Hope this helps some others who may have this same problem.

---

### Post by Mum_Chamber on 2008-01-19
fyi, a similar issue happened to me, and solved by removing screenlets

---

