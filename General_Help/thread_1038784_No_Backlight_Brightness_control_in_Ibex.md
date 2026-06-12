---
title: "No Backlight Brightness control in Ibex"
date: 2009-01-13
forum: General Help
---

### Post by rmausser on 2009-01-13
Hi, I have an HP Pavilion DV2000 Laptop (Nvidia and AMD version)

I have installed 8.10 with Ubuntu Studio installed in the Repos afterwards (this way networking and other laptop functions work)

A problem has popped up where my backlight brightness will no longer work.

This is not just for my function keys, even if I add that brightness applet to the panel, nothing happens when I slide the brightness up and down.

I have the Nvidia Driver version 177 installed for an Nvidia Geforce 7150M.

If anyone knows how to fix this it would be greatly appreciated. The install is a week old, and worked before some updates. 

I have the restricted updates installed, but falling back to an earlier kernel does not solve the issue.

Thanks

Rob.

---

### Post by crazyness003 on 2009-01-13
Same problem here. It seems like its either a bug in the new kernel update or acpi-support package. Heres the original UF thread
[http://ubuntuforums.org/showthread.php?t=1036390](http://ubuntuforums.org/showthread.php?t=1036390)
and here the bug report submitted to launchpad.net
[https://bugs.launchpad.net/ubuntu/+bug/316145](https://bugs.launchpad.net/ubuntu/+bug/316145)

If you dont mind, register on launchpad and post in there. The devs look in there more often than in here.

---

### Post by rmausser on 2009-01-14
My problem is a bit different though... I can open the brightness applet and move the slider up and down...just nothing happens when I do it. 

I don't get an error message like everyone else

---

### Post by crazyness003 on 2009-01-14
error message? oh the tooltip. No, thats just when you hover your mouse over the applet. Im sure you get it too.
But thats not the point. The entire brightness feature (the backend) is busted.
Also soft-keys [noparse](fn-f8) [/noparse]dont work either.
And we founf out what the prob is: linux kernel 2.6.27-11.23
See this too: 
[                **Reduce brightness on HP Pavilion dv5-1020ep (Ubuntu 8.10 64 bits)**]("http://ubuntuforums.org/showthread.php?t=1036041")

---

### Post by Drubie on 2009-01-15
I have a MacBookPro loading Intrepid with the 177 version of the NVIDIA driver, and an configuration option appeared under System > Administration > NVIDIA X Server Settings.
From there I can change all sorts of display-relating things (gamma, color...)  Perhaps you have a similar addition to your menu.

I know it is a lame, non-technical answer, but if it gets the job done...

---

### Post by crazyness003 on 2009-01-15
i guess that can work, but i dont know if its considered a power-saving feature. Plus it dosnt solve the fact that the new kernel update is caca
I'll give it a try to to play around tho.

---

### Post by rmausser on 2009-01-15
WOOHOO! UPDATE

The latest updates on the .11 kernel image fixed the brightness issue on my laptop.

Update to the latest restricted drivers.

Now...by not enabling these restricted updates in the first place would have never caused the issue, why have linux if you can't live on the bleeding edge? ;)

Oh, because windows is even buggier...I forgot. 

Rob.

---

### Post by crazyness003 on 2009-01-16
havent tried. will test in the morrow

EDIT: Yes, the latest intrepid-proposed updates fixed this. Thanks to the devs

---

### Post by johny_ on 2009-10-09
Hello,

It's been few months, and I'm still having this.
The Nvidia settings application let me set the brightness, the GNOME brightness applet doesn't work when moving the slider, and, another alternative way is to use "smartdimmer", but, that's must be done from the shell.
Nvidia driver is 180.44 (should be the most recent recommended), kernel 2.6.28-15-generic.

---

