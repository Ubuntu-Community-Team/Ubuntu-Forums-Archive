---
title: "Lightdm mouse cursor disapear (16.04 LTS)"
date: 2017-02-23
forum: Desktop Environments
---

### Post by jambyc on 2017-02-23
Hi,

After system update as my server was off for few weeks mouse cursor disappearing half way on the screen ( bottom horizontal )
I am on 1920x1080 (16:9) resolution (My screen is 21 or 22 inch screen). When I go down to 1280x720 (16:9) mouse cursor is visible on full screen. 
Is it graphic card issues or lightdm?
I have tried
- installing gm3 and pointing back to lightdm as main GUI
-ALT_CTR_F1/F7
and none of worked. 
I am using
40:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV635 [Radeon HD 3650/3750/4570/4580] [1002:9598]

Any suggestions?

---

### Post by NMrpHzy on 2017-03-01
I'm having the same issue with 16.10, running at 1920x1080 resolution

---

### Post by jambyc on 2017-03-14
So just too visual what I am talking about... :)

[https://www.youtube.com/watch?v=pxzC39x2DNo](https://www.youtube.com/watch?v=pxzC39x2DNo)

---

### Post by jambyc on 2017-04-09
Anyone help?

---

### Post by chocapic2017 on 2017-04-10
i had the same problem, i solve the problem :
- when you start your computer, in grub, choose to start Ubuntu with the kernel 4.8.0-36
or
- install the last kernel 4.10.0-19 from zesty (Ubuntu 17.04)

don't use 4.8,0-46, it works only with mir, not Xorg

---

### Post by jambyc on 2017-05-17
Ohh!!! Just log in to see of any reply :)

After update & upgrade I have restarted server and everything come back to normal state.
I am to thick to understand what happened but at least it is working. :)

... for now.

---

