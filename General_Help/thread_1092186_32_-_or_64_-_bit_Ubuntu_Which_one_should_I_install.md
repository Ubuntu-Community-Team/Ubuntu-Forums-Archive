---
title: "32 - or 64 - bit Ubuntu? Which one should I install?"
date: 2009-03-10
forum: General Help
---

### Post by Scubdup on 2009-03-10
I am already using 32-bit Ubuntu Intrepid Ibex 8.10

My computer currently has 1gb of RAM. (It's a P4 3gb Dell)

I have bought some more Ram (2x2 Gb) and want to install it and make the most of it.

As I understand it 32-bit Operating systems can only "see" 3 gbs of RAM and so to get the benefit of anything more than this 64-bit is the way forward.

My questions are:-

1) Can 64-bit ubuntu be installed on any machine or does it need a certain type of processor (a dual core or anything like that)? Will my P4 be able to cope with it?

2) Is 64-bit Ubuntu as easy to handle and configure and resolve as 32-bit?

3) Is installing/upgrading to 64-bit easy?

and lastly

4) Generally, would people say it's worth going from 32-bit to 64-bit? What are the other pros and cons I am not aware of?

Thanks for any help.

---

### Post by blazemore on 2009-03-10
A 32 bit operating system can only address about 4gb RAM, that includes graphics card.

If you're likely to use 4gb RAM, or use very CPU intensive applications, then use 64 bit.

Otherwise, it doesn't matter.

Personally I would install 64 bit, since it's slightly better at addressing memory, and Flash and Java aren't issues any more.

With specific answers:

1) You need a 64 bit processor
2) They're exactly the same
3) It's exactly the same process. You can't (don't bother trying) "upgrade". In theory you can, but stuff will break.
4) See points above.

---

### Post by cyclobs on 2009-03-10
well you need to have a 64bit processor for it to work with firstly.

64 bit linux requires a little more knolwage then 32 bit. mainly because some things just takes a little more to get working.

upgrading is no different to installing 32 bit, there is no real big changes between them.

pros: 64bit processing enables you to process more because of the 64 bits. so it's faster and it's able to read more memory.

cons: not everything fully supports it just yet, companys are lagging behind in compiling 64 bit applications but since this is all linux just about every program for linux can be compiled for 64 bit(this is what requires the extra skill. compiling certain programs and apps to get working)

thats pretty much it. i use 64 bit linux and it's just overall faster then 32bit and just about everything i use now days has 64bit versions so why not go with it.

hope that helps

---

### Post by skymera on 2009-03-10
I have used 64bit Ubuntu for a year now.
Ubuntu 9.04 64bit runs MUCH MUCH smoother than 8.04 64bit.

Wait for Jaunty to be released then run 64bit :)

---

### Post by 1numchucks on 2009-03-10
The Zsnes emulator works with the 32 bit with no alterations
or compiling. So I use it. But I do not know what I am missing 
out on. I tried to download it on a 64 bit ubuntu and it would
not let me because it said it was unsupported,

---

### Post by skymera on 2009-03-10
Firefox has a SNES emulator addon available from Mozillas Addons site, this has many games you can play and i do believe it works on Linux (Uses JAVA)

---

### Post by Scubdup on 2009-03-10
Thanks for the replies guys.
> **blazemore said:**
> You need a 64 bit processor> **cyclobs said:**
> well you need to have a 64bit processor for it to work with firstly.
How do I tell if my P4 is 64-bit?

If it is, then I think:-> **skymera said:**
> Wait for Jaunty to be released then run 64bit :)
I'll follow ^ that advice. You all seem to agree it's worthwhile.

Thanks a lot.

---

### Post by Yellow Pasque on 2009-03-10
If all you want to do is use more RAM, you can accomplish that by installing the server kernel on your current 32-bit install. It has PAE and can "see" up to 64GB of RAM.

Post output of:
```
cat /proc/cpuinfo
```

---

### Post by Scubdup on 2009-03-10
> **Temüjin said:**
> If all you want to do is use more RAM, you can accomplish that by installing the server kernel on your current 32-bit install. It has PAE and can "see" up to 64GB of RAM.

Post output of:
```
cat /proc/cpuinfo
```
Sounds interesting Temüjin. "All I want to do" really is get the most out of my system and the new RAM, be that by using 64-bit, or server kernel or whatever. I don't know enough to know the best option!

I will post that output you asked for when I get home and can use my ubuntu machine.

Thanks for the help!

---

### Post by skymera on 2009-03-10
> **Scubdup said:**
> Sounds interesting Temüjin. "All I want to do" really is get the most out of my system and the new RAM, be that by using 64-bit, or server kernel or whatever. I don't know enough to know the best option!

I will post that output you asked for when I get home and can use my ubuntu machine.

Thanks for the help!

If your P4 is 32BIT run the server kernel.
If its 64BIT run the 64BIT Ubuntu.

Win win?

---

### Post by 3Miro on 2009-03-10
There are many good 32-64 bit discussions on the x86_64 sub-forum. You might want to read some of those.

Other than that, I don't think P4 supports 64-bit, however, I might be wrong.

Download the 64-bit live CD and give it a shot. (just run it, not install)

---

### Post by skymera on 2009-03-10
> **3Miro said:**
> There are many good 32-64 bit discussions on the x86_64 sub-forum. You might want to read some of those.

Other than that, I don't think P4 supports 64-bit, however, I might be wrong.

Download the 64-bit live CD and give it a shot. (just run it, not install)

The later 65nm P4's are EM64T ready

---

### Post by Scubdup on 2009-03-10
> **3Miro said:**
> There are many good 32-64 bit discussions on the x86_64 sub-forum. You might want to read some of those.
Sorry - I did a cursory glance of that subforum before deciding it didn't really compare the two as rather discuss just the one 64-bit OS. I'll have a proper look now.

To prove I'm not completely useless at looking for stuff myself...(albeit too late to have the same advice from Temüjin!

[How to determine PENTIUM 4 , 64 bit capability ]("http://ubuntuforums.org/showthread.php?t=869060")

;)

---

### Post by Scubdup on 2009-03-10
> **Temüjin said:**
> If all you want to do is use more RAM, you can accomplish that by installing the server kernel on your current 32-bit install. It has PAE and can "see" up to 64GB of RAM.

Post output of:
```
cat /proc/cpuinfo
```

Hmmmm

```
sam@sam-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 1
cpu MHz		: 3191.931
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
bogomips	: 6383.86
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 1
cpu MHz		: 3191.931
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
bogomips	: 6383.97
clflush size	: 64
power management:

```
From what I've read it should say lm under flags, which it does. Is this right? Can the processor handle 64-bits?

Also, why has two sets of info come up?

---

### Post by Yellow Pasque on 2009-03-10
Yes, the processor can handle 64-bits.
Two CPU's are showing because your Pentium4 has HyperThreading, which makes it look like two CPU's to an OS.

---

### Post by Scubdup on 2009-03-11
> **Temüjin said:**
> Yes, the processor can handle 64-bits.
Two CPU's are showing because your Pentium4 has HyperThreading, which makes it look like two CPU's to an OS.
Awesome! Thanks Temüjin.

---

### Post by MaxIBoy on 2009-03-11
If your computer has 3.2 gigs of RAM or more, you'll need a 64-bit OS to recognize all of it. Otherwise, there will be a performance benefit from using the CPU in 64-bit mode (because of the extra registers that will become available,) but only for programs specifically compiled for the 64-bit architecture. It will also be somewhat more of a hassle to get things working on a 64-bit operating system, because not everything is compatible and not everything has been ported. For example, the Flash plugin didn't work on 64-bit Linux until only recently.

---

### Post by SunnyRabbiera on 2009-03-11
Mine I think is just a few months older then yours, so I dont think I can run 64bit:

```
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 2.93GHz
stepping        : 9
cpu MHz         : 2930.693
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips        : 5863.61
clflush size    : 64
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 2.93GHz
stepping        : 9
cpu MHz         : 2930.693
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips        : 5863.31
clflush size    : 64

```

---

### Post by 3l3vans on 2009-03-11
so when i cat /proc/cpuinfo what am i looking for? (concerning 64 and 32 bit)

---

### Post by SunnyRabbiera on 2009-03-11
I like to know too, according to Scubdup's specs we are very close.

---

### Post by Scubdup on 2009-03-11
From this thread:-
[How to determine PENTIUM 4 , 64 bit capability ]("http://ubuntuforums.org/showthread.php?t=869060")
...I would guess you can, SunnyRabbiera.

It seems to be that, after you "cat /proc/cpuinfo", if, under flags, there is an "lm" (short for "long mode"), then you can run 64-bit OSs.

Maybe wait for the experts though before going on my say so.

---

### Post by LowSky on 2009-03-11
If your CPU is on this chart then it is 64bit capable.

[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors#.22Prescott.22_.2890_nm.29_2](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors#.22Prescott.22_.2890_nm.29_2)

---

