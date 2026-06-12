---
title: "Unable to enable Visual Effects"
date: 2009-12-25
forum: Desktop Environments
---

### Post by trintin7 on 2009-12-25
As the title said I'm using ubuntu 9.10 on HP dv2108tx. I had already run the Compiz-Check Script

Result
```
USRNAME-UBUNTU:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72M [GeForce Go 7200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```Any advice would be appreciate
Thx in advance

---

### Post by charonred on 2009-12-25
OK, going over the basics; have you added/enabled the restricted drivers (check System > Adminstration > Hardware Drivers) and rebooted. If so have you installed compiz and *compizconfig-settings-manager (and any other related items - I use Emerald as the decorator).

* once this is installed, you should have System > Preferences > Advanced Desktop Effects Settings available.

---

### Post by trintin7 on 2009-12-26
> **charonred said:**
> OK, going over the basics; have you added/enabled the restricted drivers (check System > Adminstration > Hardware Drivers) and rebooted. If so have you installed compiz and *compizconfig-settings-manager (and any other related items - I use Emerald as the decorator).

* once this is installed, you should have System > Preferences > Advanced Desktop Effects Settings available.

I had already enabled the latest nVidia driver and rebooted several times before posting this. I could access to the nVidia Control Panel and pass all the diagnostic test before posting this. When I was going to enable the Effects it was looking for suitable driver for a while before it fails to enable the effects.

---

### Post by andrea000 on 2009-12-26
if you have installed compizconfig-settings-manager and
the latest nvidia driver right click on the desktop pick
change desktop background and then the visual effects tab
then pick extra.You can also run compiz in the terminal

applications->accessories->terminal
> compiz

and see if that gives you any errors

---

### Post by trintin7 on 2009-12-26
> **andrea000 said:**
> if you have installed compizconfig-settings-manager and
the latest nvidia driver right click on the desktop pick
change desktop background and then the visual effects tab
then pick extra.You can also run compiz in the terminal

applications->accessories->terminal


and see if that gives you any errors

No errors was given but I'm still unable to enable the effects

---

### Post by andrea000 on 2009-12-26
Have you set the effects in compizconfig setting manager?

---

### Post by trintin7 on 2009-12-26
> **andrea000 said:**
> Have you set the effects in compizconfig setting manager?
I did

---

### Post by andrea000 on 2009-12-26
ok this is one mistake i made when i first installed compiz on
the animations tab there is a open space were the effect is listed
the effect you are wanting to use needs to be the first one on the
list.The cube is a little bit harder to set up but not much.Check
to see if there is a check by the plug in and then click the
animations plug in and make sure the one's your trying to use is
the first on the list.

---

### Post by trintin7 on 2009-12-26
I'm not sure what I did but after messing with the config and restart the computer the effects just got itself enabled !
Thanks for the help by the way.

---

### Post by andrea000 on 2009-12-26
your welcome but i don't think i did anything.I'M glad
your up and running now

---

### Post by VastOne on 2009-12-29
> **andrea000 said:**
> ok this is one mistake i made when i first installed compiz on
the animations tab there is a open space were the effect is listed
the effect you are wanting to use needs to be the first one on the
list.The cube is a little bit harder to set up but not much.Check
to see if there is a check by the plug in and then click the
animations plug in and make sure the one's your trying to use is
the first on the list.

Hi Andrea!

Are you saying here that Animations just needs to be enabled?  I am having a new issue of Visual Effects keeps on turning itself off on every reboot and I am trying to see if this is related

Hi

---

