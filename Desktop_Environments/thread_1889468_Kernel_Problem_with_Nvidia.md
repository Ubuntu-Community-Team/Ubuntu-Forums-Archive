---
title: "Kernel Problem with Nvidia"
date: 2011-12-01
forum: Desktop Environments
---

### Post by joe carolan on 2011-12-01
Oneiric graphics problem with latest kernel 3.0.0-13 and Nvidia geoforce gt520
After upgrading my graphics on my old desktop computer that has an INTEL  D102GGC2 Motherboard with a Pentium processor 3.4ghz  and ATI express  200 on board graphics with a ..NVIDIA Geoforce GT520  pci card,  my  computer would no longer boot, Prior to adding the NVIDIA card to  improve my graphics, I was successfully running ONEIRIC with the  3.0.0-13 kernel provided I loaded ACPI=off in the Grub con-fig file.  with the on- board ATI graphics.
 After a lot of experimenting I can now run ONEIRIC with the GT520 card  provided I stay with the previous kernel 2.6.38-13-generic.although I  now need to boot with NOAPIC in the grub config (acpi=off is not now  required with the GT520 card) I am also running this 2.6.38-13 kernel  with the latest NVIDIA driver 290.10.loaded.
If I allow the Kernel to be upgraded  any Version 3 Kernel or if  the  headers are upgraded by the driver to version 3 my desktop, no longer  boots..""
Can I compile version 3 kernel with 2.6.38 headers ?. How would I do  this ?. or should I just stay with the older Kernel.  or am I missing  some step that i should implement.
I have read a lot of MAFoElffen posts that are very helpful.

---

### Post by BC59 on 2011-12-01
Did you try to boot using the old kernel?

---

### Post by joe carolan on 2011-12-01
I obviously did not put my post across very well if you are asking me this. I've been the whole nine yards before I could recover my system. I actually  got the desktop to boot on the newer kernel "I left it on by mistake and it booted after 12-15 MINS although it ran like a snail.
Oneiric live cd also won't  boot, natty live CD is fine. obviously the compilation of the headers on the new kernel is crashing the computer.

---

### Post by efflandt on 2011-12-01
If you compile your own kernel you would not use older headers (as far as I know) but you can compile it with options and modules specific to your hardware, which could make it boot and run better with possibly less memory footprint.

I used to do that regularly back in the mid-1990's w/386DX33 later hopped up with Cyrix 486DrX2/66, 387 math co-processor and a board so I could do LBA to use my 540 MB drive with a BIOS that only supported 528 MB max drive without LBA.  But I have not done that for many years and not with Ubuntu.

If you install source files for kernel and nvidia, they would end up in a directories in /usr/src and you would go to the appropriate linux version dir there to sudo config and make.  Not sure if you need any other packages to compile a kernel.  But there would probably be a readme file in the linux directory to tell you what to do and various configure options.

Does your CMOS setup (from BIOS splash screen) have any setting to disable your onboard video or does it automatically recognize when you add a video card?  And are you sure that your PSU (power supply) has enough power for an added video card?  Back in 2004 I had an HP PC that would not even boot when I swapped in a better video card.  Apparently its overrated 250 watt PSU could not handle a load that was 125-130 watts measured at the wall outlet once I switched to a conservatively rated 330 watt PSU.

I had trouble with my GT 430 in 11.10 even though it usually worked fine in Maverick with newest x-swat drivers, but it was an off-brand (Galaxie) and I think it was having hardware issues because it began freezing and doing strange graphics in Win7 before that. Maybe the Unity/compiz graphics are more taxing than gnome. The EVGA GTX 550 Ti I got to replace it works great.

---

### Post by joe carolan on 2011-12-02
The Nvidia GT 520 card was automatically recognized in win7 when I *added the card the* video to my computer. and is obviously recognized by the 2.6 kernel Your comments about selecting configuration options specific to my computer in the  Linux version directory sounds interesting. can anyone expand ?
Maybe i need to get the kernel log file from the boot up but I am not sure how to do this.

---

### Post by efflandt on 2011-12-02
Log files are in /var/log.


[LIST]
[*]**syslog** is system logs with time stamp
[*]**dmesg** marks things it logs with time since boot.  You can see current dmesg anywhere by doing **dmesg | less** or the end of it by just doing **dmesg** in a terminal
[*]**Xorg.0.log** is most recent log of X
[/LIST]

---

