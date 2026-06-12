---
title: "Benchmark Nexuiz 2.0 in dapper without logfile?"
date: 2006-07-06
forum: Gaming &amp; Leisure
---

### Post by SleepyHollow on 2006-07-06
Hi there,

i just wantet to compare the speed of nexuiz 2.0 in Win2K with the speed in dapper. There ist just this awful problem. Under win i just type:

timedemo demos/demo1.dem

What i get ist a file named benchmark.log and voila there are the fps-stuff.

But it doesn't work like this in dapper. If i type the same in dapper I got no logfile.

Any idea?

:confused:

---

### Post by DoktorSeven on 2006-07-06
It's saved in **/home/[youruser]/.nexuiz/data/benchmark.log**.

---

### Post by SleepyHollow on 2006-07-07
many thanks.

####____Ubuntu Dapper Drake 
date 2006-07-06 18:21:35 | enginedate 02:50:49 Jun 14 2006 | demo demos/demo1.dem | commandline ./nexuiz-linux-686-sdl -sndspeed 48000  | result 1910 frames 25.8480000 seconds 73.8935314 fps min/avg/max: 5.7471264/73.8935314/250.0000000

#####____Win2K
date 2006-07-06 11:41:50 | enginedate 02:49:48 Jun 14 2006 | demo demos/demo1.dem | commandline F:\games\nexuiz-2.0\Nexuiz\nexuiz-sdl.exe  | result 1909 frames 36.4960000 seconds 52.3071021 fps min/avg/max: 2.9940120/52.3071021/200.0000000

Nice results :mrgreen:

---

