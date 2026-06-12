---
title: "Boot problem"
date: 2009-02-19
forum: General Help
---

### Post by Macamba on 2009-02-19
Hi,

Can anyone help me with my problem? 

When I start up my system, and having chosen Ubuntu to start (dual boot configuration) Ubuntu starts nicely. I first see the 'scanner' prompt going from left to right, and back, while (I think) the kernel is loaded. Next the prompt starts from left, and progresses to right. That is normal behavior. 

When everything is loaded, it is time for the boot prompt window to appear. At that point it often goes wrong. The PC stops sending information to the screen, the screen thinks it is end of operations, and goes of too.

Sometimes I hear the sound that is played when the boot window is displayed. Once I even logged in, after which the Ubuntu welcome sound is played. But this all happens while staring at a black screen.

I tried to reanimate the session by pressing Ctrl-Alt F8. Nothing happens. Pressing the combo for a second time starts my screen, in text mode, displaying:
```
Fatal could not determine fully qualified hostname
Please set 'visible_hostname'

Starting anac(h)ronistic acon anacron                  Fail
Starting deferred execution sludater afd               OK
Starting periodic command scheduler                    OK
Checking ttry state ...
  /dev/sda:
  setting Advanced Powermanagement level to 0xfe (254) OK
  running local boot scripts (/etc/rc.local)           OK
```

Does anyone have a solution for me? It sometimes happens also after rebooting once, or even twice after a black boot screen. So it is a persistent error.

Someone suggested turning off my (NVidea) graphics card. Is that something to persue? What should I do to accomplish that?

Abel

---

