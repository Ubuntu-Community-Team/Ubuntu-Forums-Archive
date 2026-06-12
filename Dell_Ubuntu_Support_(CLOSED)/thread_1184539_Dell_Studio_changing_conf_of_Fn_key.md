---
title: "Dell Studio changing conf of Fn key"
date: 2009-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by szymonnn on 2009-06-11
Hello,
I am using Dell Studio 1555. Everything works great but I would like to change configuration with Fn key. Now to mute music I need to press F7 and Ubuntu sees it as XF86AudioMute, when I want just to use this key as normal F7 I need to press Fn+F7. Is it possible to reverse it? I mean, pressing F7 will be recognized as normal F7 and Fn+F7 as muting sound.

---

### Post by chris.evers on 2009-06-24
You can change this behavior in the bios.
- Press F2 on boot
- Advanced -> Function Key Behavior -> Function Key First

---

### Post by ccube on 2010-01-18
Hi,
I recently got my brand new Studio 1557.
The default Mapping ist Special key first, and funtion key in combination with "fn".
Of cource I can change this in BIOS, but after some time. (No Idea when andy why) it reverts back to Media key first.... :(

Is there any hidden key combination or something like this?

Anyone knows the trick?

greetz,
ccube

---

### Post by Hemenesgard on 2010-05-18
ccube, i am having the same problem. I change the order in the BIOS but after sometime it backed to set multimidia kyes first

I am using a Dell Studio 1557 and 10.04 ubuntu version.

---

### Post by Jest3r on 2010-06-10
> **chris.evers said:**
> You can change this behavior in the bios.
- Press F2 on boot
- Advanced -> Function Key Behavior -> Function Key First


I used the above to achieve the desired result, I'll let you know if mine reverts back.


```
$ cat /sys/class/dmi/id/product_name 
Studio 1558
```

---

### Post by ccube on 2010-06-14
The problem seems to be only on a 1557 board. Now I have an 1558, and it is working fine. I dont know where the difference is.

---

### Post by LegalizeFreedom on 2010-06-17
I have a studio 1555 and Ive noticed the same problem but with the "password at boot" option. The password that i choose is still there, but the option to use a password is disabled. I don't get it because I've never had this problem before Ubuntu. I don't even understand how a OS can even do that.

---

### Post by LegalizeFreedom on 2010-06-17
i'm dual booting by the way, is anyone else? Maybe its related to grub?

---

### Post by anantshri on 2010-06-17
i have dell studio 1555 and can confirm this is not os dependent.


I have this errors and time at which i have is at times related to battery discharge.

If you remove battery from the laptop even if its off or when battery is critically discharged password is gone.

hope that helps.

---

### Post by Tosho on 2011-04-09
Same here.
Dell Studio 1555.
While I'm using Ubuntu it's changing the F keys by itself even when I change them  from the BIOS dozen of times. 
Can they be set from Ubuntu ?
and how the hell the OS is accessing the BIOS ?

---

