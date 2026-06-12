---
title: "Help removing plymuth"
date: 2010-06-04
forum: Desktop Environments
---

### Post by bruno9779 on 2010-06-04
After looking everywhere for nvidia & low res boot, I am at a standstill.

My options are: 

1 - keep the default nice boot screen in hi-res, by not installing nvidia drivers. By doing this, I can use my TTYs and have a nice boot, but I must give up compiz and 3d HW acceleration.

2 - Install the nvidia drivers, and have an awful boot screen and TTYs with huge font. At least compiz and 3d work

3 - After installing the nvidia drivers I edit 2 grub files to force a different resolution. 
Compiz works, boot is a bit better (decent res, but it only flashes on screen for 2 sec), 3d acceleration.
Now the TTYs are gone. (I have read about framebuffer issue with this workaround)


well, none of this options is good for me, so I am thinking to remove plymouth altogether.

Any help or advice is appreciated

---

### Post by QIII on 2010-06-04
At this point, I think that plymouth is integral.  You'd probably bork things trying to remove it.

Think of it this way...

If you keep your drivers so that things are nice when you are actually using your machine, why is it such a problem to have something look ugly for 5 seconds when you boot?

Plymouth looked slick the first time it ran before I installed my video driver.  ATI, nVidia?  No difference.  They suffer from the same behavior.

Plymouth is up and gone on my machine before my hand reaches the soda can.  

It may be a pain twisting yourself into a Ferrari.  But once you are driving it do you really give a crap?

I'm sure this will eventually be worked out and we can all be excited by 5 seconds of really cool graphics on boot.

---

### Post by bruno9779 on 2010-06-04
the problem is, that since 10.04 it has been more 35s (nvidia) than 5s(first boot). And I would really like higher res on the TTys

---

### Post by QIII on 2010-06-04
I get boot times of between 16 and 18 seconds to full desktop.  

If you are having that sort of delay just to get through the plymouth splash, something is definitely wrong.

It might be worth a peek at launchpad to see if there is something enlightening there.  I'll try to go back through some threads I've seen regarding slow performance like that and see if I can find something to help.

---

