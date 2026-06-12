---
title: "Using Ubuntu Live CD and PISSED."
date: 2009-03-01
forum: General Help
---

### Post by noseforsharpies on 2009-03-01
Here we go, in simple terms:

1. Computer overheats constantly, then shuts off.

2. Running Ubuntu 8.10 as operating system.

3. After restarting computer, Ubuntu goes into automatic file-check.

4. Automatic file-check fails, tells me to do manual file-check.

5. I do manual file-check. Lasts forever, thus shutting off PC from heat.

6. Could explain hard-disk issues, but won't. What I really want to know is..

7. Is there a way to avoid file-checks? Remember, I'm using Live CD and can't make changes to the OS through that. I think. I'm missing Windows right now, ONLY because I can avoid the checks. I can't access my operating system. 

Thanks.

---

### Post by jwbrase on 2009-03-01
As far as the overheating, probably a hardware issue. First thing to do from that end is to open up the case and see how much dust is in there. It may be worth vacuuming out. (Be sure to take anti-static precautions any time you open up the case, of course).

As far as avoiding the file checks: If you're using the live CD, and don't have Ubuntu installed to the hard disk, you should be able to simply remove the CD from the drive. Or you could go into setup (Generally some key like ESC, F2, F12, or Del. at the manufacturer's splash screen) and change the boot order so that it boots from the hard drive before the CD. That will stop it booting to Ubuntu. After that, it should boot to Windows unless something is really screwed up. (If you're having overheating problems, though, Windows is likely to end up overheating too, and the amount of time it takes will probably be similar).

---

### Post by Acetertrix on 2009-03-01
The problem with overheating is some laptops like my Aspire 3620 needs some HD space for the BIOS to store commands like fan speed etc, as soon as I format my HD I know I have about 30-40 mins befor it overheats, once HD is formatted and OS is installed fan speeds are normal and controlled. So the problem with his install is the fan isn't actually running at top speed if at all until the os is in, he needs to speed up the install. And disk checking actually overheats the system 10x faster. Best bet, well for me.. I partition and format (STOP) shut it down. Thebn after it completely cools, do the install, when I break up this into 2 stages HD Prep then OS Install it works ok. This is not specific to Ubuntu, it happens with Windows, its a design flaw with the hardware.

With Windows and Ubuntu they may be conflicting with your Bios and interupting the fan temp's and speed controls. There is a sure fix but its costly.

If you create unallocated space like 36-40 MB at the beginning of the HD for the BIOS to use, it resolves the overheat and fan issues.

---

### Post by Xiong Chiamiov on 2009-03-01
The newer releases of Ubuntu allow you to skip fscking by pressing escape.  I don't know if that's implemented in the live cd, though.

Don't do the manual fsck if you know it's not going to help you, and just take more time and cause more overheating.

---

