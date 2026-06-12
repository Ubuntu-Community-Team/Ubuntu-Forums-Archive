---
title: "Why can't I get help with this?"
date: 2009-08-08
forum: Desktop Environments
---

### Post by Gnusboy on 2009-08-08
I've posted this twice and so far have received 1 suggestion - and it did not work. 
I have read through many forums and cannot get a clear idea or a simple work around to make 9.04 boot properly - like it is supposed to work. 
I don't mind doing a reinstall, if necessary, but I'd like to know how to avoid the issue in the future. 
This is the situation:

                                  **9.04 Suddenly Won't Boot -previously worked fine.**             
                                                       [B]Boot problem: Jaunty runs through startup, gets to splash page, appears to load and then display goes black before logon. (I tried Ctl-alt-f2 - nothing)
[/B] [B]
Ubuntu Jaunty 9.04 installed about 3 weeks ago and it functioned fine until it suddenly did not. I had Shut it down as usual, but when I booted later, it went through POST up to the splash page and then no display. No user or password space - just dead.

Reconnected other machine, read forum. Tried booting through recovery mode solutions generic kernels 2.6.28-14, 13, 11- AND recoveries from Grub as listed.
None of the recovery options generic or recovery modes got me past initial splash screen.

Also tried repair modules - nada.

Everything was working fine until I made 1 change in the keyboard assignment area - I thought I turned off the Caps Lock, and enabled it with shift-caps. (can't recall exact phrase)

Did nothing else that I can recall.
Apparently, this was an earlier problem, but the threads died before I could find out how to bring up the terminal without a password and then add some code.[/B]    

I'd prefer not stumbling around in a dark room and barking my shins more than I have. The fun of this adventure is wearing thin.
Thanks


------------------------------------------------------------------------------------------------------
System: ASUS M3A78-EM, integrated ATI Radeon HD3200 GPU, AMD 4-Core 9850, 4 GB 800 mhz ram, 640 HDD, Ubuntu 9.04,
------------------------------------------------------------------------------------------------------

Any ideas?
Thanks

---

### Post by Tclarkie on 2009-08-08
boot off cd, get all files u need to keep, then try reinstalling
its not a common problem

---

### Post by ddrichardson on 2009-08-08
One of my laptops does this, a Dell 1545 but its intermittent and is usually responsive to the power button being pressed to reboot then its fine.

I coincided with a kernel update and I suspect its an APIC implementation problem. When on the grub boot menu, edit the boot line to add at the end:```
noapic
```

If this doesn't stop it we can rule it out and look elsewhere.

---

### Post by Gnusboy on 2009-08-08
Thanks
Luckily, I don't have much on disk except the new configs like Flash 10
I'm just gonna re-install and go from there.
I appreciate your suggestion, but I couldn't get it to accept the noapic line. Prolly operator error.

---

### Post by Gnusboy on 2009-08-08
Thank you.
But I just couldn't get it to work.
I'm just gonna reinstall and go from scratch.
I might need help from there though, if you wouldn't mind.
Since starting with Ubuntu, I seem to be dumber than a sack of hammers. Then again, I might have been that way anyway. :)

---

### Post by TrakerJon on 2009-08-09
1. Go to your motherboard manufacturers site and get the latest BIOS update and install it. 

2. Make sure the RAM in your computer is not from several manufacturers, in other words if you have 2 or 4 cards make sure they're all from the same company.

3. Make sure your video card is seated properly with no loose cable connections.

4. Is your system cooling properly? Old power supply? Weak CPU fan? Poor ventilation? 

Once you do the reinstall make sure you get all the available updates first before tweaking your system...

---

