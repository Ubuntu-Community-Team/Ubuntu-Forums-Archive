---
title: "Hangs during startup"
date: 2009-06-25
forum: General Help
---

### Post by litlfrog on 2009-06-25
My computer is giving an error that the display did not start correctly. When I choose "Run Ubuntu in low graphics mode," it reboots, then hangs at a line stating
setting Advanced Power Management Level to 0xfe

What's going on here? It's not responsive to keyboard commands. Do I just need to try cold booting again?

---

### Post by litlfrog on 2009-06-25
Bump. Sorry to bump so soon, but this is a work computer. I can work at an absent coworker's station today, but if we don't get this fixed soon it's going to be a real problem.

---

### Post by ManiacDan on 2009-06-25
Did you recently make any changes to the system?  The ATI catalyst driver is rather famous for this.

-Dan

---

### Post by litlfrog on 2009-06-25
No recent changes. It's an older desktop--I have the idea that it's an Intel graphics card using something called a Savage driver.

---

### Post by ManiacDan on 2009-06-25
Savage is a video card manufacturer, so that's right.

Something must have changed, but if YOU didn't do anything, it must have been something subtle.  Any system updates?  New USB devices?  Power go out?  Anything?

-Dan

---

### Post by litlfrog on 2009-06-29
I do the regular system updates through Ubuntu when they come up. Honestly, it's not exactly as if anything has changed. I finally got the computer to boot normally after literally a dozen attempts. This error has been occurring on and off practically since install five or six months ago, and it happened on the installation of Ubuntu I had on this hardware before that.

---

### Post by decoherence on 2009-06-29
> I finally got the computer to boot normally after literally a dozen attempts

Sounds like a hardware problem. Can you open the machine up and make sure the components are properly seated?

Rebooting shouldn't fix anything, software-wise.... occasionally it does (still, it SHOULDN'T) but certainly not after a dozen tries!

---

### Post by litlfrog on 2009-06-29
Sure, I'll give that a shot.

---

### Post by litlfrog on 2009-06-29
OK, we've been flat out and I haven't had the chance to open that case. My browser froze and I restarted the computer. The problem came back: Ubuntu is running in low graphics mode. I looked at the startup log and saw this:

Error setting MTRR (base=0xf00000000, type=1) Invalid argument(22)

---

### Post by Wiebelhaus on 2009-06-29
Hardware malfunctioning , give it a good once over after you open it up , I bet there's swollen capacitors or faulty PSU.

---

### Post by litlfrog on 2009-06-29
Thanks, Wiebelhaus. May I ask, does that error message pretty clearly indicate that this is a hardware issue or might it be something else? If I have to explain to my boss that I need equipment replaced, I just need to be as sure as I can. :)

---

### Post by Wiebelhaus on 2009-06-29
> **litlfrog said:**
> Thanks, Wiebelhaus. May I ask, does that error message pretty clearly indicate that this is a hardware issue or might it be something else? If I have to explain to my boss that I need equipment replaced, I just need to be as sure as I can. :)

The graphic BIOS is misreporting graphic memory and it's resulting in an error , symptoms are the wrong memory amount or memory type or in your case , failure. The specific reason cannot be determined , it's a garden variety error but just like in windows it means there's a hardware malfunction. There may very well be a software "work around" or "Jerry rig" but at the end of the day , it's still malfunctioning hardware.

---

### Post by litlfrog on 2009-06-29
New video card acquired! Since Ubuntu was set up to load with the old video card, will the computer be able to boot successfully once the new card is inserted and the monitor plugged in? Or am I going to have to edit a configuration file somehow during startup?

---

### Post by Wiebelhaus on 2009-06-29
> **litlfrog said:**
> New video card acquired! Since Ubuntu was set up to load with the old video card, will the computer be able to boot successfully once the new card is inserted and the monitor plugged in? Or am I going to have to edit a configuration file somehow during startup?

It'll re-detect , but do go with Nvidia , much better support!

---

### Post by ManiacDan on 2009-06-29
For what it's worth, I have 3 ubuntu computers with various ATI cards and the graphics are fine on all three, but you do have to use ATI's closed source drivers.  

-Dan

---

### Post by litlfrog on 2009-06-30
Oh, I don't have a choice as to what card I get. :) The company bought a bunch of HP desktops back in 2001 or so; when something breaks, we just cannibalize from the other systems. So, I put in a new card and the computer boots now, but when I try to open ANY program, it immediately kicks me back to the login screen.

---

### Post by litlfrog on 2009-06-30
Well, that's what happened at FIRST--now I'm getting the exact same error of misreporting graphics memory with a new card inserted. Is it still trying to read the onboard video even though I'm not using it? I reset xorg.conf back to defaults, restarted the computer, no change.

---

