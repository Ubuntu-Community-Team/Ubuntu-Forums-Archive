---
title: "Please help! (graphics drivers)"
date: 2009-01-06
forum: General Help
---

### Post by aa13x on 2009-01-06
I recently installed ubuntu 8.10 on my pc, and when I was using the live cd, the screen resolution was maxed out, and everything was fine. But when I was installing ubuntu, the resolution was at 640 by 480, which made the installation process tedious.

Now, after installation, the resolution is still stuck in 640 by 480. I have been trying to find solutions for a WHILE. But to no avail.

I'm on an Intel Motherboard, and running off of the built-in graphics chip set. I was surprised when I read in a few places that Intel was supposed to be well supported right out of the box, but here I am in this situation.

After tedious searching I finally found the right driver, but I have no clue as to how to install it. Also, when I was searching through the hardware setting things, I found that there are no hardware drivers even listed.

I am SO confused! And, I'm trying to solve this when it's my first time using linux...

Could anyone point out how to fix this? Also, if it requires using the Terminal, could you point out each command to use? I don't know how to use it, and every website I go to just says run this, untar that, and not giving direct info for noobs.

Anyhoo, I'm trying to install an Intel 865gv driver, and if any additional information is needed, I'll try to find it.

Thanks

---

### Post by blazemore on 2009-01-06
Go to System -> Administration -> Hardware Drivers
Is there a option to install a driver there?

---

### Post by aa13x on 2009-01-06
It doesn't show anything

---

### Post by blazemore on 2009-01-06
What's in the folder containing the driver download?

---

### Post by blazemore on 2009-01-06
Also have you checked the resolution itsself? System -> Preferences -> Screen Resolution

---

### Post by aa13x on 2009-01-06
the folder that has the install.sh and other files in it is on my desktop (called dripkg).

Also, when I go to the resolution settings thing, all it shows me is the 640 by 480 resolution, and it says in the middle is Unknown, and refresh rate is at 0 hz, and I can't change anything inside of it.

---

### Post by aa13x on 2009-01-06
bump?

---

### Post by DougieFresh4U on 2009-01-06
Have a look in **System>Administration>System Log>Xorg log**
See what it's listing as the driver. I know from recent problems Intel is 'crap'
You may need to get into 'xserver' file and put Intel in there. We can get to that later.
I am no 'guru', but I can try to help some.

---

