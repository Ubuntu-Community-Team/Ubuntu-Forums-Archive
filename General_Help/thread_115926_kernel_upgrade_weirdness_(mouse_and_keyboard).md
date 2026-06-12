---
title: "kernel upgrade weirdness (mouse and keyboard)"
date: 2006-01-11
forum: General Help
---

### Post by x3non on 2006-01-11
Hi all,

this is my first post :D

well i have a strange issue:

I've replaced my painful windows box some months ago with Ubuntu 5.10 (kernel 2.6.12-10-686) on a P4 3.0 HT and everything is working fine.

Now i'm trying to use the SMP kernel to get the full power of my P4.

I got through synaptic the kernel 2.6.12-10-686-smp but when i reboot ther's no way to get keyboard and mouse working. 

I tried booting with noapic and nolapic options in grub but it didn't solved.
I cannot go over the GDM login greeter.
Obiouvsly I can't open any terminal and I have to brute-force a reboot via the reset button.

If i revert on the old kernel everything returns working.

Any help?

Thanks a lot,
X3non :cool:

---

### Post by o_fortuna on 2006-01-11
[QUOTE=x3non]Hi all,

this is my first post :D

well i have a strange issue:

I've replaced my painful windows box some months ago with Ubuntu 5.10 (kernel 2.6.12-10-686) on a P4 3.0 HT and everything is working fine.

Now i'm trying to use the SMP kernel to get the full power of my P4.

I got through synaptic the kernel 2.6.12-10-686-smp but when i reboot ther's no way to get keyboard and mouse working. 

I tried booting with noapic and nolapic options in grub but it didn't solved.
I cannot go over the GDM login greeter.
Obiouvsly I can't open any terminal and I have to brute-force a reboot via the reset button.

If i revert on the old kernel everything returns working.

Any help?

Thanks a lot,
X3non :cool:[/QUOTE]
I never had a problem upgrading to the smp kernel... you might check to see if you have the restricted modules and everything else installed. Just do this in the terminal (applications->accessories)
```
 sudo apt-get install linux-686-smp 
```
This will install the entire kernel. If this doesn't work, I don't know what the problem could be.

---

### Post by x3non on 2006-01-11
i reinstalled the kernel with also restricted modules (that before i was missing) but it didn't helped. :(

Bye,
x3non

---

### Post by gatorbrit on 2006-01-11
I had a related problem with this upgrade - my USB wireless card was no longer found by Ubuntu.  But when I boot of the prev kernel I am good to go.  Not sure whether this is a USB issue - if your mouse and keyboard are USB - or what.

---

### Post by x3non on 2006-01-12
nope, they are PS/2

bye, X3non

---

