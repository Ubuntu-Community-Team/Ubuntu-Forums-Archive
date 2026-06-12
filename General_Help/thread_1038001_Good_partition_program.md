---
title: "Good partition program?"
date: 2009-01-12
forum: General Help
---

### Post by Shiloh Hawkesworth on 2009-01-12
I need to set up a partition. Here is the details. 

I have a secure computer. This computer is in a secure room and is used to update safeguard drawings. It is a stand alone machine, not connected to anything. This computer is already loaded with Windows.

I need to set up a 20G partition on this computer. I need this partition so I can set up a new network drive in windows. The CAD program I used to update the drawings is set up to look at a network drive to grab the macro's that are used. 

What partition program should I use to do this? 

thanks

---

### Post by oilchangeguy on 2009-01-12
you can use the partition manager on the ubuntu live cd.

---

### Post by meindian523 on 2009-01-12
The "partition manager on the live CD" can be installed using ```
sudo apt-get install gparted
```Also,a GParted Live CD is available here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Tykin on 2009-01-12
My favorite partition software is actually Acronis, but you need to pay for that one.

But, yes, burn and start Ubuntu through a LiveCD and run the GParted program. You should be about to reallocate your space.

And, as always, backup your stuff just in case something goes horribly, horribly wrong. However, I've repartitioned my drives many times and never had a problem.

---

### Post by binbash on 2009-01-12
gparted live cd

---

### Post by hangfire on 2009-01-12
> **meindian523 said:**
> The "partition manager on the live CD" can be installed using ```
sudo apt-get install gparted
```

Kind of hard to do on a stand-alone, no network machine.

> **meindian523 said:**
> 
Also,a GParted Live CD is available here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

A better idea. I have been using SysRescueCD for this purpose. Besides Gparted, it provides a wealth of other utilities.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I always keep a SysRescueCD cd around, and the ISO as well.

-HF

---

