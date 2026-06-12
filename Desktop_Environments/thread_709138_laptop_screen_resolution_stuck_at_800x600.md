---
title: "laptop screen resolution stuck at 800x600"
date: 2008-02-27
forum: Desktop Environments
---

### Post by sgleason on 2008-02-27
Hello all,

My first post ever, I hope it makes sense. 

I have an IBM ThinkPad laptop T41, and initially everything was fine.  Then I tried to connect to an external monitor and everything went to hell.  when I reverted back to the laptop screen I was stuck in 800x600 resolution mode, with no options to fix it under System->Preferences->Screen Resolution.  I've tried to follow several of the existing threads here with no luck.  I can't even figure out what my video card is and it will not auto detect. Under System->Preferences->Hardware Information I found nothing that resembled a video card. When I'm forced to use XP running on a second hard drive the resolution is fine.

Any ideas would be greatly appreciated.

-Scott

---

### Post by uberlube on 2008-02-27
Did you install your video drivers?

---

### Post by eldragon on 2008-02-27
considering the fact that you had your screen resolution working before, i would open a terminal and just do 
```

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_of_mine
$ sudo dpkg-reconfigure xserver-xorg

```

first line makes a backup (in case you bork things up with xorg, you can always log in through a terminal and copy it back and thus getting your desktop environment back.

second line will walk you through reconfiguring xorg.conf, you will be able to pick screen resolutions there.

---

### Post by sgleason on 2008-02-28
Thanks for the replies.  It turned out that going through the configuration manually gave me the options to fix the problem.  It's much easier on the eyes now :-). It also allowed me to change my keyboard setting from "us" to "gb" which fixed a bit of strangeness on some of the side keys.

Much appreciated.

-Scott

---

