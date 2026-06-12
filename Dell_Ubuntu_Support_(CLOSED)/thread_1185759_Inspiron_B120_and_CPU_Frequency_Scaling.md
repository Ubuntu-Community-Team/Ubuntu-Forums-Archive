---
title: "Inspiron B120 and CPU Frequency Scaling"
date: 2009-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MKR. on 2009-06-12
The newest entry for my laptop in the ubuntu hardware list is for Edgy, and it says CPU frequency scaling doesn't work. Does anyone know if this is still the case?

Also, does hibernation work? I can't really test this since I don't have room to dual boot.

---

### Post by coffeeaddict22 on 2009-06-12
Hi,
Welcome to Ubuntu!

Laptop support has got a heap better in the last 12 months, so anything related to Edgy is a touch out of date.  Your easiest option is to boot up off the Live CD (stick the CD in, reboot, and make sure the BIOS is set to allow booting off the CD drive before the hard drive); that'll give you a working Linux setup, albeit with default drivers, and you can test your hardware in that.

---

### Post by MKR. on 2009-06-12
> **coffeeaddict22 said:**
> Hi,
Welcome to Ubuntu!

Laptop support has got a heap better in the last 12 months, so anything related to Edgy is a touch out of date.  Your easiest option is to boot up off the Live CD (stick the CD in, reboot, and make sure the BIOS is set to allow booting off the CD drive before the hard drive); that'll give you a working Linux setup, albeit with default drivers, and you can test your hardware in that.

What program will tell me how fast the CPU is going? I used to use Ubuntu before my classes started requiring Windows-bound stuff a couple of years ago, so I don't know what sort of applications have become standard.

---

### Post by coffeeaddict22 on 2009-06-12
If you're using the Gnome desktop, there's a panel applet that'll do it- appropriately named system monitor.

---

### Post by MKR. on 2009-06-13
> **coffeeaddict22 said:**
> If you're using the Gnome desktop, there's a panel applet that'll do it- appropriately named system monitor.

That's not what I meant, but I did find what I was looking for.

It looks like both the top speed and current speed are stored in /proc/cpuinfo.

---

### Post by MKR. on 2009-06-13
Well this is weird. I have this processor: [http://ark.intel.com/Product.aspx?id=27143](http://ark.intel.com/Product.aspx?id=27143)

And while it says it doesn't support Speedstep, the fan does change speed depending on CPU usage under Ubuntu and XP. Am I just misunderstanding what frequency scaling is?

---

### Post by coffeeaddict22 on 2009-06-13
Not sure what you understand frequency scaling to mean.  The fan hasn't got a lot to do with it, although when the chip's working harder it generates more heat.
Essentially, frequency scaling is about turning off part of the CPU when there is insufficient load to require it.  See [this Wikipedia article]("http://en.wikipedia.org/wiki/Dynamic_frequency_scaling") for more details.

---

### Post by MKR. on 2009-06-13
> **coffeeaddict22 said:**
> Not sure what you understand frequency scaling to mean.  The fan hasn't got a lot to do with it, although when the chip's working harder it generates more heat.
Essentially, frequency scaling is about turning off part of the CPU when there is insufficient load to require it.  See [this Wikipedia article]("http://en.wikipedia.org/wiki/Dynamic_frequency_scaling") for more details.

The way I understood it is that normally a CPU was being utilized 100% by the OS, and it handed off capacity to processes as needed, while frequency scaling made the CPU slower when full capacity wasn't needed.

---

### Post by coffeeaddict22 on 2009-06-14
Well, yes and no.  Part of what the OS does is manage all system resources, CPU time included.  However, no OS is written so badly that the CPU has to work 100% of the time; after all, at the end of the day it's just a set of programs, and most of the time it sits waiting for you to click on something/ type something in.  It's what happens during idle times that frequency scaling applies to.

---

### Post by MKR. on 2009-06-14
> **coffeeaddict22 said:**
> Well, yes and no.  Part of what the OS does is manage all system resources, CPU time included.  However, no OS is written so badly that the CPU has to work 100% of the time; after all, at the end of the day it's just a set of programs, and most of the time it sits waiting for you to click on something/ type something in.  It's what happens during idle times that frequency scaling applies to.

I guess it has just been a long time since I read the wiki on the system idle process, because it looks like it's a normal thing on any OS, and is just to ensure that the CPU is only doing [as much as it needs to do]("http://www.codinghorror.com/blog/archives/000873.html").

So I guess the point of frequency scaling is to reduce the number of HLT commands needed.

---

### Post by MKR. on 2009-06-17
I spent a little more time in the LiveCD and tried both gnash and flash. Stumbleaudio and Pandora crash the browser whether I'm using gnash or flash. Is that normal for the LiveCD?

I didn't think to try Youtube before the system hardlocked during an installation. I know the LiveCD can be touchy, so I'm not too concerned.

---

