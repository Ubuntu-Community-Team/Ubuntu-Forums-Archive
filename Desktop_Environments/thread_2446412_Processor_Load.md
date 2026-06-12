---
title: "Processor Load"
date: 2020-06-30
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-06-30
Folks,

Running 18:04 LTS on a Toshiba Laptop AMD A8-7410 APU with AMD Radeon R5 Graphics × 4 

If I am running Handbrake and converting video sysmon shows all 4 processors at around 100%

Now I may be completely wrong here but all 4 going at around 100% each would be getting quite hot so I wanted to slow it down a wee bit.

Used cpulimit to ease the processor usage but the percentage selected bears no resemblance to what sysmon shows.

If I issue cpulimit -p <PID No> -l 50 the processors all drop to around 25% - if I select 75% sysmon shows below 50 and strangely if I select 99 sysmon shows processor load as around 50%

I appreciate there are other processes being used but the cpulimit percentage limit doesn't appear to bear much resemblance to what actually happens.

Geoff

---

### Post by TheFu on 2020-06-30
I just run handbrake with a lower priority *nice 10 {name of program}*, so everything else gets CPU first. There's also ionice. 

As for heating, that's why our systems have fans and heatsinks. If they can't handle the thermal load, that's a problem that needs a different solution.

If I have batch processing to be done, I'll use taskspooler to limit those to 1 task per queue. For years, I'd create scripts to run stuff in order and guess a delay period between those tasks. Then discovered taskspooler and all that management overhead was gone. The system would be kept busy, but not so busy as to be crazy loaded. Plus, any jobs can be nice'd as part of the TS submission.

Just read the manpage for cpulimit.  Seems like a brute force method. It uses stop/start process management signals to have handbrake start and stop constantly.  Handbrake is multi-threaded, so those different signals are sent to the main thread and child thread can take some time before they check in to see the signal. By that point, the 'start' signal has been sent. It isn't an exact thing.  I'd call it an interesting hack, since it would be great to see it use the Linux scheduler for CPU limiting, not start/stop signals.

---

### Post by Geoff_Lane on 2020-06-30
> **TheFu said:**
> I just run handbrake with a lower priority *nice 10 {name of program}*, so everything else gets CPU first. There's also ionice. 

As for heating, that's why our systems have fans and heatsinks. If they can't handle the thermal load, that's a problem that needs a different solution.

.

Thanks for prompt reply, heating hasn't indicated a problem, just using experience of other things, heating is an enemy of electrical items and my logic says all processors running at 100% equals heat.  Strangely I don't often hear the fan coming on and if it does it doesn't stay on for long so guess it is coping fine.

Long time since I've used a desktop machine, they are so much more flexible re cooling.

I'll try your 'nice' suggestion but guess if it is just a priority then it'll still take a high CPU unless something else wants it.

On my RaspberryPi I can check the CPU temperature but don't think I can on this laptop, BIOS is pathetic.

Geoff

---

### Post by TheFu on 2020-06-30
> **Geoff_Lane said:**
>  
On my RaspberryPi I can check the CPU temperature but don't think I can on this laptop, BIOS is pathetic.

Nice won't slow down any CPU, it just controls which processes have higher or lower priority.

The 'sensors' package should be able to get CPU provided temperatures from any AMD or Intel CPU.  I had a Core i7 CPU that would slow itself down due to thermal heating. It was built in 2009. The syslog would have those events. No OS stuff required. It is built-into the CPUs.  Since before 2000, CPUs have protected themselves in that way.

---

### Post by CatKiller on 2020-06-30
> **TheFu said:**
> As for heating, that's why our systems have fans and heatsinks. If they can't handle the thermal load, that's a problem that needs a different solution.

Exactly this. That processor has a maximum temperature of 90 °C. If your cooling solution doesn't keep the processor below that temperature at load, the processor will throttle to reduce the load so that it *does* stay below that temperature. That all happens automatically; you don't need to manually strangle your processes. You can monitor both the temperature and clock speeds to see if that's happening.

---

