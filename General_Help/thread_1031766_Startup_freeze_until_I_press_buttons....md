---
title: "Startup freeze until I press buttons..."
date: 2009-01-05
forum: General Help
---

### Post by HaydenGribble on 2009-01-05
Hi guys, I have a small problem with Ubuntu 8.10.
From about two days ago, whenever I startup or shut down, when the Ubuntu logo comes up with the load bar beneath it, it just stops, won't do anything. When I press a button or click the mouse (touchpad), it starts to work for a bit, then it stops. To make it start up quickly, I need to hold a button down.
Just this morning, though, when I started it up, I had to press a button down until it started doing the routine drive check... When that was in progress it worked fine and I could just leave it.
When I shut down it will just stop when the loading bar appears, until I press a button, and it will not shut down after the bar has gone black, I must press a button or the mouse for it to move... Any ideas? Thanks.

EDIT: Sorry, I thought I should put up my computer's specs.
HP Pavilion DV6504au
1GB RAM
80GB HDD
Dual boot Vista Home Premium and Ubuntu 8.10 with GRUB
[+ going to update Ram to 2GB]

---

### Post by HaydenGribble on 2009-01-08
Sorry to bump this but I was just wondering if anyone knew what could be causing this. I won't bump it again...

---

### Post by thedarkwinter on 2009-01-09
Ummmm...

I have no idea :), but it sounds like something is actually waiting for human input...

Have you tried booting recovery mode? (or press escape at the booting progress bar). This will output whats going on during the boot process and maybe you can see whats going on. 


cheers,
michael

---

### Post by adamlau on 2009-01-09
Immediately after a successful login:

```
dmesg > ~/Desktop/dmesg
```

Review the dmesg file on your Desktop for possible hardware errors.

---

### Post by HaydenGribble on 2009-01-09
Thanks guys, I'll try these first thing tomorrow.:D

---

### Post by HaydenGribble on 2009-01-12
I tried what you said and the ESC button at startup didn't show anything unusual, it just froze every now and then until I press a button, and I tried the dmesg thing and that looked normal to me, didn't look like it was asking for any input...

I'm thinking it could be a RAM problem because I know that with some things, inputting something makes it run a bit faster, but even better with more memory... I don't really know, and it isn't really that bad. It'll take a lot more for me to go back to Windows...

Thanks guys. Any more help would be appreciated but if not, well that's fine...

---

### Post by HaydenGribble on 2009-03-11
I finally found a fix for this problem.

In the GRUB bootloader, I had to put in 'acpi=noirq" on the kernel line for Ubuntu. I also found that nolapic works, but it didn't for me.

Hopefully this will help somebody else.

---

