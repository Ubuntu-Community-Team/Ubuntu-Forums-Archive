---
title: "VERY serious problem"
date: 2009-06-09
forum: General Help
---

### Post by papabill on 2009-06-09
I rebooted my Ubuntu machine 

HP Pavilion XE783 PC
Intel (R) Celeron 700 MHz processor
384MB/PC 100 RAM
Intel 810 chipset onboard video
running Hardy Heron

and the screen went patchy, and the entire box locked up. It's been running great for the last week, and the only changes I've made lately is to install Samba. A reboot was no help, it locked up again.

HELP!!!!

---

### Post by Tipped OuT on 2009-06-09
Have you tried going into recovery mode and reseting xorg back to default settings?

---

### Post by prshah on 2009-06-09
> **papabill said:**
> 
and the screen went patchy, and the entire box locked up. 

Doesn't seem to be a software problem; boot off a live CD to make sure.

Post back with details for more suggestions in either case.

---

### Post by papabill on 2009-06-09
> **Tipped OuT said:**
> Have you tried going into recovery mode and reseting xorg back to default settings?

VERY DUMB QUESTION (on my part): How do I get into recovery mode?

---

### Post by Kevbert on 2009-06-09
Can you boot up a Ubuntu CD and try and run memtest86+ from the boot menu ?
Check your monitor lead as well as any other interconnecting leads, they may be loose.

---

### Post by theo.ew on 2009-06-09
when you boot the computer it should give you an option to boot into recovery mode. It normally gives you a list of available options to boot off of.

---

### Post by yaroto98 on 2009-06-09
When you boot up GRUB should automatically try to boot normally, hit ESC while it's counting down from 3 to 0. Then select the Recover Console option.

---

### Post by Tipped OuT on 2009-06-09
Before it boots into Ubuntu (the black screen that has a countdown before it boots into Ubuntu), press the "esc" key and choose the recovery mode boot option. It should be something like "Ubuntu 8.04.2 (recovery mode)".

---

### Post by papabill on 2009-06-09
Let me see if I can answer all the questions:

> When you boot up GRUB should automatically try to boot normally, hit ESC while it's counting down from 3 to 0. Then select the Recover Console option.
Did that, went through the options one at a time (except for going into root), rebooted and still have patchy screen, frozen machine

> Can you boot up a Ubuntu CD and try and run memtest86+ from the boot menu ?
Check your monitor lead as well as any other interconnecting leads, they may be loose. 
Booted off a Ubuntu CD o.k, ran mentest 86+, it got to a spot where it says [ 54.888864]Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1). It stops, and the CAPS akd Scroll keys start flashing. Only way to make something happen is to reboot-back to same problem.
Monitor leads are fine

> Have you tried going into recovery mode and reseting xorg back to default settings? 
Yep, tried that

> Before it boots into Ubuntu (the black screen that has a countdown before it boots into Ubuntu), press the "esc" key and choose the recovery mode boot option. It should be something like "Ubuntu 8.04.2 (recovery mode)". 
Went through all options, nothing helped.

---

### Post by Ramza500 on 2009-06-09
Can you run the Live CD fine?  Because of what memtest86+ said I think you might have a bad area of RAM.

If you can run the Live CD just fine, open stuff up and play, then I'm probably wrong.

---

### Post by papabill on 2009-06-09
Come to think of it, this is the VERY same problem I had with Jaunty Jackalope. The screen went nuts and locked up the machine. I was told that the reason was because Jaunty didn't like Intel video chipsets.

---

### Post by papabill on 2009-06-09
Any ideas about how I can get the work off the machine that has been done in the last week and a half? Lots of hard work went into it, and I'd hate to lose it. At least windoze had the ability to go into in dos and save the contents. Does ubuntu?

Thanks

---

