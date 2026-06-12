---
title: "KDE crashes machine before login when using SMP kernel"
date: 2005-07-22
forum: Desktop Environments
---

### Post by TheSerpent on 2005-07-22
Hi all

First post, new to Linux but learning fast - go easy, OK!?

I have a home-brew machine with two AMD Athlon MP 2000 CPUs in it. They work happily together in a certain O/S that will not be mentioned here!

I can happily run Hoary on kernel image 2.6.10-5-k7 with KDE 3.4.0

However if I boot using kernel image 2.6.10-5-k7-smp to get my second cpu into action, KDE freezes the machine unrecoverably just before the login prompt. X starts OK and I see my background appear but the machine locks just before the login prompt screen appears.
If I switch to a different tty before KDE crashes, the machine functions perfectly. I can log on and use the command line forever. As soon as I switch to tty7, on go the brakes.

I have tried looking at KDE logs but nothing appears amiss, it just stops running - it is highly likely that I am looking in the wrong place though!

Rather than post pointless info I'd like to know what logs I should retrieve to help find the bug. Or if anyone has solved this before, well, that would be great too!

Thanks in advance

---

### Post by Ptero-4 on 2005-07-23
[QUOTE=TheSerpent]Hi all

First post, new to Linux but learning fast - go easy, OK!?

I have a home-brew machine with two AMD Athlon MP 2000 CPUs in it. They work happily together in a certain O/S that will not be mentioned here!

I can happily run Hoary on kernel image 2.6.10-5-k7 with KDE 3.4.0

However if I boot using kernel image 2.6.10-5-k7-smp to get my second cpu into action, KDE freezes the machine unrecoverably just before the login prompt. X starts OK and I see my background appear but the machine locks just before the login prompt screen appears.
If I switch to a different tty before KDE crashes, the machine functions perfectly. I can log on and use the command line forever. As soon as I switch to tty7, on go the brakes.

I have tried looking at KDE logs but nothing appears amiss, it just stops running - it is highly likely that I am looking in the wrong place though!

Rather than post pointless info I'd like to know what logs I should retrieve to help find the bug. Or if anyone has solved this before, well, that would be great too!

Thanks in advance[/QUOTE]

Try with "sudo /etc/init.d/kdm stop" from a tty (pther than tty7 off-course) and then type "startx" and go to tty7. Tell us if it works.

---

### Post by TheSerpent on 2005-07-23
[QUOTE=Ptero-4]Try with "sudo /etc/init.d/kdm stop" from a tty (pther than tty7 off-course) and then type "startx" and go to tty7. Tell us if it works.[/QUOTE]


Thanks for the suggestion Ptero

I switched to tty1 as soon as I was able and entered your suggested command. KDM stopped OK.
I then ran startx, which caused the same problem as I described before, only this time without the background image - just a white background with pointer, then total freeze up. I can't return to another tty only cycle the power, just like with KDM.

Further suggestions much appreciated!

---

### Post by TheSerpent on 2005-07-25
Bumped 7/25, apologies but still having problems

---

### Post by TheSerpent on 2005-07-26
Perhaps a hint about where to look?
If it doesn't seem to be KDE specific, would /var/log/Xorg.0.log or .old be a good place to start?

---

### Post by pioni on 2005-07-31
[QUOTE=TheSerpent]I have a home-brew machine with two AMD Athlon MP 2000 CPUs in it. They work happily together in a certain O/S that will not be mentioned here!

I can happily run Hoary on kernel image 2.6.10-5-k7 with KDE 3.4.0

However if I boot using kernel image 2.6.10-5-k7-smp to get my second cpu into action, KDE freezes the machine unrecoverably just before the login prompt. X starts OK and I see my background appear but the machine locks just before the login prompt screen appears.[/QUOTE]

I don't have a clue what might help, but decided to inform you that I have exactly the same problem here. I have dual Celeron which crashes with default Gnome setup. I've tried all SMP kernels found on the CD with no luck. Using single processor everything runs smoothly. That certain other OS works without problems (uhh, SMP related problems, that is). Both Fedora Core 4 and CentOS 4.1 seem to work with their default SMP kernel just fine.

Ubuntu SMP kernels must be just broken. I've removed everything except the essential stuff from my computer and it still doesn't work. I tried changing my Matrox display adapter to an old ATI, but that doesn't help either. I've mentioned this here before and some other people seem to have the same problem as well.

---

