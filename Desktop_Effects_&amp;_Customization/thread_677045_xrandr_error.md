---
title: "xrandr error"
date: 2008-01-24
forum: Desktop Effects &amp; Customization
---

### Post by this is not kasker on 2008-01-24
Same problem in this closed thread.
[http://ubuntuforums.org/showthread.php?t=571366](http://ubuntuforums.org/showthread.php?t=571366)



 I've searched and it doesn't seem like anybody knows much about xrandr. I'd been messing around with it for a few days then all the sudden my graphics card renders really slow and choppy, it's impossible to get dual monitors working, and this is only under ubuntu. All my hardware is fine. It was caused by xrandr. I've reset the xorg.conf file and started everything from scratch (that I know of) apart from reinstalling ubuntu. Any attempt to use xrandr other than getting the command list shows this error.

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9

I've got an ATI 9800XT.

---

### Post by staeryatz on 2008-01-25
I am getting the exact same thing. Using gutsy, Radeon X1100 with fglrx driver and compiz fusion is enabled. I am also getting core dumps every time I run aticonfig...

---

### Post by chooseopen on 2008-02-29
I am having the exact same problem in Gutsy with an Nvidia card.  

-Jason

---

