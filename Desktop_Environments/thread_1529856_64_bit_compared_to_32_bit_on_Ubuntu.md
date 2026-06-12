---
title: "64 bit compared to 32 bit on Ubuntu?"
date: 2010-07-12
forum: Desktop Environments
---

### Post by sam-c on 2010-07-12
I recently understood that this Lenovo Desktop is a 64 bit Machine.
What can you tell me about Ubuntu and 64 bit and compare with 32 bit?
Thanks
Sam:popcorn:

---

### Post by mikewhatever on 2010-07-12
There is a dedicated 64bit subforum here, but really, all you need to know is in that subforum's sticky.
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by lovinglinux on 2010-07-13
I have been using 64bit since Karmic, but today I decided to give the 32bit a try, because of the lack of support for flash 64bit and Tracemonkey on Firefox.

So far it feels snappier than the 64bit, although my browsers benchmarks shows otherwise. I'm currently compiling Firefox, which is an intensive task and I can still use the cube animation perfectly. It spins smoothly, like if I wasn't running anything else.

This is really weird, because most people will tell you that the 64bit is better for intensive tasks like compiling software and encoding video.

Later I will make some tests with virtual machines. Then I will be able to confirm if 32bit is indeed running better.

---

### Post by 3Miro on 2010-07-13
With the exception of Flash (which is fixable in several different ways) and some win 32 codecs (which is also fixable) 64-bit is overall a bit faster than 32-bit (this counts for both Linux and Windows, Mac is only 64-bit anyway). Other than that, I only know of some 64-bit printer issues for some models only.

For video/audio encoding, 64-bit is much faster, for regular apps people put it to 10 - 20% faster. I have been using 64-bit Linux exclusively for over two years now and I am very happy about it.

@mikewhatever: the 64-bit forum is closed, there is no more need for dedicated 64-bit section. You can still read the old posts (and most of them are indeed old), but you cannot post new things. People should use the general forum instead with a 64-bit for their threads.

@lovinglinux: compilation is CPU intensive, the cube is GPU intensive. To make a benchmark, time how long it takes to compile FireFox under 32-bit and then  under 64-bit. Also, virtual machines are not real benchmarks. If you are using a lot of virtual machines and you find that they work better under 32-bit, that is a good reason for you to use 32-bit, however, this is no "real" benchmark.

---

### Post by lovinglinux on 2010-07-13
> **3Miro said:**
> @lovinglinux: compilation is CPU intensive, the cube is GPU intensive. 

Yes, I know, but there is still some increase in CPU usage, from xorg and kwin for example.

> **3Miro said:**
> To make a benchmark, time how long it takes to compile FireFox under 32-bit and then  under 64-bit.

Practically the same.

> **3Miro said:**
> Also, virtual machines are not real benchmarks. If you are using a lot of virtual machines and you find that they work better under 32-bit, that is a good reason for you to use 32-bit, however, this is no "real" benchmark.

Yes, off course they are not. The benchmarks I was referring too is the Peacekeeper browser benchmark. Nevertheless, it is while using virtual machines that my computer suffers the most. So if it starts to work well in 32bit it will be a good indication that the system is running better.

---

### Post by 3Miro on 2010-07-13
> **lovinglinux said:**
> 
Yes, off course they are not. The benchmarks I was referring too is the Peacekeeper browser benchmark. Nevertheless, it is while using virtual machines that my computer suffers the most. So if it starts to work well in 32bit it will be a good indication that the system is running better.

A 32-bit guest would probably work better under 32-bit host, but I don't think 32-bit hosts can support 64-bit guests. When it comes to virtual machines, the things that matter most are RAM and cores. 64-bit apps do use a bit more RAM than 32-bit ones, so depending on the amount of memory that you might have, this can make a difference. At the same time, if you are compiling 32-bit Firefox under 32-bit Linux vs 64-bit FF under 64-bit Linux those are not the same tasks and hence it is not a fair benchmark.

At any rate, if 32-bit works for you, then by all means use it. On the other hand, there is no reason to be afraid of 64-bit either.

---

### Post by lovinglinux on 2010-07-13
> **3Miro said:**
> At any rate, if 32-bit works for you, then by all means use it. On the other hand, there is no reason to be afraid of 64-bit either.

I have been using 64bit since Karmic without issues. I was happy with it. Nevertheless, it wasn't perfect. That's the reason I decided to test the 32bit. So far is working better on my machine.

---

### Post by mildlyAmused on 2010-07-13
> **3Miro said:**
> 64-bit apps do use a bit more RAM than 32-bit ones, so depending on the amount of memory that you might have, this can make a difference. 


I wonder how much memory you have to have before 64-bit has the advantage.  Whatever it is, my eMachine doesn't seem to qualify. :(

---

### Post by lovinglinux on 2010-07-13
> **3Miro said:**
> A 32-bit guest would probably work better under 32-bit host, but I don't think 32-bit hosts can support 64-bit guests.

As long as you have the proper hardware you can. I'm running Ubuntu 64bit guest right now.

---

### Post by 3rdalbum on 2010-07-14
> **sam-c said:**
> I recently understood that this Lenovo Desktop is a 64 bit Machine.
What can you tell me about Ubuntu and 64 bit and compare with 32 bit?

64-bit Ubuntu is compiled from the same source code as 32-bit Ubuntu. It's the same except for the internal use of 64-bit numbers instead of 32-bit numbers. From the user's point of view there's no difference, except they may notice that the 32-bit edition only sees/uses 3.3 GiB of RAM or so (this is a limitation of 32-bit in general). They may also notice that 64-bit Ubuntu uses a bit more RAM than 32-bit; if you're in a low memory situation then stick with 32-bit.

---

