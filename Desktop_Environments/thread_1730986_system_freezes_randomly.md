---
title: "system freezes randomly"
date: 2011-04-16
forum: Desktop Environments
---

### Post by undomiel25 on 2011-04-16
Hi!
I have just installed xubuntu 10.10 on an old desktop computer, a Packard Bell with AMD Athlon 64 3400+ 2200MHz and 512 MB of ram.
I did install the variant for AMD64. 

The problem is it freezes at random times. Sometimes it goes back to log in but it won't let me in, other times the screen and mouse simply freeze. I tried to monitor RAM and CPU usage, but it doesn't seem to overload before freezing. I can have several applications open or none at all, it doesn't seem to make a difference.   ](*,)

Do you guys think it's an hardware incompatibility? Should I give up and try another distro??

I'm not an expert user, and I would appreciate any kind of help!
Thanks a lot!

---

### Post by dumplingz on 2011-04-16
yes, this happens to me as well.  My computer has 10.10 ubuntu and its a laptop  Intel Dual Core 2.4GHz  4GB RAM   ATi 5450 512MB and has 250GB HDD. Mine did exactly same as yours but i fixed mine by improving the cooling. I bought better cooling pad and soon after that it works fine.   You should upgrade your ram because no one uses 512MB these days and upgrade your cooling system.

Ta :)

---

### Post by K_45 on 2011-04-16
I'd open up the system and clean out the dust with compressed air, then run Memtest and a drive fitness test to see if there is anything wrong with the hardware. Memtest is here:

[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

You want the pre-compiled in the .gz file. Download it, then open up a terminal:

```
gunzip memtest86+-4.20.iso.gz
```

then open up Brasero and burn the .iso. For the DFT:

[http://www.hitachigst.com/support/downloads/](http://www.hitachigst.com/support/downloads/)

and burn the .iso with Brasero. Reboot and test.

---

### Post by Jagoly on 2011-04-17
> **K_45 said:**
> I'd open up the system and clean out the dust with compressed air, then run Memtest and a drive fitness test to see if there is anything wrong with the hardware. Memtest is here:

[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

You want the pre-compiled in the .gz file. Download it, then open up a terminal:

```
gunzip memtest86+-4.20.iso.gz
```

then open up Brasero and burn the .iso. For the DFT:

[http://www.hitachigst.com/support/downloads/](http://www.hitachigst.com/support/downloads/)

and burn the .iso with Brasero. Reboot and test.

Doesn't memtest get installed with ubuntu and xubuntu? Also @dumplingz 512mb is fine for xubuntu. I can't image why you would need more.

@OP: It would be a good idea to do a complete system update (if you havn't already). I had this problem on my old dell aswell. Updating to he latest kernel fixed the problem.

PS: does the system freeze in failsafeX? (on ubuntu: in grub choose recovery mode->failsafe graphic mode->just one session
I imagine xubuntu would be the same.

Hope I helped!

---

### Post by K_45 on 2011-04-17
> **Jagoly said:**
> Doesn't memtest get installed with ubuntu and xubuntu? Also @dumplingz 512mb is fine for xubuntu. I can't image why you would need more.

@OP: It would be a good idea to do a complete system update (if you havn't already). I had this problem on my old dell aswell. Updating to he latest kernel fixed the problem.

PS: does the system freeze in failsafeX? (on ubuntu: in grub choose recovery mode->failsafe graphic mode->just one session
I imagine xubuntu would be the same.

Hope I helped!

It is, but I always run it as a live CD.

---

### Post by Dutch70 on 2011-04-17
What graphics card do you have? If you're not sure, post the output of...
```
sudo lspci | grep VGA
```

---

### Post by undomiel25 on 2011-04-17
@K_45: I ran Memtest from the boot menu and it was passed with no problems found.

@Jagoly: The system seems stable in safe graphic mode...

@Dutch70: My graphic card is an ATI Radeon Xpress 200 G Series. I probably should have updated the driver before asking...:oops:

Driver updated. It seems to be running smoothly now.
I think that was the problem.
Thank you all so much for helping!

---

### Post by Dutch70 on 2011-04-17
Great! let's hope it stays that way. I'd give it a little time to be sure before marking this thread as "Solved".

---

### Post by undomiel25 on 2011-04-23
Er... I'm afraid the problem is still there.
It freezes less often, but the system is still unstable.

I also noticed it said "too much work for irq20" a couple of times on startup. I don't even know what irq20 is...

If you guys think I should update the kernel, I will. If you know a good guide to do that I would appreciate a link.

Thanks again!

---

### Post by K_45 on 2011-04-23
I'd enter the BIOS and disable any unused ports like serial and parallel and the floppy drive. IRQ's are interrupt request lines, where a device can request attention, so to speak, by raising an interrupt, except that there a limited number of interrupts to go around.

---

### Post by d3v1150m471c on 2011-04-23
could be the kernel. try booting into an older one if you have one by holding shift at boot and selecting it. if not, you could try upgrading to a new one.
I ran into similar issues with kernel 2.6.32-30 and using a different kernel resolved the issue.

---

### Post by undomiel25 on 2011-04-25
I updated the kernel to 2.6.38.4, the system was even more unstable so I went back to the previous one (.35).

I tried to figure out what was using irq20 and by typing cat /proc/interrupts it says eth0 and serial are using it. I went in the Bios and disabled floppy and serial devices.

The computer is still acting weird, now I also noticed problems with USB, sometimes it won't let me copy files on them. Mount/unmount does nothing, I have to reboot to make it work.

I'm really losing my patience... ](*,)

If anyone has any other suggestion I'll try it.

---

