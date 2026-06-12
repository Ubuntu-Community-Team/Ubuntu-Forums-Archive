---
title: "HELP!!! high laptop fan speed when on AC power"
date: 2010-02-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spiritson on 2010-02-20
My Dell laptop is studio 1458 with Intel Core i3 350M 2.27ghz and ATI 4530 gfx card.

UBuntu Karmic 2.6.31-20

One thing i noticed is when running ubuntu on AC power(cord plugged in)the laptop fan speed never seems to come down. It runs constantly even when the CPU is idle. 
And for minor cpu usage the fan speed fires up.

When cord is plugged out and laptop runs on battery , immediately the laptop fan speed comes down and only when the cpu is stressed it rises accordingly .

Note
: This does not happen in windows 7.When plugged in fan behaves normally increasing when stressed and decreasing when idle. Same behaviour on battery.

BUt UBUNTU when ac cord is plugged in always laptop fan speed is high even when idle. 

Is there any solution for this problem? its very important that its the only thing stopping me to wipe windows 7.

PLss HELP

---

### Post by RedSingularity on 2010-02-20
Have you installed graphics drivers for ubuntu?

---

### Post by 1337-h4xx0r on 2010-02-20
what version of Ubuntu are you running? if it is 9.10, it is buggy and glitchy. This may just be the problem.

---

### Post by spiritson on 2010-02-21
yeah i installed Ati graphics driver lates 8.69 download from amd official website.

And also is ubuntu 9.10 that bad with laptops if so which ubuntu do you suggest in which there is no problem like this 

Jaunty?
Intrepid?

I cant go back to hardy because its too old

Is there any other workaround.what seems to cause this problem??

---

### Post by RedSingularity on 2010-02-21
I have jaunty on my laptop.......it runs great.

Oh and next time you want to install drivers, use the ones ubuntu recommends.  In your case do this in a terminal...

sudo apt-get install xorg-driver-fglrx

---

### Post by spiritson on 2010-02-21
Problem is solved!! seems to be problem in default generic kernel.

I compiled my own kernel 2.6.32.8 with all acpi related  selections included in compiling and problem is gone.

---

### Post by whatname on 2010-03-11
> **spiritson said:**
> Problem is solved!! seems to be problem in default generic kernel.

I compiled my own kernel 2.6.32.8 with all acpi related  selections included in compiling and problem is gone.

Hi, could you please describe how did you do that? I have a similar problem unfortunately.

---

### Post by lz1dsb on 2010-03-12
> **spiritson said:**
> Problem is solved!! seems to be problem in default generic kernel.

I compiled my own kernel 2.6.32.8 with all acpi related  selections included in compiling and problem is gone.

Yeah, for me it would be quite interesting too. I always wanted to know how this is done. I haven't found the time yet to try it...

---

