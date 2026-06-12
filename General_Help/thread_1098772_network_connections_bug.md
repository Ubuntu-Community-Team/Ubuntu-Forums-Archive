---
title: "network connections bug"
date: 2009-03-17
forum: General Help
---

### Post by kristiansuhl on 2009-03-17
Hello!

I have a strange problem with my Ubuntu 8.10 Intrepid Ibex. 

With this version of Ubuntu, the "network connections dialogue" seem to have some kind of malfunction. Every time I reboot, ubuntu "forgets" my network info and I have to put it all in there once more....

it forgets ip, netmask, gateway and dns servers... I posted some questions about this before and the only way to get around seem to be to run another network connections program instead of the present one which seem very strange to me. For half a year ubuntu does not support static IP...

This only happens when I have a static IP, "method: manual" - when I have "method: automatic" and dynamic IP the computer works just fine after a reboot.

To me - this seem like such a gargantuan bug that I cannot understand why it has not been fixed yet. Is there a way to know if this bug is reported and if it will finally be fixed for the next version of ubuntu?

This is all so strange to me that I'm beginning to think that it is I who have misunderstood the whole thing. 



Maybe you guys can help me - is it me who got the whole thing wrong or is it really this strange? 


Thanks for all your help on various problems I've had in the past by the way! :-)

---

### Post by prince_niceguy on 2009-03-17
is it a laptop or desktop? if it is desktop i would advice to modify the network config directly so that network manager does not do anything on it.

if it is laptop (or a computer which you move around with frequently) then i am not sure how to resolve this.

---

### Post by kristiansuhl on 2009-03-17
it's a laptop! :-)

so this is an actual bug then?

---

### Post by prince_niceguy on 2009-03-17
Not sure, have never tried doing a static ip on the laptop. Are you referring to home network or office network?

If it is home, then would recommend setting static ip on your router, would give you same ip even after system reinstall or loging into some other distro or OS.

---

### Post by kristiansuhl on 2009-03-17
I have it at home and no router unfortunately. The thing is that I sometimes need to use a dynamic ip so my wish is to be able to change between these two from time to time.

---

### Post by prince_niceguy on 2009-03-17
do you get a static ip from you provider? if there is no router i would recommend not to do a static ip (unless you have opted with your provider) as whenever you will contect the ip may change and you may cause clash with some other person's ip.

---

### Post by kristiansuhl on 2009-03-17
ahh no - I am required to use the same static ip always as it is handed out to us by the ISP.

---

### Post by Chris Musampa on 2009-03-17
> **kristiansuhl said:**
> I have it at home and no router unfortunately. The thing is that I sometimes need to use a dynamic ip so my wish is to be able to change between these two from time to time.

Similar to myself, I use static IP wireless at home, static wired occasionally at work and DHCP wired at a friend's house.  Network Manager fails miserably in 2 of those 3 situations on my laptop whereas WICD has no problems with at all for me.  This been the case for me in gutsy, hardy and intrepid.

It may or may work as well for you but I would definitely give WICD a try.

---

### Post by kristiansuhl on 2009-03-17
> **Chris Musampa said:**
> Similar to myself, I use static IP wireless at home, static wired occasionally at work and DHCP wired at a friend's house.  Network Manager fails miserably in 2 of those 3 situations on my laptop whereas WICD has no problems with at all for me.  This been the case for me in gutsy, hardy and intrepid.

It may or may work as well for you but I would definitely give WICD a try.


Ahh, so I'm not the only one with this bad situation then.

I wonder if this issue will be fixed for jaunty?

---

