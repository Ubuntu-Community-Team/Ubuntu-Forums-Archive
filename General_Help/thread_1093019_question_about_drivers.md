---
title: "question about drivers"
date: 2009-03-11
forum: General Help
---

### Post by 3l3vans on 2009-03-11
i was just wondering if any of you out there know how to install a mouse driver manually. i have the disk. so i don't need any info about HOW to find the driver. i am just curious about where Ubuntu keeps that stuff (so i can better understand how it is put together)

particularly

1.are all device drivers located in the same place?
2.if not where can i find a generic "map" of where they are located (if there is one)
3. are there ndiswrapper type applications for other devices?

     my assumption is that i just need to copy the driver from the disk and place it in the right directory where Ubuntu can find it on boot. and maybe write a shell script? (alas i barely know what i am talking about). i am trying to learn as much as i can about drivers and how they behave and where they are located for each device etc, so that when i jump into other flavors of GNU/Linux i have something to go on when my devices don't work.i've mastered my wifi card and now i am working on my wireless mouse. 
    
      so any info/links would be greatly appreciated...thanks! 3l

---

### Post by SunnyRabbiera on 2009-03-11
Drivers should not matter, most drivers are made for windows so wont work with linux.
Is this a mouse with more then 5 buttons?
Linux should be able to work with most common mice, I have seen linux work with up to 4 buttons.
But those multimedia mice can be tricky, the developers of those mice dont seem to know linux even exists...

---

### Post by MaxIBoy on 2009-03-11
Mice drivers are built right into the Linux kernel. Unless you're a power user and you've compiled your own kernel with those features disabled, it won't be a problem.

Unless, of course, you have something with umpteen controller buttons and scrollwheels, plus a sweatpants button, a "make me a sammich" button, and a "call me big papa" button.

---

### Post by 3l3vans on 2009-03-11
ok so the drivers are compiled with the kernal. so that means if i am trying a flavor of linux that doesn't see my mouse one option COULD BE to try a different kernal? i have only done that once. it just seems like there has to be away. thanks for the quick replies. 3l

---

### Post by MaxIBoy on 2009-03-11
Pretty much, if your mouse isn't recognized, you're gonna have to look at the kernel.

If the kernel is a recent version and it still doesn't work, file a bug report with the distro first. The developers of some distros do compile custom kernels.

---

### Post by 3l3vans on 2009-03-11
when its booting i can see it say something about a wireless mouse, but alas the mouse don't do nuttin! its not a big deal. i am just trying to learn as much as i can. thanks

---

### Post by MaxIBoy on 2009-03-11
Just google your hardware, there's probably a guide somwhere.

---

