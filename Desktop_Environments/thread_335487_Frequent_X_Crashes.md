---
title: "Frequent X Crashes"
date: 2007-01-10
forum: Desktop Environments
---

### Post by bloodniece on 2007-01-10
X is locking up and freezing sometimes 8 to 10 times a day.  I'm not sure what I need to do to fix this.

Using ATI driver 8.32.05 on a RADEON 9550 Generic

Lockups happen randomly and seem to be app-independent.  When it locks up I cannot ctrl+alt+backspace to restart X.  The only thing that works is killing the power and restarting.

Xorg log file is attached to this post.

thanks

](*,)

---

### Post by cirocco on 2007-01-13
Hi.
   I have similar (the same?) problem, but X freezes always when starting. (it was random when started from live-cd) 
  For now I know that X starts and runs OK (but slower) without xorg.conf file. I am looking for a better solution..

---

### Post by mysticmarks on 2007-01-15
not just ati. this is reported through many forum under many topics. search for freeze in threads.

---

### Post by bloodniece on 2007-01-16
Thanks

---

### Post by lukew on 2007-01-16
I was getting hard frezzes ( no key strokes could fix it ) when using ndswrapper.

I use eth0 or if i am desperate for wireless (can not be bothered to drag the wire accross the house ) I use a differnt wifi card which did not need to use ndswrapper.

Now I can honestly say....... I am back to being solid as a rock!!!

I knew my problem was ndswrapper because after the last upgrade 6 months ago, it was the first time my old usb wifi card was picked up in lsusb, was the first time i started getting these hard locks.

I got confirmation when i ran fsck in init 2; gave me an errot to the terminal about bug in ndswrapper and then men tioning hard frezze. Strange as I never had any mentions in any logs before.

I hope this helps.

Luke

---

### Post by cirocco on 2007-02-06
In my case it was definitely ati server, after commenting out
Load    "dri"
in xorg.conf it works.

---

