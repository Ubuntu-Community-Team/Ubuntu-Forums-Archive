---
title: "Help installing old version of xorg"
date: 2008-04-28
forum: Desktop Environments
---

### Post by nett3 on 2008-04-28
Is it possible to install an older version of X Server in order to install older graphics card drivers? I have the 11R7.01 tar of X server but I am having a hard time compiling it and don't know how to go about installing it/removing the newer version.

As far as compiling I have done ./configure but them "make" does not work.

---

### Post by kerry_s on 2008-04-28
to little info.

what graphics card?
what drivers?

---

### Post by nett3 on 2008-04-28
The card is a Radeon Mobility 9200 and the drivers are 8.28.8 from the ATI site, the last ones to support this card but require only certain versions of xorg and some other requirments which I was able to meet.

The card and drivers is irrelevant really, all I want to know how to do is install/compile an older version of x server. Or is there some way to have the latest backwards compatible?

---

### Post by kerry_s on 2008-04-28
[http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200](http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200)

---

### Post by nett3 on 2008-04-28
Thanks for replying, I have read that guide over many times and it doesn't help with the problem. I actualy have the same laptop as mentioned but his solution to installing the proprietary drivers is "Install the proprietary driver for your graphic card using the Restricted Drivers Manager."

In hardy this does not work as there is nothing listed in the Restricted Drivers manager. The guide does not go into any detail on how to install the drivers. Perhaps I need to drop hardy and go to gutsy. I cant understand why support would be removed for hardware in the newer version.

---

### Post by kerry_s on 2008-04-29
would have been nice to know you were using hardy.

a quick google confirms it is busted in hardy.

dropping to gutsy is a good idea. if you need help with the driver in gutsy-> [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by nett3 on 2008-04-29
Thanks for your help kerry_s. Is there going to be any updates that fix this sort of thing or will it be unsupported from now on?

---

