---
title: "External DVD Drive, GParted, and Kernel Panic"
date: 2006-06-22
forum: Desktop Environments
---

### Post by arthur on 2006-06-22
Using an IBM Thinkpad X40. No optical drive.
I want to repartition using GParted, so downloaded the ISO and burned it to disc.
I then switched on with my external Freecom Classic CD/DVD/RW. GParted starts loading, but gets to a point where the following message is displayed:

...
[B]NO GParted LiveCD found!!!
Kernel panic - not syncing: Attempted to kill init![/B]

And that's it: no way out.



Previous troubleshooting:
CD/DVD/RW Unit: working OK (started Dapper with it on this machine)
GParted LiveCD: OK (started it completely on my other laptop)

What is happening?
This is weird!

---

### Post by Jeffrey Magder on 2007-01-22
> **arthur said:**
> Using an IBM Thinkpad X40. No optical drive.
I want to repartition using GParted, so downloaded the ISO and burned it to disc.
I then switched on with my external Freecom Classic CD/DVD/RW. GParted starts loading, but gets to a point where the following message is displayed:

...
[B]NO GParted LiveCD found!!!
Kernel panic - not syncing: Attempted to kill init![/B]

And that's it: no way out.



Previous troubleshooting:
CD/DVD/RW Unit: working OK (started Dapper with it on this machine)
GParted LiveCD: OK (started it completely on my other laptop)

What is happening?
This is weird!

Hi there Arthur.  

I'm not sure if you are still having this problem, but I may have a solution.  I too was trying to boot up the GParted LiveCD (version 3.2 and 3.3 in my case) on an external DVD drive, when I received the same error message. While there are obviously a number of possibilities as to what could cause this,  in my case it was the USB port I connected the external DVD drive to that was the source of my problems.  I switched to another port and everything ran fine.  

I can't recall the exact details, but there were some earlier error messages about the USB port and some wrong IRQ's and error -110.  These error messages appeared only after the LiveCD presented its first menu.  I think that between presenting a menu (Video Card selection, special boot options, etc), and loading the GParted image, the USB port for whatever reason was no longer accessible. (BIOS problem?)  As such, when the resident program tried to load the GParted image, it was no longer there.  By switching to another USB port, the earlier error messages disappeared, and the kernel panic went away.  

Good luck!

- Jeffrey Magder

---

