---
title: "X GUI catastrofic action!"
date: 2006-03-09
forum: Desktop Environments
---

### Post by juliodj on 2006-03-09
I install a new hardware to my computer and read on Ubuntu support/faq page the following :

[I]Hardware detection

How do I rerun hardware detection (prob/probing/re-probe)?

During second stage install Ubuntu probes your hardware and sets up X. If you change your Video Card, Sound Card or even Monitor, you may need to redo this.

This can be done with:- '**apt-get --purge remove xserver-xfree86**' [/I]

Now I am unable to restart Ubuntu. It gives me a message telling my that X is not present. I tried to reinstall the program from the CD using the 'rescue' command on prompt without success.

How can I solve this problem without losing all my documents? I have dual-boot with Windows Me.

---

### Post by zAo on 2006-03-09
Try to boot to a console (either rescue or not) and run:
```
sudo apt-get install xserver-xorg
sudo gdm
```

---

