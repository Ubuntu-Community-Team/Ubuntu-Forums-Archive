---
title: "spca5xx Driver in 5.10?"
date: 2005-10-15
forum: Desktop Environments
---

### Post by polo_step on 2005-10-15
Now that I see a much better webcam outlook with the improved GnomeMeeting in 5.10, I'm wondering about going to a Creative NX, which I believe is supported by the spca5xx driver.  These cams are cheap here this week ($4.99 after rebate) and my present IBM webcam will never work all that well due to the primitive experimental Linux driver.

Anyone know if spca5xx is in this build and, if so, how well it works with the NX?

As always, thanks for any help.

---

### Post by az on 2005-10-15
lib/modules/2.6.12-9-386/kernel/drivers/usb/media/spca5xx/spca5xx.ko base/linux-image-2.6.12-9-386


Yup.

---

### Post by pecanov on 2005-10-15
I don't know how will it work with Creative NX, but using the breezy spca5xx packed kernel module with Logitech ClickSmart, freezes the system everytime I try to use it. However, I think, this affects almost all cameras wth spca5xx chips.
Downloading it and building from source solves this problem.

---

### Post by polo_step on 2005-10-15
[QUOTE=pecanov] freezes the system everytime I try to use it. However, I think, this affects almost all cameras wth spca5xx chips.
Downloading it and building from source solves this problem.[/QUOTE]
Oy.:( 

I seem to remember someone said that the Creative USB cams were relatively trouble-free in 5.04, but I'm not sure.  I know that the spca5xx list of supported devices includes the NX (which is substantially different than the other NX series, such as the NX Pro) in the latest version of the driver.

This is of course nominal or perhaps notional. :rolleyes: My Bt879-based video capture card is *supposed* to be supported, but it crashes HotPlug (and the system) every time I try to boot in 5.04 with it installed, and would crash 5.04 Live boot as well.  I have no idea what it'd do with 5.10 and it's a bit of an undertaking to physically install it as an experiment.

I was thinking that if the NX would be PlugNPlay in 5.10, I'd get one because they're cheap here this week ($4.99 after rebate).

---

### Post by polo_step on 2005-10-15
[QUOTE=azz]lib/modules/2.6.12-9-386/kernel/drivers/usb/media/spca5xx/spca5xx.ko base/linux-image-2.6.12-9-386[/QUOTE]
Thanks for that info!

---

### Post by cowlip on 2005-10-15
breezy;s module is broken: [https://bugzilla.ubuntu.com/show_bug.cgi?id=14566](https://bugzilla.ubuntu.com/show_bug.cgi?id=14566)

---

### Post by polo_step on 2005-10-15
[QUOTE=cowlip]breezy;s module is broken: [/QUOTE]
And it seems that the definitive manual fix is still evolving. :( 

Will there be a bugfix on this before 5.11?

---

### Post by kleeman on 2005-10-15
Follow arnie's howto:
[http://www.ubuntuforums.org/showthread.php?t=70657&page=3](http://www.ubuntuforums.org/showthread.php?t=70657&page=3)

---

### Post by polo_step on 2005-10-17
[QUOTE=kleeman]Follow arnie's howto:
[http://www.ubuntuforums.org/showthread.php?t=70657&page=3](http://www.ubuntuforums.org/showthread.php?t=70657&page=3)[/QUOTE]
As of this moment in the thread, the how-to isn't fully reliable in unbugging the problem.

I'll pass on this webcam, at least until there's an official bugfix.

---

