---
title: "Printing stopped working in Ubuntu 8.04"
date: 2008-07-19
forum: Desktop Environments
---

### Post by hotdogger_khe on 2008-07-19
I  just noticed that my computer can no longer print from ubuntu.  What I find very odd about this is if I open up virtual box and load my completely virtual xp drive, printing works fine....Shouldn't the printer be being accessed through ubuntu??  

When i try to print in ubuntu it shows an exclamation mark on the printer icon and gives me the error message that the printer has stopped.  

I have had this printer working for a good month now with no issues, and haven't changed anything that I am aware of before it stopped working.  Any suggestions would be appreciated.

Thanks

---

### Post by ajgreeny on 2008-07-19
I can't see why it should happen, but perhaps worth switching it off, uninstalling the printer in System>>Administration>>Printing and then reinstalling it again, though it may be found automatically after uninstalling and switching it on.

---

### Post by hotdogger_khe on 2008-07-19
Thanks for the advice.  Apparently all I had to do was reboot???? unplugging the printer is a rather difficult task so I opted to try a simple reboot and all is well.  Although, I find it interesting that the printer stopped working in the first place.

---

### Post by smilingfrog on 2008-09-10
I am having the same problem here. I also find that the printer works through virtual box, and stops in Ubuntu until a reboot. Any ideas how to reboot the printer without having to bring the entire machine down?

---

### Post by tgalati4 on 2008-09-10
You can try to restart the CUPS printing system:

>sudo /etc/init.d/cupsys restart

CUPS is sensitive to the kernel that you are using so updating the kernel can sometimes cause breakage.

---

