---
title: "Help With Beryl Installation ATI Radeon 9250 AGP 256mb DDR"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by luckyprateek2002 on 2007-12-29
Hey everybody,

I'm very new to linux and i'm fascinated by it. But, i tried installing beryl and i think its hopeless. Its not easy as installing something on windows. I went through different websites finding instructions about glx and fglx and so on... I tried all these approaches and even got the white screen of death and the system hanged a couple of times. I tried going to the beryl website but, their wiki is closed.:(

Can anyone please tell me if its compatible with the card I have and if it is, is there a way for a successful installation of beryl?

Keeping the instructions simple would be highly appreciated:)
If there is anything i should provide like the xorg file thing please let me know thanks!

---

### Post by hotroddude on 2007-12-29
are you using gutsy gibbon? if so you dont need to install beryl. it comes with compiz fusion make sure you have your graphic drivers installed ( im not sure how to install ati drivers sorry) then go to your system-appearance-effects and try enabling them.

---

### Post by Sef on 2007-12-29
> make sure you have your graphic drivers installed ( im not sure how to install ati drivers sorry)

To install the restricted drivers:  System > Administration > Restricted Drivers Management

---

### Post by Waappu on 2007-12-29
> **luckyprateek2002 said:**
> Keeping the instructions simple would be highly appreciated:)
If there is anything i should provide like the xorg file thing please let me know thanks!

Hi

I think best use open source driver with ATI 9250.
Here is my xorg.conf file when I had same card. Beryl was working with this

[http://koti.mbnet.fi/waappu/download/xorg.conf](http://koti.mbnet.fi/waappu/download/xorg.conf)

---

### Post by Forlong on 2007-12-29
> **luckyprateek2002 said:**
> I tried going to the beryl website but, their wiki is closed.:(
Did you read the "Important News" there?
Beryl is a discontinued project, that means it's no longer maintained and there's no support for any recent version of Ubuntu.

So please let us know what version of Ubuntu you are using. If you don't know, post the output of
```
lsb_release -a
``` in a terminal.
> **luckyprateek2002 said:**
> Can anyone please tell me if its compatible with the card I have and if it is, is there a way for a successful installation of beryl?
Compiz (and therefore Beryl as well) is compatible with your card just fine. In fact it should be working out-of-the-box which means you don't have to install any driver - the one that came with Ubuntu should be working best with it.

---

### Post by luckyprateek2002 on 2007-12-29
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

---

### Post by luckyprateek2002 on 2007-12-29
Yea...i already tried that but it says my hardware doesn't need any restricted drivers.

I also tried
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
[https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty)

---

### Post by luckyprateek2002 on 2007-12-29
> are you using gutsy gibbon? if so you dont need to install beryl. it comes with compiz fusion make sure you have your graphic drivers installed ( im not sure how to install ati drivers sorry) then go to your system-appearance-effects and try enabling them.
__________________

No i'm not. Is compiz fusion similar to beryl and will it work if i just enable the effects in gusty gibson? B/c when i tried enabling feisty fawn i got the white screen of death!:(

---

### Post by Forlong on 2007-12-29
> **luckyprateek2002 said:**
> 
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
Alright then try this: [http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149)

---

### Post by hhhhhx on 2007-12-30
why not compiz?

---

