---
title: "Performance issues with Intel video drivers"
date: 2009-03-27
forum: General Help
---

### Post by IanVonSpeedfreak on 2009-03-27
I'm having trouble with the intel graphics drivers again - same problems.  First off, things are really slow - I can hardly run more than one program at a time.  Second, when I logout, my screen resolution changes (only happens with i810 driver installed).  I'm pretty sure I have the right driver installed (xserver-xorg-video-i810), but I've also used xserver-xorg-video-intel, xserver-xorg-video-vesa, and xserver-xorg-video-vga all with almost equally similar performance (none of those three have the resolution change on logout).

So here's my understanding of my computer specs:
Gateway 310S
Intel Celeron
onboard graphics/sound
OS - Hardy Heron

more specifically:
```
home@desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

I also decided to check the Gateway website using my serial number and got [this result]("http://support.gateway.com/support/drivers/getFile.asp?id=19757&uid=227745133") for my video driver.

So does anyone know if I'm doing anything wrong here, or if there's anything I should try to improve performance?

---

### Post by rjl6591 on 2009-03-27
How much RAM have you got in this machine? Is it swapping a lot? What do you get if you type:

  free

---

### Post by IanVonSpeedfreak on 2009-03-27
*facepalm*

I had a feeling I was forgetting something, but I was in such a rush to post (I was multi-tasking at the time).  Anyway, I'm supposed to have 128MB of RAM - yeah, that's really bad, I know.

So here's the output:
```
home@desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        246780     243108       3672          0        580      30848
-/+ buffers/cache:     211680      35100
Swap:       714852     139744     575108
```

That reminds me, it seems that when I first install a different driver, it doesn't use swap at all, and performs much better, but then after a few boot ups, swap gets more and more used up and things get sluggish.

---

### Post by rjl6591 on 2009-03-27
It looks as though you've got 256MB RAM but the Intel graphics will be using some of that. It's swapping quite heavily and that's probably the problem. You need either to increase RAM or reduce memory usage, although the latter isn't easy.

The display switching resolution when you log out is normal. If there are multiple users they can each set their own preferred resolution without affecting anyone else's. When you log out it returns to the default.

xserver-xorg-video-intel is probably the best driver.

---

### Post by IanVonSpeedfreak on 2009-03-27
While I'm pretty sure I still need to upgrade my RAM, part of the problem is one of my favorite programs - Firefox.  It and KDM have been using up the largest portion of memory according to ksysguard, so it would help in the interim if I could find some reasonable alternatives to them (those two were both running when I ran free).  In any case, I appreciate your help and advice, and I'll probably install xserver-xorg-video-intel as you've suggested.

Much thanks.

---

