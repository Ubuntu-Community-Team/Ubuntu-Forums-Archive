---
title: "Authorize Reboot For Automation"
date: 2008-12-06
forum: General Help
---

### Post by Rodney9 on 2008-12-06
I am trying to get my computer to start automatically when I need it. I am the only user. So far I have found code to wake the pc ([http://ubuntuforums.org/showthread.php?t=938533&highlight=rtcwake&page=2](http://ubuntuforums.org/showthread.php?t=938533&highlight=rtcwake&page=2)), Thank You Frigaut and Altay_H
 
code > sudo rtcwake -u -s 1800 -m on

 Seeing the suspend/hibernate wont wake up my usb keyboard, I was going to put 'reboot' into Alarm Clock a few minutes after the pc wakes and then after the reboot everything would be working.

My problem is that 'reboot' says "need to be root" even though I have granted my self in Authorizations.

So I need to know how to authorize myself for 'reboot' and 'rtcwake'

Rodney.

---

