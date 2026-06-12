---
title: "C states cause liveCD to freeze during boot"
date: 2009-04-23
forum: General Help
---

### Post by ToeBee on 2009-04-23
I got a brand new Dell Optiplex 760 (C2D E8400) at work yesterday. Perfect timing for a brand new Jaunty installation! However after I burned the CD and tried to boot I ran into kind of a bizarre problem. 

The CD boot menu came up fine but as soon as I selected "Install Ubuntu" the screen went blank and nothing happened. I thought it had frozen up so I punched the power button. Immediately it started reading the CD again and I got to the splash screen with the animated loading bar. Then it froze again. Eventually I figured out that as long as I kept mashing buttons the computer would run fine. As soon as I stopped, everything froze. After it loaded the mouse drivers I could move the mouse to keep the system going. This continued in the installation wizard.

I fixed it by disabling "C States Control" in the BIOS. My guess is that somehow the CPU was being put to sleep and the hardware interrupts from the keyboard/mouse were waking it up until it went to sleep again.

Now that I have completed the installation, I just tried re-enabling c states control in the BIOS and I see the same behavior when I try to boot up from the hard drive. However this time the keyboard isn't working. The only thing that makes the computer go is pushing the power button repeatedly.

My google searches on the topic have come up with nothing related to C states. Has anyone else heard of this? I haven't tried any kernel parameters yet. I'm thinking maybe some of the ACPI parameters may have an effect.

---

### Post by ToeBee on 2009-04-23
First fix I found was nohz=off. This would seem to validate my theory that the CPU was just going to sleep and not waking up again. I believe turning off nohz means that the kernel schedules periodic interrupts which either keep the CPU awake or wake it up periodically.

---

### Post by mythicalbyrd on 2009-07-20
Wow, thanks!  I have had this problem for months, and I just disabled the C states control in the bios and it works great.  I will probably just leave it disabled, so, since you know more than me, do you see any disadvantages to leaving it disabled?:D

:guitar: or (to be more realistic towards my instrument):-({|=

---

### Post by ToeBee on 2009-07-20
I think the only side effects of disabling C-states would be slightly higher power consumption by the CPU when it isn't executing instructions. Here is the Wikipedia explanation of C-states: [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Processor_states](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Processor_states). It is basically just a way for the CPU to power down certain elements to conserve power and reduce heat output.

Out of curiosity, what kind of system are you running? I'm trying to figure out how widespread this problem is because it seems like a fairly major bug somewhere. Most people in my situation would probably assume that "Linux doesn't work on my hardware" and be done with it. I just happened to notice the hard drive light flash when I pressed the power button to reset the computer.

Seeing as this thread didn't get much attention, I'm thinking it may be pretty obscure... maybe a bug in this version of the BIOS on this chipset or something. Then again, I did post on release day so maybe it just got buried. My lspci reports "Intel Corporation 4 Series Chipset" with an 82801 I/O controller.

Also if you don't mind installing powertop I would be curious to know if your CPU spends all of it's time in the C0 state or not. Running with C-state control enabled and the nohz=off kernel option, mine drops down to C1 but doesn't seem to ever hit C2/3. My laptop on the other hand, spends most of its time in C3. That might just be due to different ACPI configurations though.

---

### Post by mythicalbyrd on 2009-07-20
I am running an Optiplex 760 (C2D E7300).

It's running at about 60+ wakeups-from-idle per second with no programs open, but powertop doesn't provide me with any C-state information.
[IMG]http://img66.imageshack.us/img66/1803/screenshotj.jpg[/IMG]

---

### Post by ToeBee on 2009-07-21
Well nevermind. I didn't find this when initially googeling for my problem back on release day but this IS a known problem and it seems to be a bug in the Dell BIOS which has been fixed in the latest BIOS version which was released about a month ago. See here for details:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348694)

Now the only question is how to run the .exe BIOS updater under linux...

---

### Post by mythicalbyrd on 2009-07-21
For those too lazy: [http://ftp.us.dell.com/bios/O760-A03.EXE](http://ftp.us.dell.com/bios/O760-A03.EXE)

The bios update worked perfectly. I re-enabled C-States in the Bios, and powertop said I was hitting the C-3 state.

---

