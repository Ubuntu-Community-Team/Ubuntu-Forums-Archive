---
title: "Wireless card not working with Dell Studio XPS 1640"
date: 2009-12-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by etfd on 2009-12-25
Recently ran into this issue and thought I would post my fix for others to check out...

I installed Ubuntu on a new Dell Studio XPS 1640. The wireless card was not working however. 

It turns out that Dell's Broadcom drivers are proprietary and hence do not install with Ubuntu. (This should have been obvious in retrospect! :rolleyes:) This can be fixed by going to System -> Administration -> Hardware Drivers. You should be able to install the Broadcom STA wireless driver from this screen.


 Now, in my case, this installation of the Broadcom driver hung / failed and I had to install the drivers manually. To do this point your browser over to [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and download and install according to the README. 



-David

---

### Post by j03l5k1 on 2010-02-09
Hi, thanks for posting this i have the exact same problem.

I am a complete noob (literaly been using it for about 2 hours now) to linux and im struggling bad.

Could you please explain in retard terms how i install a tarball.

I have read many other posts on this forum, but im lost in the jargon. i dont know what make install, check install, ./configure or anything is nor am i familiar with terminal or what software i need to do this.

Sorry for not lurking enough to find this out for myself but i cannot plug the laptop in near the router (i need to use ethernet as no wifi driver) because theres not enough power points.


thanks so much in advance, im off to charge the laptop and then come back.


Kind regards,

Joel

---

