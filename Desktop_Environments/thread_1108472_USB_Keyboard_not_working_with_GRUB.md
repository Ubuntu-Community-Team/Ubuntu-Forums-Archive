---
title: "USB Keyboard not working with GRUB"
date: 2009-03-27
forum: Desktop Environments
---

### Post by calisun on 2009-03-27
I have just installed Ubuntu 8.10 on a machine that already has XP installed on it. Installation went fine, after reboot, the system gives me a menu to choose to which system to boot to: Ubuntu or XP. But the USB keyboard does not work with that menu. I try up arrow down arrow, press enter, press all the keys, and nothing, the timer just counts down and system boots to Ubuntu.
Once the system boots up, the keyboard and mouse work fine. Even before boot, keyboard and mouse work fine in BIOS.
So at the moment I am unable to get into XP, which bites.

Any ideas on how to fix this?

---

### Post by VeeDubb on 2009-03-27
That's pretty odd.

I had read the title and came in to tell you that you needed to enable USB keyboard support in the bios, but if the keyboard is already working to enter the bios screen at post, that's almost certainly not it.

The only thing I could suggest, is still the same thing.  It's "possible" that your particular BIOS has some basic default USB input support, but that enabling full USB keyboard support is a separate option in the BIOS.  

If that's the case, it would explain why you can't use the keyboard for grub, since the linux keyboard drivers wouldn't take over until the kernel was loaded.

---

### Post by zhocchao on 2009-03-27
I had the same problem. Try a different USB or the PS/2 Port. (It could be helpful playing with legacy USB support in Bios)

---

### Post by calisun on 2009-03-27
Thank you guys, that was it, I enabled legacy USB support in bios and now it works fine. 
Thanks.

---

### Post by AjitDingankar on 2012-05-13
> **calisun said:**
> Thank you guys, that was it, I enabled legacy USB support in bios and now it works fine. 


How did you enable USB support in BIOS? 
Is there a way to do this after booting into Ubuntu? 

My Dell XPS 400 does not have PS-2 ports for keyboard/mouse, 
and the USB keyboard failure prevents me from using any Function 
keys to get into BIOS set-up! :-( 

Thanks in advance! 
Ajit 
====

---

