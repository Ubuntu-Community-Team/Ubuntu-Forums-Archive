---
title: "Random System Shutdown"
date: 2009-03-21
forum: General Help
---

### Post by GGG121 on 2009-03-21
Hello All,

I've recently built an HTPC and am having problems with the system randomly shutting down. I've read threads from people having similar problems, but no solutions are posted. I've gotten alot of help from you all with a ubuntu 8.10 install on a laptop, so I'm hoping you all can come through for me again.

Hardware:
Motherboard: Biostar TForce TF8200
CPU: AMD Athlon 64 X2 6000 3.1GHz
Memory: 4 x 1GB OCZ DDR2
HD: Western Digital Caviar SE16 640GB SATA
Optical: LG DVD±R SATA
TV Tuner: Hauppauge HVR 1600
PSU: Rosewill RG630 630W

I thought that the system was overheating, but the CPU never got above 45°C. Then I thought the power supply was bad (Had an Apevia 500W PSU in there at first), so I switched out for the one I've listed above. Still have the same problem. Thought the memory was bad, checked system one stick at a time. System boots, but still randomly shuts down. I have the system plugged into a surge protector, which I would assume protects from power spikes, but maybe I need a UPS to ensure the system is getting consistent power? I've also checked to make sure all wires are properly and securely fastend.

I've checked /var/log/syslog for hints, but nothing really stands out. I'll try my hardest to post log information (and any other information) upon request. I'm still very new to linux on a personal system, but I'm very egar to learn! Any help is appreciated! I'm very determined to get this up and running!

---

### Post by amadeus266 on 2009-03-21
My Mobo has a bios setting regarding "safe" temperatures. if the temp goes above the set limit it shuts down. Worth a check.

---

### Post by GGG121 on 2009-03-21
Thanks for the reply amadeus. The bios is currently set to shutdown the system at system temp > 60°C. Seems like a high enough threshold...neither the cpu nor the system exceeds 50°C. Just in case, I'll set the threshold higher to see if that helps.

-------------------------------------

Strike what I've writen earlier...I did not have the temp threshold set at 60°C. I actually had it disabled, so that no matter how hot things got, the bios wouldn't shut down the system. Good thought though amadeus, any other thoughts...anyone?

---

### Post by GGG121 on 2009-03-22
This morning I booted the system and kept it in the bios screen so I could monitor the temps and voltages, and the system shutdown again. This leads me to believe that it's not the OS, but rather a hardware problem.

Any ideas or recommendations on other forums that may help with hardware problems? Again...any help is appreciated!

---------------------------------------------------------

I looked over the specs to my setup...

The motherboard is rated for DDR2 1066 memory. The memory I'm using is DDR2 800. Could this be the problem???

---------------------------------------------------------

Memory speed is not the issue...anybody....please???

---

### Post by novellahub on 2009-03-24
Try removing the CPU heatsink/fan and try re-seating it.  You may want to check if there is a BIOS update.  Also check your voltages on the RAM.  You may have to manually enter the timings / voltage / speed.

On a side note, did you get the on-board sound to work?  My brother in law has the same mobo with Mythtbuntu 8.10 x64 loaded and the sound is not working.

[http://ubuntuforums.org/showthread.php?t=1103960](http://ubuntuforums.org/showthread.php?t=1103960)

---

### Post by GGG121 on 2009-03-25
Hey Novellahub,

Thanks for the reply. I'll look for a BIOS update first. If I remember correctly, the instructions for the mobo even mentioned there might be a BIOS update out there. If that doesn't work, I'll try reseating the cpu and heatsink. The specs on the memory indicate 1.8V, which I think is default on the mobo. Tech support from OCZ says that the speed shouldn't be an issue, I just won't get maximum performance. How would I go about checking/setting the timing for the memory? (Can you tell that I'm a complete n00b with this stuff???)

As far as the on-board sound, I haven't gotten that far yet. It's rather disheartening to hear that there are issues 'cause I was planning on using it with my receiver. When I get to the on-board sound, I'll let you know!

Thanks again!

---

### Post by novellahub on 2009-03-25
On motherboards BIOS, there is usually a automatic setting or you can set the values manually.  I would go in the BIOS and set these values manually.  The label on the memory sticks or info for from the OCZ website will show what parameters to enter.

I have G-Skill brand memory in my Biostar TForce 550 SE motherboard and I had to manually enter the values since it was not automatically detected.  I was having stability issues without entering a value manually.  

If after that you are still having lockups, then do a memory test booting off an Ubuntu live CD.

---

### Post by GGG121 on 2009-03-25
Thanks again for another quick reply!

I'll manually set the parameters for the memory. I've also downloaded the latest update for the bios. The next chance I'll have to mess around with things is this weekend. I'll post the results then. Fingers crossed!

I really appreciate your help on this! After this, I'll start on the on-board sound!

---

### Post by The_Doc_tor on 2009-03-27
I had a similar problem with my first install of Ubuntu and I changed the Bios settings for keyboard shut-down to disable and it is fine. I dont think Ubuntu likes the Win keyboard / X86 keyboard Bios switch on & shut down. Now my problem is just getting it to shut down at all.

Another quickie with processor temps, if you do pull the fan & heat sink off remember to put some heat grease back between them for good heat transfer.
I didnt once :( it cost me a new processor

---

### Post by GGG121 on 2009-03-29
I flashed the BIOS, manually entered the memory voltage, speed, and timing, and still no luck. It was stable enough to run a memory test (about 90 minutes) and everything passed; however shortly after I exited the test, it powered down.

While setting the timing for the memory, I noticed that there are more paramters that I can manually set. They are currently set to auto, which might not be working. I'm gonna see if I can get any information from either OCZ or Biostar about these settings.

The_Doc_tor...
How do you disable the keyboard shutdown? I've found nothing in my BIOS that'll allow me to do that. 

I really hope it's not the mobo...but the longer these problems persist, the more likely it seems that the mobo is the problem :(

I'll post again if and when I get info from Biostar or OCZ that might help.

----------------------------------------------------------------------------------------

I reseated the cpu and heat sink to no avail. I also ran the system with a single stick of memory. It ran for almost 3 hours before shutting down, a new record! This weekend I'm going to pull everything out and rebuild it. Maybe I'll find that it's grounding itself and shorting out. If that doesn't work, I'll try running through all the dimm slots with a single stick of ram, perhaps I've got faulty dimm slots.

No luck with Biostar tech support. I took the time to outline the problems I've been having and explain the steps I took to try to fix it. The response I got from them was less than satisfying :(

---

### Post by GGG121 on 2009-04-04
Well, I took everything out and rebuilt the system. I found that I had put in a few extra mobo stands that weren't needed. I thought those may have been shorting the system. No luck though, problem still persists. I noticed that the onboard graphics chip was getting rather hot. After multiple system shutdowns and reboots, the system would be slow to POST. The onboard LEDs showed that the problem with the slow POST was that there was a VGA error. Once the VGA LED lit up, the system would POST. Maybe there's a critical graphics chip temperature that's being exceeded? When the system would shutdown, I noticed that the memory LED would shut off first. Perhaps I've got faulty dimm slots? Either way, I'm rather convinved that I have a faulty mobo and will be needing a new one.

I understand that I've turned this thread from a Ubuntu support thread to a hardware troubleshooting thread, and my apologies. I've continued to post here because of the wonderful support I've gotten from Ubuntu users on everything! I'm planning on getting a new mobo (gigabyte? asus? ...suggestions?). Hopefully I'll have one more reply to this thread saying that the problem was fixed! Thank you all for your help on my situation and your efforts on aiding those Ubuntu users who seek help in this forum!

---

### Post by GGG121 on 2009-04-27
Well, problem solved.

The mobo I was using was giving the cpu too much voltage, making the system unstable. There was nothing in the BIOS to reduce the voltage to within the recommended range for the cpu. I got a new mobo and all is well!

...as a matter of fact, I'm typing this reply using my HTPC!

Thank you everyone for your help!

---

### Post by bicchi on 2009-04-28
> **GGG121 said:**
> Well, problem solved.

The mobo I was using was giving the cpu too much voltage, making the system unstable. There was nothing in the BIOS to reduce the voltage to within the recommended range for the cpu. I got a new mobo and all is well!

...as a matter of fact, I'm typing this reply using my HTPC!

Thank you everyone for your help!

Could you tell me if you got audio working with the Biostar TF8200? 
I am talking about the audio output to the speakers and not the HDMI output to the TV.
You might have to use the latest version of Mythbuntu (9.04) to get the newest version from Nvidia and the Alsa drivers.

Thanks,

---

