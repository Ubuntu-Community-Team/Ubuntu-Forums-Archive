---
title: "Won't boot unplugged"
date: 2008-06-26
forum: Desktop Environments
---

### Post by salefish on 2008-06-26
My laptop will only go to a black screen with a cursor when booting with power unplugged. Also if I unplug the power cord during operation, the screen freezes and i have to pull the battery out to get it to reboot. Ubuntu 8.04 works flawlessly when plugged in.
My configuration is
Toshiba L35-S2366
Intel T2060 1.6 GHz Dual Core
2GB PC4200 DDR SD Ram
NVIDIA 200M Integrated
80GB Hard Drive.
I am certain that someone else is having this problem but I can't find the post. Can someone please direct me to the right thread, or help me with this?

---

### Post by LeoSolaris on 2008-06-26
That could be a faulty battery.

It could be the power management daemon. You could search out the power management that you have installed through Synaptic, and reinstall it.

Just tossing a couple of ideas into the mix.

---

### Post by salefish on 2008-06-26
Thank you for the quick response. The battery is fine and reinstalling will not fix it. 
I tried migrating from Vista Ultimate, power management working fine, the day Ubuntu 8.04 came out. I had the same problem. I decided to give Ubuntu 7.10 a shot, power management worked perfectly as well as hibernate. Then I decided to go back to Vista and give the people on this forum time to figure out the solution.
I had found a post about 3 weeks ago that addressed the very problem. I did not bookmark it. This has turned out to be a very costly mistake in the way of time. I have spent some time trying to find it again with no success. 
If there is anyone that has seen this post let me know please.

---

### Post by p_quarles on 2008-06-27
Does the kernel recognize the battery at all? You should be able to get info with these commands:
```
acpi -t
```
and 
```
cat /proc/acpi/battery/BAT0/info
```
Also, does it still work correctly with Ubuntu 7.10? If so, the worst case scenario may be that you would need to install a custom kernel.

---

### Post by salefish on 2008-06-27
```
acpi -t
``` returns 

```
Battery 1: charged, 100%
Thermal 1: ok, 45.0 degrees C 
```

And it works perfectly with Ubuntu 7.10, I had it working for quit a while with Gutsy and got prematurely excited and installed Hardy the first day. Unfortunately my laptop does not work as well with Vista, it won't connect to the internet all the time, so it is not really a long term solution
Now the compiling a kernel solution sounds fun. I have to tell you though that I am fairly new to Linux and am willing to try things way beyond my ability. Though this is also a draw back, since "I am willing to try things way beyond my ability"

---

### Post by salefish on 2008-07-06
Well I tried the kernel upgrade, no change. Is there anyone out there that can help with this problem? Is there just another person that is having the same peoblem

---

### Post by risoknop on 2008-10-01
Hi,

sorry to bump this older thread but I have the exactly same problem (on the same laptop), and would like to know if you managed to find a solution or is it helpless?

If I don't get the lappy working unplugged, I will have to go back to older version of Ubuntu or to XP.

Just to clarify, battery is alright, works fine in XP, Vista, older Ubuntu versions..

---

### Post by risoknop on 2008-10-01
Anybody got any idea what could be causing the problem?

Note that I am 100% sure the problem is in Ubuntu (battery is fine, works alright in Windows and in older Ubuntu versions).

Could it help if I upgraded the kernel to let's say 2.6.27?

---

### Post by madnev on 2008-10-03
I have the same issue.  [http://ubuntuforums.org/showthread.php?t=936557&goto=newpost](http://ubuntuforums.org/showthread.php?t=936557&goto=newpost)

Are you running wcid?

---

