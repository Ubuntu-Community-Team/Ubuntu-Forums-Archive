---
title: "Can you help me see my Usplash on my XPS M1330"
date: 2008-04-21
forum: Dell  Ubuntu Support
---

### Post by AegisTalons on 2008-04-21
Hey everyone,
I feel like i've tried everything from the application called startup manager to manually edit the files and nothing works. Could someone out there that also has a XPS M1330 tell exactly how to display my Usplash (window with loading bar on load of OS). Even better if you can post your files or the text of them.

Greatly appreciate any help you guys can give.

---

### Post by sdennie on 2008-04-21
Do you mean a custom usplash or are you simply seeing no usplash at boot time at all?  If it's no usplash at all, and you are running a 64bit flavor of Ubuntu, you may want to check this bug: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623)

---

### Post by AegisTalons on 2008-04-21
I have no usplash at boot time at all. The thing is before I reformated my hard drive because Vista destroyed everything (long story), I had usplash working. I didn't save the grub menu config file. Also on my desktop (64 bit) I have it working and at a high resolution none the less but I looked at the grub menu config file and there is nothing special in it, like vga=791.

Any ideas will greatly be apprecaited, especially if you have a m1330 and have usplash working, could you post your grub menu config file.

---

### Post by sdennie on 2008-04-21
When I was running 64bit Gutsy, I had the same problem on an XPS m1330.  I didn't spend much time trying to fix it because you can just remove the word "splash" from "defoptions" in /boot/grub/menu.list and run update-grub.  That's not optimal because you won't have a pretty usplash screen but, you at least get some feedback instead of a blank screen as the machine starts.

Note: This only happens on 64-bit flavors of Ubuntu.  The usplash works just fine on 32-bit.

---

### Post by jespdj on 2008-04-21
There's an old bug (can't find it right now in Launchpad), where the boot splash screen does not display on 64-bit Ubuntu with nVidia 8xxx cards.

I had this problem on my desktop (with 8600GT) and M1330 (with 8400M GS) with 64-bit Ubuntu 7.10 and older versions.

It looks like this is finally solved in the release candidate of Ubuntu 8.04 - on my XPS M1530 (with 8600M GT), the boot splash screen works perfectly, and it's in high resolution too.

So, try the 64-bit release candidate of Ubuntu 8.04 (or wait a few days for the final release of Ubuntu 8.04) and see if it works.

---

### Post by AegisTalons on 2008-04-21
Yargh, I guess the easiest solution would be for me to wait till Hardy gets released into the update manager and just hit the update button.

Regarding that, does anyone know if there are any issues with upgrading because I do not feel like reinstalling ubuntu using the CD or having the system not work like it is now especially with the end of college coming up.

---

