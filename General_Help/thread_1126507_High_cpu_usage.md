---
title: "High cpu usage"
date: 2009-04-15
forum: General Help
---

### Post by Net_Exploder on 2009-04-15
Hello. I'm new to the Linux world and I'm experiencing some problems. I get high cpu usage for just about every process I open. It isn't centered to a specific program. For example, if I open firefox, cpu usage will go to 50-60% for 1-2 seconds. Or if I open deluge or openoffice I get the same result. Also if I watch streaming video or downloaded videos I get 100% cpu usage for firefox and mplayer accordingly. I'm not sure what's the problem but I have tried debian, opensuse and finally ubuntu and I get the same issue. The cpu usage is low when the system is idle so it shouldn't be some process eating up cpu constantly.I dual boot ubuntu and windows xp where I have no such problem.

My system is: Intel pentium D 2.66ghz, nvidia geforce 6200 LE, 2gb ram, Ubuntu 8.10 interpid. I'm using the top command to see cpu usage.
Thank you.

---

### Post by perrti-y02 on 2009-04-15
This is a bit of a guess but I suspect that it is in fact that the processor is having too much pushed through it at one time. The Front Side Bus on the 2.66 Ghz is only 566 Mhz so I would guess that this is simply the program's initial requirement.
I think you get a spike as you open a program because lots of new processes need to be started. As for streaming and downloading, this is putting a constant load onto the cpu becuase it is computing lots of data in a stream.

I may be totally wrong but that is how I see it.

---

### Post by 3Miro on 2009-04-15
You always get a spike when a new program opens for the first time. There might be an issue if the spike doesn't come down. (There is a spike in windows as well, I have monitored that).

---

### Post by Kain000 on 2009-04-15
> **perrti-y02 said:**
> This is a bit of a guess but I suspect that it is in fact that the processor is having too much pushed through it at one time. The Front Side Bus on the 2.66 Ghz is only 566 Mhz so I would guess that this is simply the program's initial requirement.
I think you get a spike as you open a program because lots of new processes need to be started. As for streaming and downloading, this is putting a constant load onto the cpu becuase it is computing lots of data in a stream.

I may be totally wrong but that is how I see it.

I agree, if indeed your motherboard is set to a FSB of only 566Mhz, thats not alot of bandwidth by todays standards.  a new motherboard is usually 1066 Mhz FSB from the start, and some come at 1333mhz.   

I agree with perrti, your system is just cramming all those calculations into that 566Mhz sized hole and it's loading up your cpu.  If you can (depends on the motherboard manufacturer) overclock your FSB freq to something more substantial then you will see an improvement but thats about all you can ask for.

---

### Post by Kain000 on 2009-04-15
also when a program is opened for the first time your kernal puts it into RAM and that will take some cycles up.  If your system is sluggish all the time then your bottle neck is going to be the cpu FSB.

---

