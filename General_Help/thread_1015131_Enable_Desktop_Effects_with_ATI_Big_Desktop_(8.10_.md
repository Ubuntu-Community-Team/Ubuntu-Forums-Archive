---
title: "Enable Desktop Effects with ATI Big Desktop (8.10 + fglrx)"
date: 2008-12-18
forum: General Help
---

### Post by noahsatellite on 2008-12-18
I'm wondering if anyone got Desktop Effects working with dual monitors using ATI Big Desktop.  I've seen a lot of posts about getting compiz working but either the result seems to be that you can't get it to work, or doesn't seem to apply to people using fglrx drivers with ATI Big Desktop.  It took me a day just to get my dual monitor setup working, and now my desktop effects are disabled :(

When I run compiz-check it alerts me to the fact that my resolution is set to 3360x1050 which is greater than the maximum resolution for compiz (2048x2048).  It seems to me that this has to do with how ATI Big Desktop works since my monitors themselves can each only do 1680x1050 (which is half the length of 3360x1050).

Is there any way to get compiz working in a setup like this?

Thanks,
Noah

---

### Post by baietas on 2009-01-28
Have you figured this out? I'm trying to enable desktop effects on 2 x 1920 x 1200 but no luck :(

---

### Post by rodbotic on 2009-01-28
ditto, 

if I clone it works fine. 
big desktop nada. mine is set at 2560x1024.

I was wondering if I would have any luck using 2 card for dual screen.
but I couldn't get ubuntu or ATI software to dectect the second card(PCI 9550, the main card is an AGP 9800) windows dectects the second card fine.

if anyone has the solutions/workaround I would love to know.

thanks

Rod

---

### Post by oneindelijk on 2009-03-24
Hi, 

I've finally managed to get Compiz working With two Monitors on my Acer Tm 5520 with an Ati Radeon Express 1250 without screwing my desktop so badly
I can't even recognize where my cursor is.
After screwing up a bit my whole system, I've reinstalled from scratch, thereby using the newest ati drivers (found on the ati website).

After several restarts and fiddling with a number of settings, this is what worked for me:
- remove all fglrx -related packages
- run ati-installer script (you won't need any dependencies mentioned in the installation instructions; probably because they come out-of-the-box with 8.10 Intrepid.
- reboot
- set screen resolution to 1280x800 (my laptops screen)
- enabled compiz effects
- reboot
- connect L1908w monitor (1440x900)
(! after a reboot linux automatically selected the maimux sceensize, which is already an improvement as I had to correct the screenresolution everytime I booted with the external display connected)
- using Catalyst Control Center, enabled both displays as independent
- set resolution 1440x900 resp 1280x800
(the screen resolution is set to 1280x800 for both screens
- reboot

Now my desktop looks fine with one screen set to 1440x900 and the other to 1280x800.
Compiz still works; Cube still works; reactive Corners still work;

However, I can't get my mouse to the second screen !
Do I need to alter a setting somewhere or do I need to use a shortcut to switch between them ?

If you need any specific information that can help you out setting up dual monitors, feel free to ask !

btw I tried enabling Xinerama (which is just a checkbox in the new catalyst config screen) which resized my desktop to about a quarter of the viewscreen thereby keeping the original coordinates for the mouse...

---

