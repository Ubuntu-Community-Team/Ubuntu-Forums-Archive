---
title: "3D acceleration only works on warm T22 thinkpad!?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by ted209 on 2005-10-26
I have bizarre problem on my thinkpad T22. I installed DRI drivers for savage 3D acceleration as described here:
[http://www.ubuntuforums.org/showthread.php?t=75393](http://www.ubuntuforums.org/showthread.php?t=75393)
it works fine and planetpenguin-racer is nice and fast, BUT it only works when the laptop is warm!  If I boot up from cold, it takes 2 attempts to get ubuntu loaded up.

What happens is: everything loads up as normal, but right before the login screen appears, the screen freezes on a single cursor in the top right corner. Ubuntu hasn't crashed, because I can log in or reboot (without being able to see the screen).

Can anyone help diagnose the problem?  I know it is related to 3D acceleration, because I don't get the problem unless these drivers are installed.  I've had a look in my xorg.0.log files and I can't find any obvious clues there. This is quite infuriating and I would really appreciate any help with this problem.

P.S.  I'm writing a blog on my experiences with ubuntu on the T22, which I intent to post as a HOWTO when I'm done: [http://ubuntuthinkpad.blogspot.com/](http://ubuntuthinkpad.blogspot.com/)

---

### Post by gillion on 2005-10-26
Have you tried starting the machine from cold boot with ACPI turned off ?

It could be that your ACPI settings are causing the system to behave funny (i have seen weirder things)

You might also want to look into the cpu scaling.

---

### Post by ted209 on 2005-10-26
I already have ACPI turned off - I have also tried disabling APM, but no luck. I have also tried turning off cpu frequency scaling in ubuntu and in the BIOS.

Another problem is that *sometimes* my PCMCIA wireless network card does not initialize.

I don't get it - computers aren't supposed to be random!!

Ed

---

### Post by patwack on 2007-02-09
this is happening me with feisty now, did you ever find a solution to the problem?

it worked fine in edgy and dapper

---

