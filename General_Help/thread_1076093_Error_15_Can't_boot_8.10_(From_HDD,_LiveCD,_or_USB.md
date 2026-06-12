---
title: "Error 15: Can't boot 8.10 (From HDD, LiveCD, or USB)"
date: 2009-02-21
forum: General Help
---

### Post by thehuman on 2009-02-21
Hey guys. Upon some advice I received earlier today, I was attempting to install Ubuntu 8.10 64 bit over my existing 32 bit installation. I wasn't trying to do anything fancy--just wipe the whole original install and put the new one in its place. Everything was going fine until the end of the installation, where everything froze. I had to do a hard restart, and now I get the Grub Error 15 every time I try to boot. 

The general consensus I have found on this error message is that I need to edit my grub file to point it to the right place, but I cannot boot ANYTHING right now. I tried 5 different Live CD's, an Ubuntu flash drive, and even an XP install disc, and NOTHING will get past the GRUB error. It just gets there and freezes.

Does anyone have any ideas how I can get my PC to boot ANYTHING right now? I'm not really too thrilled about what is going on, and while I would prefer not to, I don't care too much about data loss. I just want to be able to boot. Any advice would be greatly appreciated.

System:
Lenovo Thinkpad R61
Core 2 Duo 2.4GHz
4GB RAM
160 GB 7200RPM HDD (30GB for XP, 30 GB for Ubuntu, 6GB for swap, and the rest for shared storage)
Intel Integrated Graphics

Thanks for reading, and hopefully someone can help me out. Good night!

---

### Post by Amarsingh0793 on 2009-02-21
Check the settings in your BIOS to see if devices are placed before the HDD in the botting queue. Also try the Knoppix CD ([http://www.knoppix.org/](http://www.knoppix.org/)).

If everything goes well, I recommend you burn another 64 bit ubuntu disc and try again :P

Good Luck

---

### Post by sahabcse on 2009-02-21
Hi

If you are able to access the bios setup means, just connect the external DVD drive, Put the OS cd and change the boot device. The live CD will loaded from the external Disk. Then you can fix the grub very easily. For fixing the grub follow the urls

====================================================
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
====================================================

Regards,
Sahab

---

### Post by thehuman on 2009-02-21
I can get to BIOS, and I have tried changing the boot order (as well as every other setting I thought might even remotely affect it), and it didn't help.

I will try Knoppix CD, but I don't have an external CD/DVD drive, so that could be a problem if the CD drive just plain doesn't want to boot.

Thanks for the advice so far guys. This is driving me crazy, and I really appreciate the help.

---

### Post by primus454 on 2009-02-21
If you have the option, try switching "IDE Configuration" in BIOS from "Enhanced" to "Compatible". I had to do this in order to to get Ubuntu to install period on my ASUS.

---

### Post by thehuman on 2009-02-21
That was actually one of the things I had already tried to no avail.

I ended up fixing this, but it was just a worst-case scenario solution. I dismantled one of my external hard drives to get the case, and then I took the cd drive out of my desktop, and put them together. A very annoying solution, but it worked.

Thanks for all your help, everyone. I am truly grateful. I mean, come on... a Saturday morning without a laptop??? What is this world coming to?

Anyway, I'm glad I have Ubuntu up and running, and now I'm 64 bit, so I feel that much cooler. Thanks again!

---

