---
title: "Noob in need of help"
date: 2010-07-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Lash009 on 2010-07-30
Hi everyone, I'm Matt and I was wondering if someone could answer a few questions for me.

My family is getting a new desktop, and I'm pretty much getting this faulty one I'm on now. It's a Dell XPS 400 running XP (32 bit)- which I have had endless troubles with. So I've decided to duel-boot ubuntu with xp.
The specs are:
Processor: Intel Pentium D 2.80 gigahertz
           2 cores, 64-bit ready, no hyperthreading
3 gb of Memory
Graphics Card: NVIDIA GeForce 9600GT
Multimedia: SigmaTel High Definition Audio CODEC 
                     Unimodem Half-Duplex Audio Device
Intel PRO/1000 PL Network Connection

I've used an ubuntu 9.04 live disk to trial run ubuntu on this computer and didn't experience any problems; aside from not having media codecs installed and not being able to watch youtube videos. I've also checked my hardware for compatibility, but I couldn't find the Graphics card or sound card on the list.
although I think the graphics card works because I didn't have any trouble when using the live cd.

Anyway to my questions...
Is there anyway to test the sound card for compatibility while using the live cd (on the test run)?
and
If I decide to install ubuntu, I will get a newer version first. Should I get the 64-bit edition (the processor can handle it) even if I only have 3 gbs of Memory?

Sorry It was such a long post, but I wanted to give you all the info you needed.

---

### Post by Revolutionary101 on 2010-07-30
I would suggest using the 32 bit version because of the fact that you will not see any difference in performance from 64 bit. This is because you are only using 3 GB of RAM. You would only see a difference if you had more than 4GB of RAM.

Before you install the latest version of Ubuntu (Ubuntu 10.04 Lucid Lynx) you should burn it to a CD and use it as a LiveCD. This will show how well your system runs on the latest version. These may seem like a weird thing to do since you already have tested it, but rarely Ubuntu may have a hardware problem with a later version that it didn't have before.

To test the sound on Ubuntu (and a bunch of other things) go to System>Administration>System Testing. Or you could just click on the "Examples" icon on your LiveCD Desktop and there should be some video or music files you can play.

---

### Post by p.s. on 2010-07-30
32 should be fine, you can always upgrade later if you feel like it! 

Also, if you're having trouble with watching youtube videos, etc. in Firefox after you get the codecs, etc. I'd try Chrome.

---

### Post by geekette2010 on 2010-07-30
> **Revolutionary101 said:**
> I would suggest using the 32 bit version because of the fact that you will not see any difference in performance from 64 bit. This is because you are only using 3 GB of RAM. You would only see a difference if you had more than 4GB of RAM.

Before you install the latest version of Ubuntu (Ubuntu 10.04 Lucid Lynx) you should burn it to a CD and use it as a LiveCD. This will show how well your system runs on the latest version. These may seem like a weird thing to do since you already have tested it, but rarely Ubuntu may have a hardware problem with a later version that it didn't have before.

To test the sound on Ubuntu (and a bunch of other things) go to System>Administration>System Testing. Or you could just click on the "Examples" icon on your LiveCD Desktop and there should be some video or music files you can play.
With lucid lynx 10.04 you need to add adobe and flash player yourself to be able to see and hear any video.

---

### Post by geekette2010 on 2010-07-30
> **Lash009 said:**
> Hi everyone, I'm Matt and I was wondering if someone could answer a few questions for me.

My family is getting a new desktop, and I'm pretty much getting this faulty one I'm on now. It's a Dell XPS 400 running XP (32 bit)- which I have had endless troubles with. So I've decided to duel-boot ubuntu with xp.
The specs are:
Processor: Intel Pentium D 2.80 gigahertz
           2 cores, 64-bit ready, no hyperthreading
3 gb of Memory
Graphics Card: NVIDIA GeForce 9600GT
Multimedia: SigmaTel High Definition Audio CODEC 
                     Unimodem Half-Duplex Audio Device
Intel PRO/1000 PL Network Connection

I've used an ubuntu 9.04 live disk to trial run ubuntu on this computer and didn't experience any problems; aside from not having media codecs installed and not being able to watch youtube videos. I've also checked my hardware for compatibility, but I couldn't find the Graphics card or sound card on the list.
although I think the graphics card works because I didn't have any trouble when using the live cd.

Anyway to my questions...
Is there anyway to test the sound card for compatibility while using the live cd (on the test run)?
and
If I decide to install ubuntu, I will get a newer version first. Should I get the 64-bit edition (the processor can handle it) even if I only have 3 gbs of Memory?

Sorry It was such a long post, but I wanted to give you all the info you needed.
With lucid lynx 10.04 you need to add adobe and flash player yourself to be able to see and hear any video.

---

### Post by Revolutionary101 on 2010-07-30
> **geekette2010 said:**
> With lucid lynx 10.04 you need to add adobe and flash player yourself to be able to see and hear any video.

No, the video and music files provided in the examples folder are .ogg files, which Ubuntu comes with the codec preinstalled.

---

### Post by Lash009 on 2010-07-30
Wow thanks everyone for helping me so quickly and not making fun of me for being a noob:p.
I ran the test and everything worked so I guess this can be marked as solved.

---

### Post by linux18 on 2010-07-30
64-bit IS ALWAYS BETTER than 32 bit if you can handle it its not just the more than 4GB paging file size, if a program is compiled and run on a 64-bit platform it will execute faster than if it was compiled and run on a 32-bit platform. 64 bit is the future, and we'll get there faster if we stop clinging to the notion of 32 bit superiority. That's why I choose 64-bit first when I made my own distro (see sig). we had this fight once before going to 32 bit from 16 bit and guess who won that one

---

### Post by Revolutionary101 on 2010-07-30
> **linux18 said:**
> 64-bit IS ALWAYS BETTER than 32 bit if you can handle it its not just the more than 4GB paging file size, if a program is compiled and run on a 64-bit platform it will execute faster than if it was compiled and run on a 32-bit platform. 64 bit is the future, and we'll get there faster if we stop clinging to the notion of 32 bit superiority. That's why I choose 64-bit first when I made my own distro (see sig). we had this fight once before going to 32 bit from 16 bit and guess who won that one

Well I have no doubt that we are going to move to 64 bit in the near future. As of now it is hard to find any new computers that have less than 4 GB of RAM. It is only a matter of time. I also advocate using 32 bit Ubuntu only if you have less than 4 GB of RAM that doesn't make 32 bit superior than 64 bit.

Anyways, this is getting beside the point and I still advocate the use of 32 bit Ubuntu on his desktop with 3 GB of RAM.

---

### Post by linux18 on 2010-07-30
> **Revolutionary101 said:**
> Well I have no doubt that we are going to move to 64 bit in the near future. As of now it is hard to find any new computers that have less than 4 GB of RAM. It is only a matter of time. I also advocate using 32 bit Ubuntu only if you have less than 4 GB of RAM that doesn't make 32 bit superior than 64 bit.

Anyways, this is getting beside the point and I still advocate the use of 32 bit Ubuntu on his desktop with 3 GB of RAM.
I reject your sensible view of processor architecture and memory limitations, and substitute my own reality.















ok,  I've given up (just wikipedia'd 64-bit) maybe th OP should go with it

---

### Post by RTrev on 2010-07-30
The problem with choosing 64-bit right now is that Adobe pulled the 64-bit version of flash they were testing.  Until it comes back, we have to run the 32-bit flash inside a wrapper.  Normally this isn't too bad, but lately I've seen that wrapper using way too much cpu.

So, while I'm testing Maverick for example, I'm using only 32-bit versions.  On a production machine, as opposed to testing, the same argument would apply to an even greater extent.

We're held hostage by Adobe's stranglehold on this market.  Hopefully I'll still be around to enjoy the show when Flash dies a slow and painful death. <g>

---

