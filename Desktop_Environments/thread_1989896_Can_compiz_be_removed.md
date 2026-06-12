---
title: "Can compiz be removed"
date: 2012-05-29
forum: Desktop Environments
---

### Post by jmfal on 2012-05-29
I trying out 12.04, read about >compiz-check< in another thread, installed and ran the program.

 Results said that my video driver is not compatible with compiz/unity.  I've had a couple of freeze-ups and log said something about colord, and compiz before running the test.

 I know that I can use the default ubuntu/unity desktop, or gnome, etc., but I think that compiz is causing problems no matter what desktop I use, mainly being sluggish, causing minor freezing.  

Compiz-check said that one problem was that the compiz-daemon is being used by another compositer and asked to shut it down, which I did---resulting in a black screen. 

Rebooted to ubuntu desktop but having some problems, so I can't post any logs or test results. I'm on another pc right now.

---

### Post by zombifier25 on 2012-05-29
If Compiz is causing problems, you can log in the Unity 2D desktop instead.

---

### Post by jmfal on 2012-05-29
I was using 2D when the freezing happened.

---

### Post by zombifier25 on 2012-05-29
Unity 2D does NOT use Compiz - it uses Metacity instead. If you are not trying to run Compiz with Unity 2D, then I doubt the problem lies in Compiz.
Put this command in the terminal and post the result:
```
ps ax | grep compiz
```

---

### Post by jmfal on 2012-05-29
Here is the result of::  ps ax | grep compiz

2551 pts/0    S+     0:00 grep --color=auto [COLOR=Red]compiz[/COLOR]

---

### Post by 3Miro on 2012-05-29
Compiz is NOT running on your system, whatever problems you might be having have nothing to do with compiz. 

My guess is that everything comes from your video driver. Can you post info for your video card and video driver.

---

### Post by jmfal on 2012-05-29
>     
**Re: Can compiz be removed**
 		Compiz is NOT running on your system, whatever problems you might be having have nothing to do with compiz. 

My guess is that everything comes from your video driver. Can you post info for your video card and video driver. 	  

I ran-

```
 xxx@xxxx-xxxxx:~$ lspci -v 
```

and the output --

```
 02:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 240] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8335
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at df000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dc000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at def80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb
  
```

In the Nvidia xserver settings: driver version  295.40

I appreciate the help, need to get this fixed

Thanks

---

### Post by jmfal on 2012-05-29
This is the /etc/x11/xorg.conf file:

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

This is the whole file, nothing for mouse, keyboard, display.

---

### Post by jmfal on 2012-05-29
Solved

---

