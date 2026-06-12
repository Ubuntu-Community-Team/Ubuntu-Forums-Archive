---
title: "Latitude D630 and no backlight problems"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by biogon on 2007-06-19
Hi.

Sorry to be a raving maniac for my first post, but I'm near at my wit's end now.

I JUST got my Latitude D630 in today.

Configured Vista, installed Ubuntu Feisty. (I had to read this post to get it up: [http://ubuntuforums.org/showthread.php?t=476144](http://ubuntuforums.org/showthread.php?t=476144) -- Thank you!!)

Then on one random reboot, my backlight won't come on. I'm sitting here with a really bright halogen light over the screen, and the machine hooked up to an external monitor.

The backlight won't come on during the BIOS startup, it doesn't come on in Linux, it doesn't come on for Windows.

I can fiddle with the brightness control and the auto-dimmer in Vista and I get zero backlight.

The Fn-key diagnostic gives me error codes 2000-0413, 2000-0414, and 2000-0322. Inverter cable problems -- can't detect and can't access.

Do I have a hardware or a software problem? Are these errors that could result from an incorrect xorg.conf or something? 

Also, how do I reinstall the original Vista MBR bootloader?

The Dell Reinstallation CD won't boot -- it will spin, then drop back into GRUB. Is it SUPPOSED to be bootable?

Any help would be appreciated.

Thanks.

-jon

---

### Post by apel_2804 on 2007-06-20
if light is off also in bios it is hardware related. plug in and external monitor and disable ambient light sensor in bios. if this doesnt help, please call dell due to an backlight/inverter problem. you also can try to reseat the lcd cable, just remove the keyboard and pull the cable on the right top middle of the notebook.

---

### Post by Voland666 on 2007-06-20
In my Dell Latitude D630 (AU Optronics 1440x900 LFP) I noticed no backlight related problem wathsoever. The light sensor nicely works once properly setup from the bios.
The dell hardware test gave me also no Fn or inverter cable problems (in fact passing every single test with green checkmarks).
The "inverter" raises the battery voltage to a much higher lever to light up the CCFL lamp in your panel. Did you remove the keyboard or otherwise disassembled the machine? If it's just a cable related problem, it might be very easy to fix it. They have a service manual somewhere in their support site (documentation downloads), but given it's a brand new machine, I'd call them to have it properly serviced.

---

### Post by Voland666 on 2007-06-20
I forgot... both "Drivers and utilities" (blue DVD) and "Operating system" (brown DVD) are bootable. In fact, I repartitioned the whole HDD from scratch, getting rid of the OEM diagnostic partitions for good. Dell technical support confirmed to me that the blue DVD has everything you need to perform hardware tests. Just to be sure, I had my computer run all of them...

---

### Post by apel_2804 on 2007-06-20
Thats right, the utility has everything needed for ts, but did you have it with you all the time? The tech support will advice you to reseat the cable. and they also ask for an external monitor to check the bios. i supported latitude notebooks a year ago... :)

---

### Post by biogon on 2007-06-22
Thank you for all your help!

With the information on this forum, Dell agreed that it was a hardware backlight cable failure. They are exchanging the machine.

What a funky coincidence... once I installed Ubuntu, the backlight cable disconnects! 

And I was SURE we were past the old days of video card drivers cranking the refresh rate up so high it could blow out a monitor. ;)

I still can't figure out why the blue Utility disk isn't booting though. Perhaps something else is wrong with this system. I will try again with the new machine. 

Thank you so much for your help!

-j

---

### Post by apel_2804 on 2007-06-22
You welcome! they exchange the hole maschine?? wow no repair? how old is it?

---

### Post by Tethtibis on 2007-06-26
your back light went out. see if it is under warranty, check the service tag number under the computer, usually a black or white tag and get them to fix it, if it's not under warranty, a new backlight will cost about as much as a new laptop, might as well go for broke!

---

