---
title: "3D drivers in ubuntu 9.04"
date: 2009-05-27
forum: General Help
---

### Post by CLoss on 2009-05-27
Ok my laptop has 3d drivers but the thing is i don't know if they are activated, because everything runs smooth in my vista but if i try to play a game in ubuntu its all jumpy, i.e World of Padman can any1 help please, does any1 know how i can check if it is activated or if there is a way i can activate them,
thankyou.

---

### Post by Bender2k14 on 2009-05-27
Are you using the newest version of Ubuntu?...9.04 Jaunty?  If you are, then I check if 3D graphics are enabled by triggering a notification (such as disabling Network).  When the notification bubble appears, put your mouse over the bubble.  If the bubble completely disappears, then you are NOT using 3D graphics.  If the bubble goes 10% transparent, then you ARE using 3D graphics.

I want to understand 2D and 3D graphics better, but this is the best I got for now.

---

### Post by albinootje on 2009-05-27
> **CLoss said:**
> my laptop has 3d drivers 

Post "lspci" output please.

---

### Post by CLoss on 2009-05-27
ok how do i disable network, and thankyou

---

### Post by Bender2k14 on 2009-05-27
> **CLoss said:**
> ok how do i disable network, and thankyou

In the Notification Area, there is an icon for the Network Manager.  If you right-click it, you can uncheck Enable Networking to disable networking.

---

### Post by CLoss on 2009-05-27
ok i did it and it just dissappears witch means they are disabled, my laptop in a dell studio 15 and it hasd the drivers, does any1 now know hoew do i activate them please.
and what do you mean by "lspci" albinootje?

---

### Post by Bender2k14 on 2009-05-27
> **CLoss said:**
> what do you mean by "lspci" albinootje?

He means, open a terminal (Application -> Accessories -> Terminal), type that command, and hit enter.

---

### Post by Yellow Pasque on 2009-05-27
```
LIBGL_DEBUG=verbose glxinfo
```

---

### Post by CLoss on 2009-05-27
ok thankyou i tryed oth commands
lspci
and

LIBGL_DEBUG=verbose glxinfo[FONT=Verdana]

AND my ubuntu is still gittery with games.
y would this happen?
[/FONT]

---

### Post by Bender2k14 on 2009-05-27
> **CLoss said:**
> ok thankyou i tryed both commands
lspci
and
LIBGL_DEBUG=verbose glxinfo[FONT=Verdana]

AND my ubuntu is still gittery with games.
y would this happen?
[/FONT]

I am not sure what
```
LIBGL_DEBUG=verbose glxinfo
```
does for sure, but
```
lspci
```
does not modify your system.  It simply prints all the devices that use your PCI Bus.  Can you paste the output of
```
lspci
```
into your next post?

---

