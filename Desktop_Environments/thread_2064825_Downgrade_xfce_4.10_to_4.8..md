---
title: "Downgrade xfce 4.10 to 4.8."
date: 2012-09-30
forum: Desktop Environments
---

### Post by UAdnan on 2012-09-30
Greetings,

I have Xubuntu 12.04 LTS on my computer, and wanted to give xfce 4.10 a try. I knew it was to be officially released in the 12.10 version and not recommended with 12.04, but there wasn't really something I had to care about.

Well but the testings aren't that great, the panel plugins are crashing often and the boot time has almost doubled since it's taking more time to get the environment loaded.

Is there any way to downgrade from xfce 4.10 to the previous one ? If so, please provide the necessary commands.

Thanks in advance,
UAdnan.

---

### Post by Frogs Hair on 2012-09-30
How did you install it ? If it was with a PPA check for a PPA purge where you found the PPA. I just installed 12.10 but was using the XFCE session in 12.04 and I'm not sure if 4.10 was in the 12.04 repository or not. _I'm not sure if reinstalling the the desktop would work._

```
sudo apt-get install --reinstall xubuntu-desktop
```

---

### Post by UAdnan on 2012-09-30
Well, I don't want to mess it up, here are the commands that I used to install it, nothing else :

```
[B] sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
 sudo apt-get update
 sudo apt-get dist-update[/B]
```

Can you help me more through the process ?

---

### Post by Frogs Hair on 2012-09-30
See the remove PPA section.[http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html](http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html)

---

### Post by UAdnan on 2012-10-09
That didn't work, I get the following error :

" Reinstallation of xubuntu-desktop is not possible, it cannot be downloaded. "

---

### Post by neu5eeCh on 2012-10-09
> **UAdnan said:**
> That didn't work, I get the following error :

" Reinstallation of xubuntu-desktop is not possible, it cannot be downloaded. "

Did you remove 4.10 before getting this message?

(As a side note, you problems with 4.10 sound like the exception to the rule. I use 4.10 and have had no difficulties on either of my systems; not that this information is helpful, but it *does* sound like you have issues unrelated to 4.10.)

---

### Post by UAdnan on 2012-10-15
> **VTPoet said:**
> Did you remove 4.10 before getting this message?

(As a side note, you problems with 4.10 sound like the exception to the rule. I use 4.10 and have had no difficulties on either of my systems; not that this information is helpful, but it *does* sound like you have issues unrelated to 4.10.)

This would sound quite stupid, but it's that I haven't removed it. Thanks.

---

