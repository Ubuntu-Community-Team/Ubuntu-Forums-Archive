---
title: "Compiz check help!"
date: 2009-05-16
forum: Desktop Environments
---

### Post by andydandy325 on 2009-05-16
So I ran Compiz check and this is what I got....
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2562 detected. 

Would you like to know more? (Y/n) Y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N)
```should I skip the blacklist? what could happen?

This is my first post in the forums. help with this is greatly Appreciated!):P

---

### Post by andrea000 on 2009-05-16
i ran a blacklisted check with mine and had no problems but
as with all things it could cause some i guess.try checking
the internet and compiz website first to see if it is 
blacklisted no need to run the check if you can find out
another way.

---

### Post by raymondh on 2009-05-16
I have one computer whose card was blacklisted. I decided to skip the blacklist and what I got was a "slow" compiz... that I ended up disabling it.  Some forum members have other (successful) results. A quick search will reveal lots of varying results.

As always, the decision is yours and no one can guarantee results.  As for me, I have decided to wait until said card is whitelisted and just have the good 'ol desktop in the meantime.

Good luck.

---

### Post by andydandy325 on 2009-05-16
Thanks guys!
I decided to un-blacklist it, and when I tried to enable the effects all my windows and the panels disappeared. The only thing on the screen was the mouse.Oh well, thanks for your help. 

so basically eventually my video card will be whitelisted?

---

### Post by raymondh on 2009-05-16
> **andydandy325 said:**
> Thanks guys!


so basically eventually my video card will be whitelisted?

I'm sorry to hear that.  Keep on searching  and googling around. We can all hope that the devs' will get a fix soon for our respective cards. 

Nevertheless, my "plain 'ol gnome desktop with no compiz" in 9.04 is still as productive (for me) as my other computers that have compiz enabled :)

Hopefully, Karmic will be better ... 

Raymond

---

### Post by andydandy325 on 2009-07-05
I fixed it!!!!!!!!!!

Here you go!

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

