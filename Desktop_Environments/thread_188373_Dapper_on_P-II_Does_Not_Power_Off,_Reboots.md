---
title: "Dapper on P-II Does Not Power Off, Reboots"
date: 2006-06-04
forum: Desktop Environments
---

### Post by beeldings on 2006-06-04
Tonight, I installed Dapper on my parents old Gateway G6-400, a 400 MHz Pentium II with 6.4 GB HDD and 256 MB SDRAM. Set-up was a breeze, perhaps a bit longer than I was used to, but everything was detected and set-up properly. I noticed that when I attempted to shut off the PC (System > Quit > Shut Down), Dapper would run through the shut-down/log-off sequence until the "Will power down" sequence at which point I would hear the hard drive power down and the keyboard LEDs would flash, but the computer simply restarted as opposed to shutting down. This problem did not occur when this particular computer ran Ubuntu Warty through Breezy, it appears to be a Dapper-only problem.

The only thing I thought of was to pass "noacpi noapm" to the kernel through GRUB, but the problem still occurs. I also tried turning off the PC from the CLI as root using the "poweroff" command, but the problem persisted. I am able to manually turn the PC off by pushing the power button once I hear the hard drive power down, but I really don't want to leave that up to my parents. This is an older computer system, I believe it is seven or eight years old (perfect for my parents, they do simple internet surfing), and even after checking the power management settings in the BIOS, I am unable to determine what the source of this problem is. Does anyone have a solution (other than replacing the PSU or buying them a new computer)?

---

### Post by Peter76 on 2006-06-04
Hi, this is the third thread I see about this, a lot of people seem to have this problem... I posted a solution here: [http://www.ubuntuforums.org/showthread.php?t=187186](http://www.ubuntuforums.org/showthread.php?t=187186)

I'll ask somebody to make this a sticky thread.

Good luck

---

