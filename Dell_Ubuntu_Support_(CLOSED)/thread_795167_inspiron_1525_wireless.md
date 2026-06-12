---
title: "inspiron 1525 wireless"
date: 2008-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Maha1980 on 2008-05-15
on the right side of my machine
under the express card 
there is the wireless switch 0 and 1
even if i put it on 1
it doesn't light up
i've never seen the light on
so i think thats why my machine (ubuntu 8) is not picking up the wireless!
anyhelp?

---

### Post by GolanTrevize on 2008-05-15
does [http://ubuntuforums.org/showthread.php?t=751405](http://ubuntuforums.org/showthread.php?t=751405) apply to your configuration?

---

### Post by notwen on 2008-05-15
What version of Ubuntu are you running?  Gutsy or Hardy?  Which wireless card do you have?  

Let's figure out which wireless card you have in your machine, please copy & paste the following command into a terminal and paste the output back here:

```
lspci
```

---

### Post by NineKnuckles on 2008-05-18
The wifi-catcher lights only work when the laptop is off.  They were designed, as far as I know, to be used to check for wifi signals without having to wait for your laptop to power up.  When your laptop is on, the wifi-catcher lights stay off and the wifi indicator, next to the battery indicator, should light up (it doesn't actually work in hardy) or an on-screen applet should show up.

---

