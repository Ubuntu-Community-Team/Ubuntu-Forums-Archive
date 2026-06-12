---
title: "No shutdown/reboot possible (nonsense characters on screen +freeze) 9.10"
date: 2009-11-14
forum: Desktop Environments
---

### Post by SiarAneas on 2009-11-14
Hi everyone!
I can't shutdown/reboot 9.10 at all!

As soon as I click on shutdown/reboot (doesn't matter wether after login or on the login page) the screen flickers, turns black and then some nonsenes characters are shown (see picture attached!)
The same when I shutdown from console (CTRL-ALT-F1)!

As soon as the system "freezes" like this I can't do anything at all (even CTRL-ALT-F1...) doesn't work.

I have to press the power button for ~5 seconds then to turn off my laptop. When I do this, you can hear that the hardisk was'nt in parking position by then, so I suppose the shutdown failed!

Any ideas?? Please help!

Thank you so much!

---

### Post by Kilz on 2009-11-14
Sounds like a driver problem, what video card do you have , and what drivers are you using for it?

---

### Post by SiarAneas on 2009-11-14
Hi!
Thanks for your quick reply :)

It's an
ATI Mobility Radeon X2300 

I didn't install any (additional) drivers, just used the ones that were installed!
Everything else is fine (Compiz and desktop effects work fine).

Have you got any idea?

Cheers,

SiarAneas

---

### Post by Bakudan00 on 2009-11-27
I just installed 9.10 yesterday in a dual boot with Win 7 and have the same problem, sort of. On logout or shutdown the screen goes black and flickery, and displays this:

Ubuntu 9.10 eric-laptop tty1
login:
password:

The keyboard is only half responsive but I managed fill in the first field before it wouldn't display anything I type at all. I have to shutdown via the power switch, and I'm typing this in Win because I'm afraid I might be doing damage that way.

I have a ATI Radeon HD 3200 graphics.

---

### Post by SiarAneas on 2009-11-28
Hi Bakudan!

Your problem seems to be a different issue!
It seems that your x-server (so the graphical interface "your desktop") crashes and you go back to the virtual-console.
>Ubuntu 9.10 eric-laptop tty1
 >login:
 >password:
Try to login there with your username/password (as you would do on the graphical log-in screen) and then type
sudo shutdown -h now
This will shutdown your computer properly so you don't have to power off manually (which can be indeed, as you said, dangerous for your computer!)

I've filed my bug here: There you will also find a work-around that worked well for me!
Just have a look:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/483036](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/483036)

Best regards,

SiarAneas

---

### Post by Bakudan00 on 2009-11-29
On the second day it stopped doing that for some reason, and it hasn't done it again since. Perhaps some updates fixed the problem?

Thanks for your help anyway. :D

---

### Post by sdanesino on 2009-11-29
I have the same problem on a laptop (Samsung). The screen becomes black with white slashes in it. I hadn't that problem using 9.04, the problem started when I upgraded to 9.10. I tried to solve the problem changing /etc/rc6.d/S40umountfs as follows: 
fstab-decode umount -r -d $WEAK_MTPTS
but nothing.
Could you please help me?
Thanks
Sophia

---

