---
title: "Ubuntu 8.04 Studio with Dell XPS m1530"
date: 2008-05-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by E_S p on 2008-05-11
Hi everyone, 
 
i just had an XPS M1530. I have install Ubuntu 8.04 and i am very new to this environment. I am in dual boot with vista and i keep having ](*,) problems with:

wifi (he don't see it)
touch pad (acting weird)
webcam (don't work at all)
eject button (don't work)
Ubuntu Studio did not install properly
Most important for me, the JACK control don't want to work in Realtime with my sound card

I did not yet found infos on this forum about those problems. If someone can help me figure out a way to help me work properly with the studio environment, i would like it)

thanks in advance,:-({|=

---

### Post by clw3388 on 2008-05-13
I have same box... tried 8.04.. couldn't get touchpad to work at all. I fought it for a week then went back to 7.10.. I would suggest the same... sorry coudnt be of more help.. There seems to be an issue with regarding the graphics driver and your touchpad in the xorg.conf file in the /etc/X11 directory... i couldnt figure it out... course you could always wait for an "update"...

---

### Post by dwarness on 2008-05-14
> **clw3388 said:**
> I have same box... tried 8.04.. couldn't get touchpad to work at all. I fought it for a week then went back to 7.10.. 

There's actually a real simple fix for the touch pad.  If you're familiar at all with how grub works, just add i8042.nomux=1 to each kernel line in /boot/grub/menu.lst

Another way (but not permanent) is when the system is booting and you get the grub menu, hit 'e' on the appropriate system you want to boot up.  Then select the kernel line, and hit 'e' again.  Add i8042.nomux=1 to the end of the line, and then hit 'b' to boot that kernel.

I was a 8.04 has been very good for me and my m1530.  The sound system works much better, everything runs better, AND suspend FINALLY works!

Good luck, hope this helps.

-Dave

---

### Post by clw3388 on 2008-07-09
> **dwarness said:**
> There's actually a real simple fix for the touch pad.  If you're familiar at all with how grub works, just add i8042.nomux=1 to each kernel line in /boot/grub/menu.lst

-Dave

I'll give that a try... I am running 8.04 on my server/workstation downstairs and love it... just couldn't stand having to use an external mouse.. 

Thanks for the tip!! I'll report back my success.

---

### Post by clw3388 on 2008-07-11
Well .. it worked.. :) thx

---

### Post by falcon61102 on 2008-07-11
There are a couple threads in here for getting your wireless to work... if your system is similar to mine and has a Broadcom chip than you may need to do a little work, but it's rather simple once you find the root of the problem... Type the following in your terminal and post the results.
```
sudo lshw -C network
```

---

### Post by falcon61102 on 2008-07-11
Also... Check out this thread which gives you the two steps necessary for the CD Eject button to work:

[http://ubuntuforums.org//showthread.php?t=115499](http://ubuntuforums.org//showthread.php?t=115499)

Another thing, I've heard that installing Cheese through the Add/Remove Programs may help your webcam.  Mine worked right away so I can't confirm, but I read that somewhere in here.

---

### Post by hendrikwout on 2008-08-05
> **E_S p said:**
> 

Ubuntu Studio did not install properly
Most important for me, the JACK control don't want to work in Realtime with my sound card

I did not yet found infos on this forum about those problems. If someone can help me figure out a way to help me work properly with the studio environment, i would like it)

thanks in advance,:-({|=

I've just managed to get realtime and low latency with jack on my dell xps m1530!

Here is my setup:

I disabled all performance/processor features in the bios, including multicore support :( , SpeedStep support and Dynamic ... (forgot) support etc. 

Maybe one of those things doenst have to be turned off.

I'm running ubuntu 8.04 32-bit realtime kernel, and I have realtime capabilities (a single config somewhere had to be edited to get this, forgot which one).

I use qjackctl with:
Frames/Period: 128
Force 16-bit: true
Priority: 60
Sample Rate: 44100
Periods/Buffer: 2
Input Latency: 10
Output Latency: 10

I hope this helps.

---

