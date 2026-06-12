---
title: "Since Gutsy upgrade: what _old_ ATI driver to use to enable Compiz"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by blazko on 2008-01-06
Hello all,

I am going nuts. I own an IBM Thinkpad R50 with a native screen resolution of 1400x1050 pixels. In Feisty I got a compiz setup working when using the open source driver and 16 bit colour depth.

After upgrade to Gutsy, my screen froze (X startup: black screen). So I tried around with all modules available, and it already was extremely hard to get X working in 800x600 and now even 1400x1050.

Now I managed to get it working, but like to have my Compiz back. Problem is, that for my built-in ATI there seems to be no actual driver available and most discussions here are about supported chips or the people have other setups.

Last i tried is add some ServerFlags in xorg.conf and to install xserver-xgl, but then X freeze again, so I had to remove that package again.

According to lspci I have this card:
"ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)"

so, is this a Radeon, a mobility, a FireGL? This is amking me nuts. Playing around with the "ati", "radeon" and "fglrx" driver (last should not work at all) helps nothing.

I would not have opened this thread, but in all these other threads I cannot find solutions or find information that is not fitting to my setup r applies to an older Ubuntu release, where I got it working though.

So, what driver do I have to use, what libs or Ubuntu/packages do I have to use for my outdated setup?

Thanks and regards,
Timo

---

### Post by Ub1476 on 2008-01-06
[Post #18]("http://ubuntuforums.org/showthread.php?t=550082&highlight=Gutsy+ATI+R250&page=2")

---

### Post by blazko on 2008-01-07
Hi,

okay, so it seems I have to reinstall Gutsy. According to Synaptic I have libmesa-dir and -glx installed which seems to be wrong. However, I these would have to be replaced by what? This is because I think mesa is the only alternative to the original ATI ones which do not work for my old chipset? I am a bit clueless. ;)

Thanks and kind regards,
Timo

---

