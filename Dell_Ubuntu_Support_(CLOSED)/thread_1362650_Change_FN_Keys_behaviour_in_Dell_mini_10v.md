---
title: "Change FN Keys behaviour in Dell mini 10v"
date: 2009-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by primolarry on 2009-12-23
Hi there,

I've installed UNR 9.04 in my new mini 10v and almost everything works perfecly. However, there are two small issues that are bugging me.

-FN Keys. By defualt, I need to press "FN" to access to F1,F2, etc. That is, if I want to lower the volume for instance, I need only to press the key labeled F8/vol_down. However, if I want F8 I have to press FN+(F8/vol_down). I'd like this to be the other way, normal press meaning F8 (any Fx actually) and needing to press the FN key to access the special functions

-The wifi on/off key (F2) is not working. It's kind of strange, because all the other special keys (volume, brightness, battery, etc.) work perfectly. Somebody having a mini 10v with jaunty can tell me if this happens to them as well?

Thanks in advance, regards

---

### Post by Brandon Williams on 2009-12-23
> **primolarry said:**
> 
-The wifi on/off key (F2) is not working. It's kind of strange, because all the other special keys (volume, brightness, battery, etc.) work perfectly. Somebody having a mini 10v with jaunty can tell me if this happens to them as well?


The wireless key doesn't do anything on its own. You have to map it to a program to make it turn the wireless on/off. That program is aircraft-manager, which you can install from [my PPA repository](https://launchpad.net/~opensource-subakutty/+archive/ppa). I updated the packaging so that it can be installed on later versions of Ubuntu and I fixed it so that it works with the new network manager.

The backward Fn key behavior bothers me, too. I haven't been able to find a way to make it work the other way.

---

### Post by primolarry on 2009-12-29
Thanks Brandom, your PPA was very helpful :)

Now I have linked the key to aircraft-manager, but I still have to enable manually the aircraft mode. Is there any way to do it automatically, like calling "aircraft-manager --togle-aircraft-mode" or something simillar?

Regarding the other issue, I haven't been able to do it as well. I'll report if I do.

Thanks

---

### Post by Brandon Williams on 2009-12-29
You probably don't want aircraft mode to be enabled automatically, since it will prevent the battery from charging. I assume that you're looking to automatically disable one or both of the radios. You can use aircraft-manager-util for that.

```
gksu aircraft-manager-util WIFI off
gksu aircraft-manager-util BT off
```

---

### Post by primolarry on 2010-01-06
> **Brandon Williams said:**
> You probably don't want aircraft mode to be enabled automatically, since it will prevent the battery from charging.

Really?Why is that?We are not supposed to charge devices in a plane?

Regards (and thanks for the instructions with aircraft-manager-util)

---

### Post by primolarry on 2010-01-14
I finally found out how to solve the Fn issue. There is an option in the BIOS to change the FN behaviour.

Regards

---

### Post by dejan.jovanovic on 2010-02-17
thanks for the bios tip, life is so much better now.

---

### Post by HyperFlexed on 2010-07-07
I have an inspiron mini 1012 (mini 10, not 10v), if your bios trick flies, I am forever in your service.

Basically this is the stupidest design I've ever seen. I'm guessing they figure windoze users don't have any use for the keys, so it's easier to dumb down the design and waste the F6 key entirely. Man.. just *facepalm*

---

### Post by primolarry on 2010-07-20
Hope it will work out for you as well HyperFlexed.

Brandon, will aircraft-manager be avalaible for lucid as well?

Thanks, regards

---

