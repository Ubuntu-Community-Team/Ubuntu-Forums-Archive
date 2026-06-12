---
title: "Trying to install graphics drivers for Inspiron 1545"
date: 2009-11-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by v1nsai on 2009-11-24
I've been having some trouble getting my graphics drivers installed.  Everything is working like it should I have compiz enabled and transparency on some of my windows like I like and all, but cairo-dock has the black box around it, which indicates the graphics driver isn't installed properly.

lshw -C display confirmed it:
```
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation                                      
       physical id: 2                                                 
       bus info: pci@0000:00:02.0                                     
       version: 07                                                    
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

I've tried installing 'xserver-xorg-video-intel' but apt says its the newest version already.  I went to Intel's website to get the drivers myself and after running in circles for 15 minutes and registering, no matter what system I tell it I'm running, it only lets me download a Windows .exe for the drivers -_-  .  Not very happy with Intel right now.

Can anyone suggest how to get these drivers installed?  I can use cairo-dock without the effects but I don't like not having these drivers installed...

---

### Post by mikewhatever on 2009-11-25
I think it would be logical to suggest that if all else but the cairo dock works well, the problem is with the cairo dock and not with something else. It should also be safe to assume, that if compiz works, there is no problem with the graphics driver installation.
That out of the way, you got me somewhat confused about what exactly you were trying to do. If you had a driver to install and just needed help with that, why did you try getting more drivers from Intel? If you tried getting drivers from Intel because you didn't have any to install, what were the drivers you were talking about in the opening sentence?

---

### Post by v1nsai on 2009-11-25
Well it sounds confusing when you put it like that :P

It may just be a cairo-dock problem, but as you can see the display driver (looks like I cut the top off, but that's just the VGA adapter) isn't claimed, which means there isn't a driver loaded (right?).

I am able to run compiz/emerald effects just fine, but I use cairo a lot and I'd really like to get it to look right.  Since the display is unclaimed, I think that's probably the problem.  I'm on a 9.04 Wubi install (not my laptop) if that makes a difference at all....

Since the display wasn't claimed and none of the packages from the repos were doing me any good, I went to intel to try to find a driver, ended up going around in circles, wasting my time registering with them and then getting handed a .exe for all my troubles -_-  Intel asked me to fill out a survey about them so I got to vent a little but it didn't solve my problem unfortunately.

---

### Post by bobcollard on 2009-11-25
> **v1nsai said:**
> Well it sounds confusing when you put it like that :P

It may just be a cairo-dock problem, but as you can see the display driver (looks like I cut the top off, but that's just the VGA adapter) isn't claimed, which means there isn't a driver loaded (right?).

I am able to run compiz/emerald effects just fine, but I use cairo a lot and I'd really like to get it to look right.  Since the display is unclaimed, I think that's probably the problem.  I'm on a 9.04 Wubi install (not my laptop) if that makes a difference at all....

Since the display wasn't claimed and none of the packages from the repos were doing me any good, I went to intel to try to find a driver, ended up going around in circles, wasting my time registering with them and then getting handed a .exe for all my troubles -_-  Intel asked me to fill out a survey about them so I got to vent a little but it didn't solve my problem unfortunately.
Same computer, same drivers, see my signature.  If you have no driver you won't see anything on that screen.  Here is an example of one of my screenshots:
Addendum, here is my  output like yours above, a little different:
*-display:0
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff

---

### Post by v1nsai on 2009-12-14
I just bought a Dell Studio 15 and I'm having the same problem on it too (same graphics card).

I've read [here]("http://ubuntuforums.org/showthread.php?t=1193473&highlight=display+unclaimed") that Intel is updating their stuff and it just isn't finished atm, but since I'm already running 9.10 I don't want to have to roll back to a previous version/kernel.  Can I download the correct module and load it myself?  I've been googling but I can't find a graphics module for this card.  I've added the PPA [here]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") but the 'xserver-xorg-intel' driver isn't updated and even after reboot my display is still unclaimed.

Can someone point me where to find this module, or suggest something else?  My FPS is terrible right now and I'm pretty sure this is the cause :-/

---

