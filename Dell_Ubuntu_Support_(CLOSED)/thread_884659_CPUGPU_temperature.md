---
title: "CPU/GPU temperature"
date: 2008-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Hellbourne on 2008-08-09
Hi,

I have a D630/T7500/160GB7200RPM/Nvidia Quadro NVS Mobile 135.

1. What should the typical temperatures of the CPU and GPU be?
   a. Idle
   b. Working hard (computation, say with Mathematica/Matlab)
   c. Playing a movie

2. Is there a way to monitor all these temperatures in a simple manner, i.e. not with sensors, cat /proc/..., etc.

Thanks,

Amit.

---

### Post by Diggs808 on 2008-08-09
I really cant speak to the average temperatures on that system....however I can recommend a way to monitor those temperatures.  

I use a program called i8k and gkrellm to monitor my system temperatures.  

Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k

---

### Post by Hellbourne on 2008-08-09
Any chance you know why there isn't an AMD64 package of i8kutils and gkrellm-i8k for Hardy?

---

### Post by Diggs808 on 2008-08-09
> **Hellbourne said:**
> Any chance you know why there isn't an AMD64 package of i8kutils and gkrellm-i8k for Hardy?

Sorry...No.  You might check the source page for i8k....there might be some information there.

---

### Post by Diggs808 on 2008-08-09
> **Hellbourne said:**
> Any chance you know why there isn't an AMD64 package of i8kutils and gkrellm-i8k for Hardy?

I did some checking into this and it looks like there is not a version for 64 bit.  However it appears that some others have gotten a program called dellfand and it works on the 64 bit since it is not kernel dependent.  

[http://ubuntuforums.org/showthread.php?p=4069092](http://ubuntuforums.org/showthread.php?p=4069092)

---

### Post by slaanco on 2008-09-02
> **Hellbourne said:**
> Hi,

I have a D630/T7500/160GB7200RPM/Nvidia Quadro NVS Mobile 135.

1. What should the typical temperatures of the CPU and GPU be?
   a. Idle
   b. Working hard (computation, say with Mathematica/Matlab)
   c. Playing a movie

2. Is there a way to monitor all these temperatures in a simple manner, i.e. not with sensors, cat /proc/..., etc.

Thanks,

Amit.

did u get any temperatures with that program? and if than whet were the temps.

thanx a lot

---

### Post by mrynit on 2008-09-02
I use this for monitoring gpu, cpu(s) temps and fan speeds.

btw I have never had consistant fan behaviour with i8k

---

