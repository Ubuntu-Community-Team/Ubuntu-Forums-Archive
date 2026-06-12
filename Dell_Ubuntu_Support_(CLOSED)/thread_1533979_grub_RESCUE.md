---
title: "grub RESCUE ?????"
date: 2010-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by grahamz on 2010-07-18
ok. 

My previous thread was about installing ubuntu to a dell gx280 I did that...

On reboot I get 

error: file not found.
Grub rescue >  


I have researched the commands for grub but none of them work at all 

I am lost 

I have looked on the forums and people seem to be ignoring it ?? 

WHAT DO I DO ?

---

### Post by tuxsun on 2010-07-19
Not sure what file is missing; grub config file, grub menu file, kernel?

For GRUB2 Documention (from Ubuntu), visit:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Hold down the SHIFT key while machine is booting to get to the GRUB menu, then select a kernel that says (RECOVERY MODE) next to it, and try booting that. That will bring you to a GRUB menu with various choices: (Reconfigure GRUB, Fix broken packages, etc.), which may or may not fix your problem.  NOTE: You may have to scroll the GRUB2 Recovery menu to see all the choices!

When I was having GRUB problems, I too searched the Forums and, found messages saying to hit ESC on bootup, but that is for the original GRUB. GRUB2 docs say to use the SHIFT key, and that works great for me.


HTH

---

