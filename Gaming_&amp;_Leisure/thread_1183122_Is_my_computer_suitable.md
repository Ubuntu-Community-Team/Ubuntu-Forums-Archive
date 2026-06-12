---
title: "Is my computer suitable?"
date: 2009-06-09
forum: Gaming &amp; Leisure
---

### Post by connorh123 on 2009-06-09
Hi,
I play Counter-Strike 1.6, Nonsteam, and recently, I've had some problems. However, that's not why I'm here, I'm wondering if my computer can keep up with Counter-Strike. Here is my information.
Graphics Card: ATI Radeon 7500
256MB
Intel Mobile Pentium M at 1.6GHz
40GB
And I think that's it.
Thanks in advanced.


[This is the laptop I'm using.]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-41638")

---

### Post by CharmyBee on 2009-06-09
Bump up the ram a little bit more to 512MB and you'll be able to Ubuntu on there, however since it's a laptop and you're stuck with the Radeon 7500 which has bad driver support,  you'll have to do CS in software.

---

### Post by connorh123 on 2009-06-09
Software doesn't really work for me, I can't change which hand I use or anything. I use OpenGL, and it seems to be working. What about D3D?

---

### Post by lisati on 2009-06-09
I'm not familiar with running Counter Strike, but would opt for more RAM as well. The laptop I recently gave to my nephew only has 222Mb of available RAM: although I was able to get Ubuntu to work on it, performance was less than ideal.

---

### Post by connorh123 on 2009-06-09
Also, the game worked before, fine. Not so sure why it's not now.

---

### Post by eragon100 on 2009-06-10
Counterstrike is a pretty old game AFAIK, so I don't think it should have any problems on your machine. It runs under wine just fine on ubuntu, so don't worry :wink:

---

### Post by connorh123 on 2009-06-10
It actually runs horrible. It ran perfect in Hardy, and awful in Jaunty. It randomly shuts down whenever I'm playing.

---

### Post by eragon100 on 2009-06-10
> **connorh123 said:**
> It actually runs horrible. It ran perfect in Hardy, and awful in Jaunty. It randomly shuts down whenever I'm playing.

That's probable because you are now using the open-source (AKA complete utter crap) ati drivers that come with Jaunty. They have 3d acceleration, but it's, let's say, not optimal. unfortunately, ATI has dropped support for older cards such as yours in the newest official drivers, and the old version that supports your card doesn't work in Jaunty. In other words, the only way to fix this is to downgrade to at least intrepid ibex 8.10, and then install the old version of the official ATI drivers that still support your card. I am afraid there is no other way to fix this :(

---

### Post by ELD on 2009-06-10
Is there no way to install an older catalyst driver in jaunty? If not this will surly single out a lot of people?

---

### Post by CharmyBee on 2009-06-10
> **eragon100 said:**
> That's probable because you are now using the open-source (AKA complete utter crap) ati drivers that come with Jaunty. They have 3d acceleration, but it's, let's say, not optimal. unfortunately, ATI has dropped support for older cards such as yours in the newest official drivers, and the old version that supports your card doesn't work in Jaunty. In other words, the only way to fix this is to downgrade to at least intrepid ibex 8.10, and then install the old version of the official ATI drivers that still support your card. I am afraid there is no other way to fix this :(

The 7500 wasn't supported in fglrx for 8.10 either. They dropped support for the 7x series somewhere in 2006.

---

### Post by connorh123 on 2009-06-10
So downgrade to Hardy I guess?

---

