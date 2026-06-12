---
title: "compiz fusion, what to do?"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by superbungalow on 2007-08-03
I have tried many compiz-fusion tutorials, all of which have failed, and 2 of which have caused me to re-install ubuntu completely. I have a packard bell easynote, with an intel core duo processor, and graphics by ATi. I have completely updated my system, and am running feisty. Can anyone tell me the first thing I need to do in order to prepare for installing compiz-fusion. I can post the output of any programs if you need me to, if you need more information about my laptop. Thanks!

---

### Post by fofo412 on 2007-08-03
Which ATI  card do you have?  Some are supported, some are not.

What fails in the tutorials?  More specifics are needed. . .

---

### Post by superbungalow on 2007-08-03
I don't really understand, I just get error messages like: "GDLRS not available" or something like that (probably wrong), or everything goes liny and spazzes out on the screen. How do I find out what ATi card I have?

---

### Post by miggols99 on 2007-08-03
Type "lscpi" (without quotes) into the terminal and post the output.

---

### Post by atomkarinca on 2007-08-03
> **miggols99 said:**
> Type "lscpi" (without quotes) into the terminal and post the output.

that should be
```
lspci
```
i guess.

---

### Post by superbungalow on 2007-08-04
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Does anyone know what I need to do first?

---

### Post by atomkarinca on 2007-08-04
have you tried this tutorial: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) ?

your graphics card is ati radeon xpress 200m, by the way.

---

### Post by superbungalow on 2007-08-04
Yess, and when I ran compiz --replace, my screen went black
I had to hold down the power button to turn it off, and then when I booted back into ubuntu I gott some message about devices with GRDRL or something and I couldnt run it. I had to re-install the whole operating system!

---

### Post by superbungalow on 2007-08-04
What are the requirements for running compiz-fusion? And what is the first step I should take?

---

### Post by atomkarinca on 2007-08-04
there is howto here for your specefic graphics card, maybe that could help:
[http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)

---

### Post by superbungalow on 2007-08-04
umm, thanks, that looks like a good tutorial, but could someone eplain it, as I don't really understand the guy. He just types things fast in all caps.

---

### Post by SkippyIsForYou on 2007-08-04
Just follow the guide exactly as it was written.

---

### Post by superbungalow on 2007-08-04
> Right now i'm out off time, but when i have some, i'll try to install ATI drivers from ATI site into version V 7.04
Right now just activate all options in the repositories, do a update in System -> Administration -> Update Manager, go to System -> Administration ->Restricted Drivers Manager and activate ATI driver.
NOTE: DESKTOP EFFECTS DOES NOT WORK !!!!! ATI DOES NOT SUPPORT COMPOSITE EXTENSION!!

do I have to do that stuff, or is he just saying it about what he did?

also, this tutorial is for beryl, not compiz fusion, and is for edgy, not feisty.

---

### Post by superbungalow on 2007-08-04
I found this thread:

[http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)

He says: "I assume that you have fresh system install with proprietary drivers enabled."

How do I check/ do this?

---

