---
title: "blank screen after sleep mode laptop xfce"
date: 2019-04-04
forum: Desktop Environments
---

### Post by userxub-3498 on 2019-04-04
I use older gear and began using Xubuntu 32 bit on my machines a few years back and it's been great, no real problems at all until the most recent update on Monday or Tuesday. Now when the laptop goes into sleep mode it won't "wake up", just a black screen and the machine has to be restarted. When restarting it's very slow now where it used to be fast. 

Any initial thoughts? I searched and can't find other posts about it but surely I'm not the only one. :confused:

---

### Post by userxub-3498 on 2019-04-04
Ubuntu 18.04.2 LTS
Linux 4.15.0-47-generic i686
Xubuntu distro running xfce de

---

### Post by userxub-3498 on 2019-04-05
Ok, so found more info searching: "*Laptop doesn't or won't wake up after sleep / hibernation"*. Still no real answers though the 4.15 kernel is thought to be a possible source of the problem. Going to try stepping back to 4.14 and see.

---

### Post by userxub-3498 on 2019-04-05
Restart > open grub options menu > select previous kernel > complete booting and viola it's back to doing what it did before which is annoying but I can live with it. Now when waking up I have to open and shut the lid twice to get 100% rendering. It's still a 4.15 kernel (4.15.0-46-generic) but an improvement. This has been an ongoing issue for many laptop users why is this still a thing? Seriously. 
Going to try an earlier kernel to see if it can be fully fixed.

---

### Post by userxub-3498 on 2019-04-25
Just completed the new kernel update to 4.15.0-48. I guess it was too much to ask it would be better than the useless -47 and annoying but functional -46. But hey, -48 boots to a black screen!!! YAYYYYYYYYYY!!! Thanks so much to the so-called developers who work so hard to provide faulty crap to all the nice linux users everywhere, really, thanks so much. And we are especially grateful for being ignored and abused, truly. If I wanted to be treated like this I would still use Microsoft. :mad:](*,)

---

### Post by userxub-3498 on 2019-04-25
So, just to restate ( I know no one is reading this but it's cathartic) 

Post update to 4.15.0-48 laptop now restarts to a black screen. And that's the case for two different machines. I'm sure there'll be another million or so folks with the same problem as soon as everyone is awake. (It's 4:40AM)

---

### Post by him610 on 2019-04-25
I also use Xubuntu on several machines, so maybe we can figure this out. Please show, between code tags, the results of *inxi -F*
Does this behavior include your system being powered by both battery and power adapter?

---

