---
title: "Slow and unstable running on new machine"
date: 2009-03-09
forum: General Help
---

### Post by Hibbo on 2009-03-09
Hello there!

I've been running Ubuntu for just over a year now, and am very happy with it.  I started off by installing 8.04 on my HP nc6320 laptop, this was then updated to 8.10.  The install is completely on an external USB harddrive (a WD Passport 250GB to be precise) including grub etc.

I now have a new laptop, a Dell Latitude D830, and Ubuntu does indeed boot and run from the USB drive.  However, it is quite unstable on this new laptop.  I often get application windows greying out, I have problems with sound (especially with Skype) and only one application can access the sound hardware (if Firefox is open and I open RhythymPlayer, RP gives an error when you try to play a tune).  It also seems VERY resource heavy, even with the computer sat idle, one processor is showing 99-100% in use on the system monitor, yet the processes tab doesn't show anything to be using such resources.

None of this was the case on the HP laptop.

So, (I think) what I am asking is: Is it possible to get Ubuntu to autodetect and reconfigure itself to its new hardware, just as it does when one installs for the first time?  
I have a nice setup, so I really don't want to have to wipe it and start again..... (Windows style!)

Thanks for any help or pointers,

Cheers!

---

### Post by kmac on 2009-03-09
Well, try upgrading to Ubuntu 8.10 to help with some compatibility issues. Also, change your default audio device from "Auto" or "OSS" to ALSA under your sound preferences. This should fix your audio problem, be sure to reboot afterward. I can't remember if it's 8.04 or 8.10 that uses the new version of xorg, but the newer version will automatically detect hardware and configuration at bootup.

Also, I think you should have stuck with HP and not have switched to a Dell, but that's just my brand preference :)

---

### Post by Hibbo on 2009-03-10
Thanks kmac, I am already running 8.10.  I *think* have have already done that with the sound drivers, but I'll check though.

PS.  These are work laptops, so I had to hand the HP back when I changed jobs.  It did run very well though.....:)

---

### Post by Hibbo on 2009-03-10
Here's a screenshot of the system monitor, all that is open is a Firefox window, but look at my poor processors....:(

---

### Post by kmac on 2009-03-10
You might also be limited by the speed of your drive access. Any possibility of switching to an interface such as firewire or eSATA?

---

### Post by kmac on 2009-03-10
> **Hibbo said:**
> Here's a screenshot of the system monitor, all that is open is a Firefox window, but look at my poor processors....:(

Ouch... you got me beat now. Try testing with a fresh, naked install of ubuntu on something like a 1GB flash drive. See if something a bit more barebones still keeps that load on there.

---

