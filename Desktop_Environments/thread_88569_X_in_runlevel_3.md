---
title: "X in runlevel 3?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by PascalGR on 2005-11-10
Hi all,

I tried to install the nvidia drivers by moving to runlevel 3, but I realized that X are keep running! :o Is that natural???

I found BUM to edit the runlevels and set X to run only on level 5 (and not from 3) but before applying the new configuration I want to ask if it has any drawbacks. I don't wanna break anything ;)

Thanks

---

### Post by Joe_lurker on 2005-11-10
I wouldn't use any unsupported tool to edit the run levels.  Try booting into single user mode for the install instead.  The default install using GRUB should have made a menu entry for 'failsafe' I believe.  That should put you in single user mode and no X.  Ubuntu only has two runlevels.  Every run level is the same except for 1 (and 6 to be technical).

I am unhappy with the way the run levels are set up in Ubuntu and that lack of a "expert" sys-v editing tool for modifying the run levers.  There is a tool in the repository in Universe called "sysv-rc-config" - I think.  I used that with some success.  I guess the service editor has an export mode that is not exposed.

-Joe

---

### Post by PascalGR on 2005-11-11
That's what I'm gonna do.

Thanks for the help ;)

P.S.: The runlevels in Ubuntu suck :(

---

