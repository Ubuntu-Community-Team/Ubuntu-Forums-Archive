---
title: "Does PowerNow run by default?"
date: 2006-01-05
forum: General Help
---

### Post by rasmusbp on 2006-01-05
Hi, 

I'm using Breezy on my Centrino laptop, but the fan seems to be always on. So I've checked other threads out, and it seems PowerNow is the solution. However, I cannot seem to find out how to enable the thing - or is it on by default when you install breezy?

Thanks,
Rasmus

---

### Post by duminas on 2006-01-05
It may be installed by default, but on my machine it did not appear to be so.

To install it:

On the menu... *System > Administration > Synaptic Package Manager*

Search for _powernowd_ and install it. This should cause it to start upon bootup as well, but a quick way to check would be to install _bum_ from Synaptic as well. Once both are installed, run BUM (which should appear under the same menu you found Synaptic) and see if "powernowd" is listed and enabled.

If BUM (or Boot-Up Manager or something similar) does not appear in your menus, run ```
sudo bum
``` from the terminal to get it going.

---

### Post by rasmusbp on 2006-01-06
Many thanks! 

I installed bum and saw that powernowd indeed was enabled in my system. 
What then can be the reason that my fan is pretty much always on? 
In my previous XP life, I used "SpeedSwitch" to regulate fan speed/battery usage, and that stopped the noise somewhat. 

I have a Centrino CPU

Cheers
Rasmus

---

### Post by 23meg on 2006-01-06
You can check whether or not powernowd is running with ```
ps -e |grep powernowd
```If you get no output, it's not running. Type ```
cat /proc/cpuinfo |grep MHz

``` to see what speed your CPU is running at; is it the maximum speed?

---

### Post by rasmusbp on 2006-01-06
Thanks 23meg. 

It seems to be running: 

> 
rasmus@ubuntu:~$ ps -e |grep powernowd
 7825 ?        00:00:00 powernowd

And I don't know about speed, 600 out of 1600??

> rasmus@ubuntu:~$ cat /proc/cpuinfo |grep MHz
model name      : Intel(R) Pentium(R) M processor 1600MHz
cpu MHz         : 600.106

---

