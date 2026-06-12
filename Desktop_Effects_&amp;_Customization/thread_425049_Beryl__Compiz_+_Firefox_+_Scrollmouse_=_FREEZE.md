---
title: "Beryl / Compiz + Firefox + Scrollmouse = FREEZE"
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by KrazyPenguin on 2007-04-27
Still on the topic of Feisty crashing and completely freezing.

By adding the option to the kernel at boot:  pci=assign-busses I haven't had a freeze with compiz/beryl when they are turned OFF.

But when they are turned ON I get random FREEZES.  :shock: 

This has happened the last 3 (three) times X 
I have used Freezy, opps, I mean Feisty.

And I'm going tell you how I reproduced the freeze:

1) Make sure Beryl or Compiz is running so the 3d effects and cube is ON.
2) Connect to internet wirelessly
3) Open Firefox
4) Use a wireless microsoft scroll mouse, scroll the mouse rapidly and FREEZE.
5) Do a hard boot.

Maybe my mouse has a virus??
:confused:

Anybody else experince this.
Basiclly, the next time you freeze look , stop and look at where your fingers are.

8-[

---

### Post by kpettersson on 2007-04-28
I can confirm that I experienced the "Beryl / Compiz + Firefox + Scrollmouse = FREEZE" on Feisty in combination with my DELL PRECISION M90. However I also get freezes which appear like this:
1. two or three quick blinks on the monitor
2. wifi-network quits (need to reboot to get it back)
3. system eventually freezes.

Right before the system freezes I get kernel messages on my consoles which looks like this:
```
Apr 29 00:38:16 Adventure kernel: [ 7687.660000] Uhhuh. NMI received for unknown reason a1 on CPU 0.
Apr 29 00:38:16 Adventure kernel: [ 7687.660000] You have some hardware problem, likely on the PCI bus.
Apr 29 00:38:16 Adventure kernel: [ 7687.660000] Dazed and confused, but trying to continue
Apr 29 01:07:28 Adventure kernel: [ 9438.840000] NVRM: Xid (0001:00): 6, PE0000 0374 00000000 001cbdf8 00ffffff 00000001
Apr 29 01:07:28 Adventure kernel: [ 9438.856000] NVRM: Xid (0001:00): 30,  L1 -> L0

```

I haven't tried your pci=assign-busses approach yet. I let you know if it makes a difference.

---

### Post by dagrump on 2007-04-29
It's the mouse, I find if I don't touch the scroll wheel while pages are loading no freeze. I just can't give up my wireless keyboard & mouse. Here I said I was going quit messing w/ this machine, & fired her up first thing, & start looking for the fix. But if I don't touch the scroll wheel during page refreshes & loads it does not seem to lock.

---

### Post by Tarsonis on 2007-06-04
I've been struggling with this problem for some time now (basically since Feisty came out of pre-release).  I have been able to duplicate the Beryl+FF+scrollmouse=freeze, but I'm not entirely sure the mouse wheel is at fault.
As long as I scroll slowly and smoothly (wheel, arrow keys, dragging the slider.. etc) , everything is fine, even if the page has not yet loaded.  However, if I rapidly scroll the page, either by flicking the wheel *OR* rapidly dragging the slider, instant freeze.  aka, it appears the freeze has to do with a rapid re-rendering of the page rather than the method of input.  All this was done with Beryl disabled.
Could it have anything to do with linux ATI drivers?

---

