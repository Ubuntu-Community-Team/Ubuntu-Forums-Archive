---
title: "[SOLVED] Inspiron 1150 heats up to ~50-55 C even when idling"
date: 2007-09-08
forum: Dell  Ubuntu Support
---

### Post by tak1150 on 2007-09-08
I have an Inspiron 1150 with pentium 4 CPU, 730 MB RAM.
It heats up to 50-55 C even when the computer is idling. I used to have beagle and it would bump up the heat to 60-70 C when idling, so I switched to tracker and it's better.

But still 50-55 C when idling is a bit too much. In fact it has physical effect on my hands + arms. I have gotten very mild low-temp burns from my laptop a couple of times (esp. if I have to type a lot).

It seems like the left hand side (where CD-R / DVD-ROM drive is) is the hottest spot besides the CPU. I'm at a loss to explain this phenomenon. It's been a while since I erased Win-XP, but I don't think it got this hot.

Thanks for your help in advance.

---

### Post by Packrat1947 on 2007-09-08
Hi,
Here's a possible solution for laptop heating problems.  This may not help you, but someone else may benefit.

Thermaltake Mobile Fan II External USB Cooling Fan -

Amazon has this product for $10.00.  When I do heavy duty malware cleaning, etc. on customer's lappys, I set the laptop on .75 by .75 sticks and have this blow in from the back.     It only runs when the computer is up, and no wallwart is needed.  Variable speed too.  Neat.  

Cheers,
Packrat1947

---

### Post by tak1150 on 2007-09-09
thanks for replying.

I have thought about getting a cooler mat w/ fans (via USB), but none of them seem to have the design so that I can actually place the thing on my lap and still have the cooling function. The fans would be blocked by my lap and they would not work on soft surfaces.
I would not want to pay for one of those unless I get this feature.

Anyways, I think that it's at least partially a software problem. Which if it is true, it can be fixed without buying new hardware (which I like):)

---

### Post by HangLoose on 2007-09-10
hmmm, i just posted something really close to your problem ;) Even when I booted the system after an entire night without using it the temperature went up to 50c.

Now when Im with Netbeans, firestarter, pidging, firefox and banshee it goes to 47c ;)

You could try to alter the cpu frequency of your laptop to a lower one. Mine can go till 1.6Ghz in each core and its running now at 1Ghz.

I dont need full speed of processor, and mostly people also dont use everything, cos I also have 2Gb of ram.

---

### Post by Beggar on 2007-09-11
I was having a very similar problem on my dell e1505, it turns out my fans just were not turning on. I installed I8k and gkrellm (both in the repos) after someone mentioned it on these forums, then just set the temps at which the laptop should run and I could suddenly hear the fans. Very rarely does my laptop exceed 55c now. Might be worth looking into.

---

### Post by tak1150 on 2007-09-11
> **Beggar said:**
> I was having a very similar problem on my dell e1505, it turns out my fans just were not turning on. I installed I8k and gkrellm (both in the repos) after someone mentioned it on these forums, then just set the temps at which the laptop should run and I could suddenly hear the fans. Very rarely does my laptop exceed 55c now. Might be worth looking into.

I thought about using software to control the fans rather than letting the BIOS, but I was a bit scared of the possibility that the program fails and let the CPU get really hot. I will look into the 2 things you mentioned though. Thanks!

---

### Post by tak1150 on 2007-09-11
gkrellm rocks!
I just hope that this program won't crash on me. but so far it's great!

One remaining problem;
For some reason, the left side of the laptop (where the CD-R / DVD-ROM is and where my left hand rests) gets hotter than CPU sometimes. I don't have any CD / DVD in there.

Do you know how to find out what process is possibly using CD-ROM drive? I have opened up this laptop (had to switch the motherboard), and I don't remember seeing anything other than the CD drive at the spot I'm referring to. So I think it has to be the CD drive... ???

Can you think of why this might be happening?
Thanks!

---

### Post by Beggar on 2007-09-11
Could that be your graphics card/gpu? 

I am given two options in gkrellm (which, in a month of use I have never seen crash, and have never had a single complaint about it), one for left and right fan. Then I just configure them separately. Do you see something similar?

---

### Post by tak1150 on 2007-09-12
Inspiron 1150 comes with integrated graphics card and I don't remember seeing GPU... at least not in that corner of the laptop.

Yes, I do have 2 options for the CPU fans. But when I took my laptop apart, I only saw one fan for the CPU.

To test, I have left my laptop with the CD drive tray hanging out (the part where you put your CD on) for a while and the CD drive portion of the laptop was still warm. So perhaps it's not exactly the CD drive, but something that's at the same place? 

I don't think there's anything else there...:confused:

Edit: actually the wireless card is right beneath the CD drive I think... Could that give that much heat?

---

### Post by tak1150 on 2007-09-12
I've confirmed that the wireless card is the source of the heat.
I'll mark this thread as solved and open a new one for the wireless card problem

[the new thread]("http://ubuntuforums.org/showthread.php?p=3354616#post3354616")

---

