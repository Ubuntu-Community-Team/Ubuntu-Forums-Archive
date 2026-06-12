---
title: "hard crashes while running matlab"
date: 2009-06-02
forum: General Help
---

### Post by evencoil on 2009-06-02
This might be slightly inappropriate as its more general computing...but involving a Ubuntu system! I am trying to run a long, computationally intensive program in MATLAB on an Ubuntu 8.10 64-bit machine. I am running the program in parallel using the parfor (parallel for loop) in MATLAB and the processor is an Intel Q6600 quad core duo. This ends up using 100% of all four cores.

I am getting fairly frequent hard freezes which require a power on/power off to reboot (RSEIUB doesn't do anything). No flashing lights on the keyboard to indicate a kernel panic.

Originally I was having this problem and noticed that the temperatures were climbing into the upper 60Cs before a crash. After installing a better heatsink the temperatures do not rise above the mid 50Cs at 100% load. Supposedly this is a quite safe full load temperature for this type of chip.

None of the standard system logs give me any information about the crashes.

I'm done MEMTEST overnight and not had any problems.

The power supply is probably adequate but its hard to tell.

Any suggestions as to what could be causing this and how I can further troubleshoot it?

---

### Post by wpshooter on 2009-06-02
Are you positive that it is not some flaw in the MATLAB software application that is causing the lockup, i.e. have you ran this same application on another computer without having these lockups ?

P. S. - Are you getting any freezes of this type when you are not running this program and just doing other things or if the computer is just at idle ?

---

### Post by evencoil on 2009-06-02
That's really the reason I posted this in the ubuntu forum...It seems very possible that there's a flaw with MATLAB and/or MATLAB's parallel programs and/or the way either of these perform in Ubuntu 8.10. (However, doesn't it seem suspicious that its a hard crash for which nothing is written to the syslog? Doesn't that tend to indicate a very basic hardware failure?)

Unfortunately I don't have any way to test this long term on another multi-core machine, let alone a Linux one, let alone an Ubuntu 8.10 one.

I can tell you the following: If I run the program using a regular for loop (i.e. without parallelization) then things seem stable. But, I also notice that not all of the cores are running at 100% all the time when I'm doing this, so that doesn't really isolate the problem. The temperatures stay cooler as a result and I would assume less power is being used.

I don't have this problem with any other application or when at idle. Only when running MATLAB under extreme stress.

Is there another program I could run that would keep my cores at 100%? That would seem to isolate MATLAB vs. hardware if I don't experience a crash during that.

---

### Post by wpshooter on 2009-06-02
Get some type of external desktop or another type of FAN and let it blow as directly on the machine as possible, as it is running the program in the mode that is giving you the problems and see if it still freezes.

Also, what program are you using to monitor the temperatures ?

Can you get xsensors to run on it while it is running your application and watch the xsenrsors temperature on the CPU to see if it freezes when it gets to a particular temperature.

I think there were some problems with getting xsensors to running on some of the more recent versions of Ubuntu but I know that it has been fixed in Jaunty, because it is running fine on this machine I am typing on.

---

### Post by evencoil on 2009-06-03
I'm running sensors-applet so I can see all of the temperatures of the cores (and what they are when it freezes). The last time I tried the cores were running at 57-58 celcius 100% load for 5 hours and then suddenly I had a hard freeze. Oh, and the sensors appear to be accurate since after I have a freeze I can immediately reboot and check the temperatures in the BIOS; they match.

I figure I out to get a couple more case fans anyway since the circulation is pretty bad currently. I'll report back how things work out after I've dropped the core temperatures down 5 degrees more or so. But suppoedly Intel Core Duos don't start to have problems until the low 70s...so I'm skeptical.

---

### Post by wpshooter on 2009-06-03
I would not go and buy any more case fans until I knew this was actually the problem.  I would just get a large floor/box or desk fans to blow on it while it is running.

---

### Post by evencoil on 2009-06-05
Tried a floor fan. This time the temperature maxed out at 54 but still had a crash.

---

### Post by wpshooter on 2009-06-05
> **evencoil said:**
> Tried a floor fan. This time the temperature maxed out at 54 but still had a crash.

Hmmmmmm.  Really does not sound like temperature problem.

What is the wattage rating of your power supply ?  I am hoping you are going to say at least in the 500-600 watt range.

I notice that on the system requirements for this MATLAB software, that there is a 1gb (and preferrably) 2gb memory recommendation.  Do you meet the RAM and other system requirements for MATLAB ?

---

### Post by evencoil on 2009-06-07
the power supply is 500W and I have plenty of RAM (4gb, only about 1.5 GB is being used during the process).

I'm in the process of rewriting my program in Fortran (for speed since MATLAB is quite slow). I'll let you know if I still get the crashing in that case...

---

