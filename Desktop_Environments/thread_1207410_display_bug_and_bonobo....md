---
title: "display bug and bonobo..."
date: 2009-07-08
forum: Desktop Environments
---

### Post by deltamoins on 2009-07-08
Hi everybody,
I'm new in this forum so I hope I found the good section to post my question.
I've got a similar problem as in the post here :
[http://ubuntuforums.org/showthread.php?t=35082](http://ubuntuforums.org/showthread.php?t=35082)
I can't answer because it's an archived discussion...
My problem is the following : my display sometimes "flashes" (? I'm French so I don't know perhaps the good word) and sometimes my screen becomes black without any means to get back except restarting...
Here are the log of messages just before the bug :
```

Jul  8 10:40:10 aramis kernel: [  240.040013] Marking TSC unstable due to TSC halts in idle
Jul  8 10:50:39 aramis kernel: [  868.544738] pidgin[3810]: segfault at 0 ip 00000000 sp bfe865fc error 4 in pidgin[8048000+c6000]
Jul  8 10:50:40 aramis kernel: [  869.733930] Xorg[3007]: segfault at 3ce ip b794b6d4 sp bfbbc644 error 6 in intel_drv.so[b7922000+72000]
Jul  8 10:50:43 aramis bonobo-activation-server (yves-4413): could not associate with desktop session: Failed to connect to socket /tmp/dbus-lGGHXnYT69: Connexion refusée
Jul  8 10:50:48 aramis exiting on signal 15

```In fact I've done the hwclock changing as it's proposed at the beginning but it doesn't change anything...
I didn't try to kill the bonobo-activation-server yet but next time it'll bug I will.
But this bonobo stuff does something useful doesn't it ? I mean killing it is not a solution no ?
Does someone can help me please ?

---

### Post by deltamoins on 2009-07-08
Hi again,
The solution proposed in the archive : 
```
killall bonobo-activation-server
```
before restarting the X server didn't work a all...
Help !!!! :-)

---

### Post by deltamoins on 2009-07-09
It's definetly linked to the wifi use because at work where I use my netbook too, I've spent all the day without any problem and I'm linked to the network by a cable. Arrived at home, problems began again...
Help !!!!!

---

