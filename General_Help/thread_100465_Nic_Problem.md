---
title: "Nic Problem"
date: 2005-12-07
forum: General Help
---

### Post by vleger on 2005-12-07
Hey, i have ubuntu 5.10 on a toshiba saellite m45-s351 and have a nic MArvel Yukon , but linux doesn't detect. What can i do, because i can't find the drivers neither.

LEger.

---

### Post by aclaunch on 2005-12-07
Google around and try to find the actual chipset used in your NIC. Linux supports a fair number of cards directly and several others with "ndiswrapper" which allows you to use the Windows driver (I don't know much about ndiswrapper, but you can Google that too). Once you know the chipset, you can determine what kernel module (driver) that you need.

Good Luck
Alan

Edit: I just checked, it seems to use the "sk98lin" module. Do a "sudo modprobe sk98lin" and report back.

---

### Post by vleger on 2005-12-08
i did what you told me. 
as root "modprobe sk98lin"
FATAL: Module SK98lin not found

---

### Post by aclaunch on 2005-12-08
Several things come to mind: see if you see any reference to your card in "dmesg" (do a "dmesg" as a rergular user in the terminal"; you can also check the output of "ifconfig -a".

There was a recent thread about the Marvel card:
[http://www.ubuntuforums.org/showthread.php?t=90579&highlight=sk98lin](http://www.ubuntuforums.org/showthread.php?t=90579&highlight=sk98lin)

Look at that.

If all else fails, you can go to: [http://www.syskonnect.com/syskonnect/support/driver/htm/sk9e21_lin.htm](http://www.syskonnect.com/syskonnect/support/driver/htm/sk9e21_lin.htm)

and try to build the driver by hand. But I'm surprised if you have to as it seems it is already in Breezy.

Post back with results. Good luck.
Alan

---

