---
title: "Computer Will not Boot UP!!"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Inhumane on 2006-09-13
Last night I recompiled my Kernel and told it my processor is a P4/Celeron (I have a Celeron, but there are different varients of it, I wasn't too sure), which made it go from 386 to 686. That night I was playing Diablo II on that machine when it powered down... after it went down I couldn't turn it on, no fan, no sound, nothing, presssing the power button doesn't work. It had to be the 686, it must have taken too much power from either the CPU or the PSU, either way one must be fried now, how can I tell which it is? I opened up the computer last night and nothing seemed wrong..

---

### Post by coffeecat on 2006-09-13
A kernel compiled for 686 should be fine for a P4 Celeron. If anything it should be more efficient than a 386-optimised kernel. One likely explanation is that the CPU cooler was not up to the task, and when you had the CPU under heavy load the CPU temperature went up too high and the CPU was damaged. Possibly just a coincidence that it happened after a kernel recompile.

One thing to try is to see if you can borrow a PSU, and try to run the machine from that. If it works, your PSU has failed. It happens sometimes. If not you may indeed have a fried CPU.

---

### Post by Inhumane on 2006-09-13
The only other computer I have in my house is a laptop, and no one of my friends in their right mind would let me take out a PSU out of their system. 
Are there signs that would help me figure out wether it's a faulty motherboard, a PSU or a melted CPU?

---

### Post by turbojugend_gr on 2006-09-13
Since you have a laptop, you are in trouble. If your Guarantee is not expired, you should forward this question to the ones responsible for it. If your guarantee is expired, you should open the laptop, then check if the mainboard is of just by looking at a led. Most propably that's not the case. After that you may check if the cpu is fried, I don't know how it goes when it comes to laptop cases, but in a desktop pc you can check the cpu just by removing it from the socket, and check if it's pins are black, or depp greyed. If not you are ok then too. That's pretty much what I can cotribute, 'bout the psu I am pretty sure that in laptops alos smells very intesively if burned down... so if you had a PSU out of order (which usually is the case) you should smell something like burned plastic, or sth near it. If you can't smell it now, once you open the case it will surely be more intense...

PS: I can assure you that the kernel update was just accidentally bad timed ... no connection for me between the 2 issues.After all you chose the correct kernel.

---

### Post by Inhumane on 2006-09-13
No no, the PC affected is a desktop, the person above just mentioned taking a PSU from another computer and connect to mine to see if that's the problem, but I the only other computer I have available is a laptop, which has no PSU. 
I know the Kernel itself is not the cause, it's just software, not hardware, BUT like I said, I did configure it and said I have a P4, maybe it told the CPU to use more power since.. P4's need more power I'm sure than what a lousy Celeron would use. I don't think I can remove the heatsink off my CPU though, I tried it last night and it seems glued, if I try to rip it open, that will break the CPU for sure. I'll try to buy a PSU, hope that's the cause.

---

### Post by coffeecat on 2006-09-13
A few points:

If your celeron is not a P4, or rather a Celeron D, then I doubt it would have been able to run a 686-optimised kernel. A 'lousy' Celeron is essentially a Pentium with some of the level 2 cache stripped out - cheaper to manufacture, but runs a bit slower. The heatsink isn't glued to the CPU. That's thermal paste which is quite sticky. You can prize the two apart but you have to be careful. Suggest you google around - specialist stores that sell computer parts might have illustrations and instructions for removing and fitting CPUs and heatsinks. Was there a fan on the heatsink? You really need one for a P4/Celeron D.

Best of luck anyway.

---

### Post by turbojugend_gr on 2006-09-14
Oh, my bad, since it is a desktop can't you take the CPU out from the socket and check it's pins? If it was a burned Supply unit I am sure it would smell very bad, and you should have noticed that. I believe that since it can't even boot Ram is also out of the wuestion... but anyway check out for smells coming from the PSU (doesn't it have a power switcher on it? Check it, sometimes it comes along with a led so you can see if it gains power, even if the PC is closed). You know I 've seen such issues (I was working for a pc service store) coming from very simple-sometimes funny- mistakes. I don't believe that a Linux user would not notice anything from the following but I write them down just in case: -check if the PSU is closed from the switcher -check if the source of power (ac/dc cables,multi-adaptor, or anything like that you may use to bring electric power to the box) is damaged, or generally faulty -check if the cable supplying power to the mainboard is removed or faulty. -check any similar case you may think of, my memory stop to the above... 

P.S. My view is that it is possible that it is something simple, because I don't see the PSU burned since it doesn't smell, nore I believe a CPU can get fried while using low need applications.

---

### Post by Inhumane on 2006-09-14
Umm well I don't think anything is burnt either, becuase the computer is right below my desk, I would have smelled something, I mean it was working fine, and then shut down for whatever reason, and from then on it wouldn't power on. My PSU does'nt have a on/off swtich on the back, so that can't be it. When I plug the connector to the back of the PSU, there's a constant buzzing sound, I don't think it was there when the PSU was working fine, it's really faint, but you can hear it, and it buzzes for aslong as it's plugged, could that tell you something?

PS, sorry if this has gone out of topic, but I thought the 686 configuration made it work harder than it could take, which is why I posted here in the first place

---

### Post by turbojugend_gr on 2006-09-14
Hmm, so no smell ha? I c so the fried equipment goes out of the picture (though I insist it is fairly easy to take the CPU out of it's socket and check it's pins). So the PSU has no switch and the cable supplying it with electricity seems to work (since you hear that sound), but then again is it possible for you to check if there's a sparkle too? Cause you know that sound might be static electricity "stored" on your PSU's parts... So check the supply cable and also try checking if the mainboard is correctly attached to the cord coming from the PSU... that thing might moved an inch or sth... till you do so I 'll might come up with sth else. I hope I am or the right path...

---

### Post by turbojugend_gr on 2006-09-14
Oh damn I am quick (lmbao) ;). open the bloody case too ,and check the Ram Dimms unplug them and then put them back again, sometimes they loose connectivity and somehow the appropriate sound doesn't beeps after startup. I believe  that's a shot in the Dark but it worths a chance. Make sure you do check the CPU pins, when it comes to intel's CPUs they have that effect (after socket 384 I recall-but then again I am not so sure). If you are afraid to do so, check aeverything else and then go for this one (though I believe it is better to check it- you just release the handle that keeps it on the socket (usually a clip-like tiny bar) and then gently slide it up, take a look at it's connection pins in a dust-free yet lighted room, so you can see if they are greyed, and then slide it back in gently again.

PS: You know this forums is for ubuntu related issues so we might be out of topic, but then again no harm in giving advise. AGAIN if you do not wish to unplug your cpu do not do it just because I tell you so, it is your equipement.

---

