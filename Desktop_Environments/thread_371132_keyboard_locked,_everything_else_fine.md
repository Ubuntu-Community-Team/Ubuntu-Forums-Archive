---
title: "keyboard locked, everything else fine"
date: 2007-02-26
forum: Desktop Environments
---

### Post by niais77 on 2007-02-26
My new edgy install has been repeatedly and randomly losing it's grip on my keyboard.
Everything else works fine, I can surf the web, hear music, anything so long as it doesn't require my keyboard.

After weeks of trying to correlate this loss of grip to one paricular event/keystroke/process I am still stumped.
I set up a redirect of my .xsessions-errors file to capture this error output.

kdesktop: WARNING: LockProcess::startSaver() grabInput() failed!!!!

Once this error is thrown, the keyboard is dead in the water until I restart X (using only the mouse) or reboot the machine.  If I had an existing session on say TTY1, I can use the switch session option under the k-menu to switch over there at which location the keyboard works fine.  So the problem only exists within X and is not system-wide.

I've been unable to find anything about this on the web.

This is on an AMD64 machine with 
kernel: 2.6.17-11-generic #2 SMP 
ii  xserver-xorg                               7.1.1ubuntu6.2                       the X.Org X server


Anyone ever seen anything like this?

Any thoughts appreciated
TIA

---

### Post by lhtown on 2007-02-26
Could I suggest that maybe your keyboard or keyboard cable is going bad?

If your keyboard is a really weird one, if you told us the model, perhaps that would shed some light on the situation.

Also, how does your keyboard connect? PS/2 or usb? If it is USB, I would tend to think it is a USB problem.

---

### Post by niais77 on 2007-02-28
Thanks for the reply.
That's a good thought but I failed to mention that I had tried several different keyboards.
Both ps2 and usb.
Same results with each one individually or with all of them plugged in at once.

---

