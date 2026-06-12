---
title: "hangs on loading ubuntu"
date: 2007-09-24
forum: Desktop Environments
---

### Post by kaushis on 2007-09-24
Hi all,
 after booting from grub, the ubuntu(7.04) loading hangs. it hangs at the beginning itself. the status bar  doesnt move any further. it happens almost every 90% times of my boot. then i restart the PC. if im lucky, the ubuntu loads properly,  otherwise i again restart it. its very irritating.
any one can help me out?
thanks,
kaushik

---

### Post by rsambuca on 2007-09-24
Next time you boot up, select ubuntu at the grub screen and press 'e' to edit the entry.  Remove the words 'quiet' and 'splash' and then boot up.  If it hangs, write down what step it is hanging up at and maybe we can figure it out!

---

### Post by kaushis on 2007-09-25
i tried editing the grub. i deleted the line 'quiet'. but there was no line 'splash', but instead was 'saveDefault', which i deleted. but even then, the loading got stuck. i cudnt find any text messages or commands on the screen so that i can paste them here. all i got on the screen is again the status bar. 
is there any way i get in to the command line(text) details of ubuntu loading instead of the graphical status bar?

---

### Post by rsambuca on 2007-09-25
You took out the wrong line.  At the end of the 'kernel' line are the words that you have to delete in order to see the boot sequence and remove the status bar.

---

### Post by kaushis on 2007-10-06
here is the output im getting:

[COLOR="Red"]<there is something getting printed very quickly, some booting information>[/COLOR]
handlers:
Disabling IRQ #18 [COLOR="Red"]<it is waiting here for some time>[/COLOR]
Failed to set xfermode (errmask = 0x40)
Failed to recover some devices, retrying in 5 sec.
qc timeout (cmd 0x27)
ata_hpa_size 1: secors.
Failed to set xfermode (errmask = 0x40)
limiting speed to UDMA/100:p103
Failed to recover some devices, retrying in 5 sec. [COLOR="Red"]<waiting here for some time here>[/COLOR]
[COLOR="Red"]<some other lines>[/COLOR]
USB hub found
2 ports detected.
Done.
check root = booting cat /proc/cmdline 
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by -uvid/bab2bd23-848b-43a2-91c6-e2549892b797 does not exist.
Dropping to a shell!
BusyBox v.1.1.3 ... Built in shell
/bin/sh: Can't access tty; job control turned off
(initramfs)[COLOR="Red"]<command line prompt here>[/COLOR]

but all these things dont come or doesnt stop anywhere if the boot is normal. these lines are observed only when the boot hangs. why?:(:confused:

---

### Post by rsambuca on 2007-10-07
Sorry kaushis, I am of no help with these errors.  It is rather strange that they occur sometimes, and not others.  The only thing I can suggest is to check all of your cables and connections to make sure they aren't loose.  Hopefully someone else may be able to help you here.

---

### Post by alex77 on 2007-10-14
Sounds like one of your drives jumpers are not set correctly- i had a similar problem to this.

Check that ur drives are jumpreed master/slave correctly. For example- my dvd was the only drive on the cable, but i had it set to slave. Windows ignored this, but it caused my ubuntu to hang at boot. Changing the jumper setting sorted this.

---

