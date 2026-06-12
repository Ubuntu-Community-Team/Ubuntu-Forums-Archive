---
title: "Jaunty 9.04 Suspend problems"
date: 2009-05-24
forum: General Help
---

### Post by kevin82485 on 2009-05-24
Whenever I enter suspend mode, my screen just goes blank except for a blinking cursor in the top left corner.  All of the fans in my computer are still running and there is no way to get out of this except by pressing the reset button.

I've read other threads about suspending problems but none seemed to be quite like mine, or it was with an earlier version of Ubuntu.

---

### Post by kevin82485 on 2009-05-24
Anyone know what is wrong?

---

### Post by kevin82485 on 2009-05-26
Would this have anything to do with my Nvidia 9800GT video card?  I used the driver Ubuntu recommended, I don't think its the official Nvidia driver.

---

### Post by juankaos on 2009-05-28
i'm having a similar problem with my pavilion dv7. after I suspend and then open the laptop again, I can see the login screen with a blinking cursor but neither the mouse nor the keyboard respond. Any help would be greatly appreciated

ubuntu 9.04 64bit
ati radeon graphics with the driver ubuntu suggested

---

### Post by kevin82485 on 2009-05-29
I'm still looking for help...I'm not going to use Ubunutu until this is fixed.  No sense in completely shutting down my computer every time I'm finished using it.

I have a computer I built myself. Dual boots Ubuntu 9.04 or Win XP. ASUS P5B Deluxe, Intel Core 2 Duo E6600, 3 GB RAM, Nvidia GeForce 9800 GT.

I have had the exact same problems since Ubuntu 8.10.

If anyone knows how to fix this please post or PM me.

---

### Post by PGScooter on 2009-05-29
hi kevin and juancaos,

have you guys seen this?

HowTo: Fix suspend and hibernate on laptops
```
http://ubuntuforums.org/showthread.php?t=471855
```

---

### Post by kevin82485 on 2009-05-29
> **PGScooter said:**
> hi kevin and juancaos,

have you guys seen this?

HowTo: Fix suspend and hibernate on laptops
```
http://ubuntuforums.org/showthread.php?t=471855
```

Does this apply to desktops as well?

---

### Post by PGScooter on 2009-05-29
kevin,

I would think so, but am not 100% sure. Either way, I figure it's worth a read.

---

### Post by kevin82485 on 2009-05-29
> **PGScooter said:**
> kevin,

I would think so, but am not 100% sure. Either way, I figure it's worth a read.

Thanks for your help man, I'll give it shot and see if it works.

---

### Post by kevin82485 on 2009-05-29
Sadly, the suggest in that thread did not work.

When I entered ```
/sbin/s2ram --force
``` it just returns me to the login screen.


I'm beginning to think it has something to do with my system BIOS.

But I'm just a beginner with Ubuntu and Linux in general.  Most of the stuff that is talked about on here is like Chinese to me.  I'm really good with Windows but obviously not with Ubuntu.

---

### Post by eluminx on 2009-05-29
Do you still have to option to suspend available on your shutdown menu?  FOr some reason i dont have available on mine and was wondering why it when i installed jaunty it was working fine, then all of a sudden it just not there anymore.  I dont mean to steal the thread, i just my prob is similar to yours.  Any help would be greatly appreciated it.

---

### Post by avilella on 2009-05-30
Hi,

I created a Linux Launchpad team for the people who own or develop for the HP dv4z (or dv2z/dv5z/dv7z) series laptops with discrete ATI graphics card, so that we can have more information from users that use Linux, and send better bug reports upstream. This will give us more visibility as a group when having to ask for patches or support.

If you are new to the group and you own or develop for this laptop (discrete ATI graphics card version, not the dvXt version with Nvidia or Intel graphics card), please subscribe to this team:

[http://launchpad.net/~dv4z](http://launchpad.net/~dv4z)

Cheers,

Albert.


> **juankaos said:**
> i'm having a similar problem with my pavilion dv7. after I suspend and then open the laptop again, I can see the login screen with a blinking cursor but neither the mouse nor the keyboard respond. Any help would be greatly appreciated

ubuntu 9.04 64bit
ati radeon graphics with the driver ubuntu suggested

---

### Post by linuxgeoff on 2009-10-26
did anyone come up with a fix?

I have a toshiba m200.  I've had ubuntu since feisty and got suspend to work ok on every version till 8.04, until I double upgraded to 9.04, and now I have excatly the same sysmptoms as the original poster.

---

