---
title: "Video - Processor runs hot"
date: 2012-09-11
forum: Desktop Environments
---

### Post by Geffers on 2012-09-11
I am running 12.04 on a laptop with an Athlone x2 processor.

If I run a video using a live stream the fan is on most of the time, psensor shows at least one cpu at 100c with the other one hot also.

I think many users have heard of the RaspberryPi, ARM processor, Debian system and no fan, video plays perfectly, processor is warm to the touch only.

Any ideas why the laptop is getting so hot.

Geffers

---

### Post by youngunix on 2012-09-11
I have the same issue with my Gateway laptop, runs very hot and the fan is so annoying I was about to throw in the pool one day. I cleaned it thoroughly inside and out from dust and what not, I even replaced the thermal paste with a high quality one, and no luck. I don't know about you, but I have a very bad experience with AMD computers. 
In your case, I'd try to clean the computer, change the thermal paste if you can, and run a lightweight OS.

---

### Post by newb85 on 2012-09-11
My last machine had that same processor.  I don't recall fan issues, but I know the CPU regularly reached 105C.  At one point, I called the manufacturer.  Part of the conversation went something like this:

John: I'm sorry, sir, but if you're using a third-party operating system, that's outside the warranty coverage, and I cannot help you.
Me: So, if I boot into Windows and install software to monitor the temperature, could you help me then?
John: I'm sorry, but that would still be third-party software.
Me: And there's no provided software for checking the CPU temperature?
John: That's correct, sir.
Me: So, if I have any way of knowing that the temperature is way too high, you can't help me.
John: That's correct, sir.

I would vow never to buy from that manufacturer again, but last I heard, they were pulling out of the PC market altogether.

At the end of the day, my solution was to hide the temperature indicator and pretend nothing is wrong.  I ran it that way around 42 months before selling it to someone else (With Ubuntu installed, of course.)  It's still working great for him.  As far-fetched and scary as it sounds, 105C could be within the design specs for that CPU.

---

### Post by youngunix on 2012-09-11
Tell me about it, I'm never buying a windows machine again. I personally prefer to pay premium for them Apple jewels. A good friend of mine has about 10 apple products (family wise) some are about 4yrs old and they never ever had a single hick up. I've dealt with many windows laptops, some as steep as $3k and they all had issues and flaws. That's why I'm set to at least give Apple macbook a try.
Others may think otherwise and it all comes down to personal preference and experience.

---

### Post by Geffers on 2012-09-23
> **newb85 said:**
> 

At the end of the day, my solution was to hide the temperature indicator and pretend nothing is wrong.  I ran it that way around 42 months before selling it to someone else (With Ubuntu installed, of course.)  It's still working great for him.  As far-fetched and scary as it sounds, 105C could be within the design specs for that CPU.

:D love that solution, turn the sound up and I wont hear the fan either.

Geffers

---

### Post by Pergun on 2012-10-26
> **Geffers said:**
> I am running 12.04 on a laptop with an Athlone x2 processor.

If I run a video using a live stream the fan is on most of the time, psensor shows at least one cpu at 100c with the other one hot also.

I think many users have heard of the RaspberryPi, ARM processor, Debian system and no fan, video plays perfectly, processor is warm to the touch only.

Any ideas why the laptop is getting so hot.

Geffers
Are you sure the temperature is that high. I have read many post about high CPU temperature and I wonder if the temperature indicator is showing the correct temperature. I'm running a desktop with an old ASUS motherboard. When I start up and look in the BIOS configuration the temperature is OK. The fan controls the temperature at just above 50C. As soon as I boot up Ubuntu 12.04 the temperature indicated by "Hardware sensor indicator" by Alex Murray indicates 70C and it seems it is controlled by the fan at that level. Same thing if I start the computer from cold, the temperature indicates immediately 40C, when I expect something slightly above room temperature (20C). Additional info: I found out that it was not the CPU sensor I was reading. Once I got that right, the temperature matches the one in the BIOS.:redface:

---

