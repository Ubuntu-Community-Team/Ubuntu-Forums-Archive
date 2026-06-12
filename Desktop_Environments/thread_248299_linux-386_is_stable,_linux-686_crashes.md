---
title: "linux-386 is stable, linux-686 crashes"
date: 2006-08-31
forum: Desktop Environments
---

### Post by kewldude606 on 2006-08-31
I have a Pentium 4 (2.4Ghz, 800MHz FSB, if it matters) and I read that doing sudo apt-get install linux-686 will increase system performance with no bad side effects by enable SSE or something.

So I did that, except I used sudo aptitude install linux-686.  Now my system is very unstable, crashing within 2 minutes after boot.  When I tell GRUB to use 386, it is rock solid.

So should I just stick with the 386 or is there some easy way to fix the 686?

---

### Post by DigitalAxis on 2006-08-31
Well, for now I'd say yes; stick with linux-386.  Not crashing is preferable to speed any day of the week.

The only thing that comes to my mind are kernel modules.  
Supposedly if the modules are compiled for a different kernel, things can be unstable.  
Do you, perchance, use linux-restricted-modules (like nVidia or ATI graphics drivers), and did aptitude install a 686 restricted module to go with your new 686 kernel?  I'm not saying that's definitely why you've got crashing, but making sure you have matching version and CPU type probably couldn't hurt.

---

### Post by kewldude606 on 2006-09-01
I have linux-restricted-modules-386 and -686 installed.

---

