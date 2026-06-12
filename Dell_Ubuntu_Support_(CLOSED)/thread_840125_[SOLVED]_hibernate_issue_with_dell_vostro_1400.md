---
title: "[SOLVED] hibernate issue with dell vostro 1400"
date: 2008-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by empty_tank on 2008-06-25
I think I have resolved most of my issues with ubuntu hardy install on Vostro 1400n.  Resolved issues include: keyboard control of brightness, sound and pulseaudio, and compiz.

My remaining issue involves resuming from hibernation.  Suspends works (it would resume nicely with a login box either thru opening the lid or pressing the power button).  While hibernating, the computer would show that the HDD activity LED lights up before the computer shuts down.  Pressing the power button would, however, restart the computer instead of resuming.

My specs are:
        Vostro 1400 with: 
	Intel Core 2 Duo (1.66.Ghz), 
	4 GB DDR2 SDRAM, 
	120 GB HDD, 
	integrated Intel Graphics and wireless, 
	Sigmatel 9928 Audio,
	Conexant HDA D330 MDC Modem 
        4 GB swap partition


Thank you.

---

### Post by totlinuxnewbichik on 2008-07-04
I'm using a Dell c610 ( 1Ghz 640mgs RAM Radion Mobility M6 graphics card)
and I have issues with hibernate mode even since adding more memory.
What I used to do when I had Windows XP installed was to put a screen saver on it to prevent the hibernate from happening all together. 
I started doing this because when I would leave it on without moving the mouse for an hour or two, I'd come back to find the screen black with no possible way to revive it but to reboot. 
Since I use my laptop for business, I'd often have work open that I didn't want to have to dig up again when I returned from lunch break or whatever. I had this crazy idea that maybe if I gave it something to work on, it wouldn't go to sleep. 
I don't know if that was even in the same ball park as correct, or if it was mere coincidence, but once I had the screen saver on there the laptop would go right back to what I'd been doing before I left - even if I left it overnight. No more restarting the whole system after an hour long conference call! Since I switched OSs, I have no idea how to do this or if it would still work. 
Any ideas? :confused:

---

### Post by empty_tank on 2008-07-04
> **totlinuxnewbichik said:**
>  once I had the screen saver on there the laptop would go right back to what I'd been doing before I left - even if I left it overnight. No more restarting the whole system after an hour long conference call! Since I switched OSs, I have no idea how to do this or if it would still work. 
Any ideas? :confused:


even without the screensaver, you could suspend the system to RAM.  You could restart by pressing the power button or open the laptop lid.  This is not an issue with my laptop using hardy.  

My problem is hibernating to the harddisk (specifically swap partition).  If i try to hibernate, the laptop basically just shuts down.  I cannot resume if I repower my computer (it just restarts).

---

### Post by empty_tank on 2008-07-06
issue solved.  Please see [http://ubuntuforums.org/showthread.php?t=850755](http://ubuntuforums.org/showthread.php?t=850755)

---

