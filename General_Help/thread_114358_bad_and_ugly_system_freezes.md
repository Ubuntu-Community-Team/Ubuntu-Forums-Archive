---
title: "bad and ugly system freezes"
date: 2006-01-08
forum: General Help
---

### Post by louis_nichols on 2006-01-08
Hi!

As you may have guessed from the subject, my system freezes. :( 

It allways happens when apps (gnomemeeting, kooka, kopete 3.5...) try to access the webcam  I have connected. The freeze is hopeless: no CTRL+ALT+anything, be it F1 or Fx or BCKSP. NOTHING. I have to do a hardware restart of the PC.

I am open on any suggestions on how to stop this from happening. I would hate to have to unplug the webcam everytime I boot Linux (I know I could try to not use the apps anymore, but sometimes I just click wrong :) ).

Or, even better, something to make my webcam work in Linux, so I won't need a reason to boot windoze anymore. In other distros I used spca5xx, but in ubuntu I can't compile it... where is the package for the 2.6.12 kernel source, anyway? LOL

=============================

I should mention that I have read all the threads I could find on the matter and positively ruled out other reasons, like the video driver, powernowd or RenderAccel in xorg.conf. And it might also be important that it used to happen the exact same way in Ubuntu.

---

### Post by stuporglue on 2006-01-08
You mean *this* spca5xx? :-) 

```
stuporglue@ubuntwo:~$ modprobe -l | grep spc
/lib/modules/2.6.15-11-386/kernel/drivers/usb/media/spca5xx/spca5xx.ko
```

I'm running dapper, but I'll bet it's there in Breezy too. To load it manually type

```
$ sudo modprobe spca5xx
```

and do that before you try to access it. If that works so that it doesn't freeze the system, you can edit /etc/modules and add spca5xx to the list to load at boot time.

---

### Post by louis_nichols on 2006-01-08
WOW! you're right!! I never thought it would be included in a distro. LOL, I guess I still have much to learn abut linux and the speed it moves at. :) 

but... what should I do about it? I'm afraid I'm more familiarized to modules in FreeBSD than Linux. I don't even know how to load a module, let alone configure it to use my webcam...

---

### Post by encompass on 2006-01-08
I have the flexi cam it says that it is on the support list... but nogo with your command...
> jason@lappy:~$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.12-10-686/kernel/drivers/usb/media/spca5xx.ko): Invalid module format
jason@lappy:~$

any ideas?
BTW It is nice to see someone of the same faith.  Rock'on man.

---

### Post by louis_nichols on 2006-01-08
well... my spca5xx loads without errors. But... the system still freezes when I try to access it. I tried spcaview, which I've used before in other distros without problems and I can't explain why this is happening in kubuntu and ubuntu. (this is not surprising, though, because, after more 1 year of Linux, I still feel like a newb and, with so much stuff out there, I really don't see myself more than this ever LOL :)  )

It's a shame though, because the webcam thing is one of only 2 reasons why I still boot windoze. And it's even more a shame now, that I feel so close, with kopete supporting webcam in yahoo messenger...

Any help? Anybody! PLEASE!!!!

---

### Post by tseliot on 2006-01-08
I had the same problem until I tried this guide: [http://ubuntuforums.org/showthread.php?t=75284]("http://ubuntuforums.org/showthread.php?t=75284")

Enjoy!

---

### Post by louis_nichols on 2006-01-08
you were right, man!! it did work!! THANK YOU VERY MUCH!! now I'm dying to test it, but I've been looking into this one for so long that everyone's gone to sleep by now. :)

---

### Post by chele on 2006-01-14
EasyCam [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") is a cool utility to update, download and build drivers for many webcams.

---

