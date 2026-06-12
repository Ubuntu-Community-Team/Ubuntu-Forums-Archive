---
title: "lm_sensors doesn't change values"
date: 2009-03-19
forum: General Help
---

### Post by Spectre5 on 2009-03-19
Hello all!

I have a question about lm_sensors.  I installed the "Sensors Applet" to use for monitoring my temps/fan.  The fan speed definitely seems to work correctly and I see it occasionally change.  The GPU (Nvidia 9500) also seems to update and varies between about 28C and 31C.

However, the CPU temperatures (dual core, E8400) don't seem to ever update.  They stay at 37C and 40C all the time.  I've never seen them change - no matter how many apps I am running or how hard the computer is being pushed.  This doesn't seem right to me.

Does anyone have any idea why this wouldn't work?  I do notice that if I go into the "PC Health" in the Bios that the CPU temps seem to be incorrect there (they say ~17C which is way to low...although it does fluctuate between about 16C and 18C).  The CPU is using the standard CPU cooler that came with the E8400.

I'd really like to know that I am getting good sensor values, is there any good way to know what the temperatures really are?

---

### Post by Spectre5 on 2009-03-19
I guess I should also have mentioned that the motherboard is a Gigabyte:
GA-G31M-ES2L

---

### Post by rsambuca on 2009-03-19
I have an E8400 as well, but with a Gigabyte GA-EP45-UD3R motherboard.  I have overclocked the cpu up to 3.779 GHz from the stock 3.0 GHz.

Using lm-sensors, my idle temps are 41 C with a Scythe Mini Ninja and low speed fan.  When I did a 24 hour stress test, the temps went to mid 50's with 100% cpu utilization for 24 hours.

Something definitely seems incorrect with your numbers, since they sound lower than room temp (unless you happen to be living in an ice-box).

---

### Post by Spectre5 on 2009-03-20
> **rsambuca said:**
> I have an E8400 as well, but with a Gigabyte GA-EP45-UD3R motherboard.  I have overclocked the cpu up to 3.779 GHz from the stock 3.0 GHz.

Using lm-sensors, my idle temps are 41 C with a Scythe Mini Ninja and low speed fan.  When I did a 24 hour stress test, the temps went to mid 50's with 100% cpu utilization for 24 hours.

Something definitely seems incorrect with your numbers, since they sound lower than room temp (unless you happen to be living in an ice-box).

It is pretty cold here!  Haha...but ya, something seems wrong with them.  For NO load I could believe 37C (Core0) and 40C (Core1).  But under load, they should go up.  I'd also expect some natural fluctuation, but I'm not seeing ANY change.

The ~17C that the Mobo reports in the PC Health screen of the bios is definitely wrong...that is colder than room temp (sometimes anyways)

---

### Post by Spectre5 on 2009-03-23
Hm....weird.  I still don't know what the problem is - I'm guessing something to do with the mobo.  I was just using my computer like normal and then saw that lm-sensors (via the Gnome Sensor Applet) showed that the CPU core's (0 and 1) were at 42C.  Thinking that this was good (maybe it would start working), I restarted my computer to look at the temps in the bios PC Health.  It used to always show 17-18 and now it was varying between 24-25C.  I then restarted my computer again to boot Linux again and the lm-sensors report the 37/40 for core 0/1 again.  Looking in the bios is back to the 17-18 again.  So weird??

---

### Post by norwoods on 2009-03-23
you probably need to run sensors-detect     see

[http://www.lm-sensors.org/wiki/man/sensors-detect](http://www.lm-sensors.org/wiki/man/sensors-detect)

---

### Post by Spectre5 on 2009-03-23
> **norwoods said:**
> you probably need to run sensors-detect     see

[http://www.lm-sensors.org/wiki/man/sensors-detect](http://www.lm-sensors.org/wiki/man/sensors-detect)

Yes, I have run this.  I'm thinking it must be a mobo problem as the bios reports incorrect values too.  Maybe I should update the bios...but they only give an exe for updating so I'll have to find out how I can do it via Linux...(maybe with FreeDos if the exe is a dos program...)

---

### Post by norwoods on 2009-03-24
you can update your gigabyte bios running the bios.  you do not need any operating system, windows, dos or linux.

---

### Post by Spectre5 on 2009-03-25
> **norwoods said:**
> you can update your gigabyte bios running the bios.  you do not need any operating system, windows, dos or linux.

Ah ya, I just realized this today...now I just need to get a new usb drive to put the file onto (my old one has burned out)...I hope this fixes the problem!

---

### Post by Spectre5 on 2009-04-27
Just a FYI - the newest bios didn't fix this problem and I still have it...the bios now reports 25C or 26C...but still doesn't change from that...even if I run an intensive game, restart and look at the bios...

lm-sensors reports 37C and 40C for the temps still...and they never, ever change.  There is another temp that is reported (called temp3) that does change...but it is 18C at idle which is way to low.  It does increase with CPU usage, but INSTANTLY goes back to 18C when I stop doing something intensive (i.e. quit a game).

This is very frustrating!  It seems there are a number of people that have problems with the temperature readings with the E8400...

---

### Post by aboutblank on 2009-05-24
Hello,

I have a GA-EP45-UD3R and I believe lm-sensors is now working.

First, try updating the BIOS to version F9. The comment for the update was about the temperature sensor.

Second, make sure you are really loading the CPU. Try downloading prime95 and doing a small fft torture test.

---

### Post by Spectre5 on 2009-05-24
> **aboutblank said:**
> Hello,

I have a GA-EP45-UD3R and I believe lm-sensors is now working.

First, try updating the BIOS to version F9. The comment for the update was about the temperature sensor.

Second, make sure you are really loading the CPU. Try downloading prime95 and doing a small fft torture test.


That is a different motherboard.  I have the F8 bios on mine (GA-G31-ES2L) and there is a beta F9 bios, F9c.  All it says for the comment is beta, but I don't see anything about it affecting the temp sensors.  I'm not sure I want to try out a beta bios...I'm waiting for it to become stable.

---

