---
title: "Cannot Get Past Loading Screen"
date: 2009-01-03
forum: General Help
---

### Post by iamthird on 2009-01-03
After reinstalling Ubuntu a number of times, using everything from wubi to mounting the iso using daemon tools to booting from the cd, I still cannot get ubuntu to boot successfully.

The splash/loading screen appears, and I get to watch the little orange bar bounce back and forth for about 30 seconds until it freezes completely, and I have to reboot.

The same problem occurs when trying to boot ubuntu after installing with wubi, to simply trying to try the demo from the live cd without any installation. 

I've spent quite some time looking for help, and maybe I'm not looking hard enough, but I'm stuck. Please help if you can, thanks.

---

### Post by dtrot55 on 2009-01-03
What is your computer specs?

---

### Post by Tom--d on 2009-01-03
Mainly, what is your Graphics Card?

---

### Post by iamthird on 2009-01-03
Intel Celeron D 2.8GHz
2 Gb DDR2 SDRAM
533 MHz Bus Speed
Nvidia Gefore 5200 FX

---

### Post by dtrot55 on 2009-01-03
I had this problem at one point ... I loaded ubuntu on my hard drive restarted and either froze at loading screen or froze at the orange screen to the login...Look in your bios and see if you have an option called "Large Disc Access"  I had to switch mine to other...this changed the way the data was written on the hard drive...cause apparently some OS's like different geometry on the hard drive

---

### Post by dtrot55 on 2009-01-03
Or you could not install the Compiz stuff..though i dont know if you can do that in the initial install and since you cant get to the login screen you cant access the terminal to do that...but its worth a try to look into..ill see if i can find something out there for ya...benefits of working in the morning...hehe

---

### Post by dtrot55 on 2009-01-03
After looking around for awhile...havent seen anything to not install compiz on the initial install...but can you try loading up in recovery mode???  If that works and you get to the login screen do a ctrl+alt+f2 and use this code

> 
sudo apt-get remove compiz

and follow that by

sudo apt-get remove compiz-core


---

### Post by i.dont.register on 2009-01-03
Abit mother board? I have the IP-35-pro and there are known issues with booting on Sata drives.

---

### Post by hyperdude111 on 2009-01-03
I had to install (on my old pc) 8.04 first the upgrade.
It might work for you

---

