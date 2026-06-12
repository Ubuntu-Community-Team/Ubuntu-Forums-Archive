---
title: "Black Screen of Death?"
date: 2008-12-19
forum: General Help
---

### Post by loony636 on 2008-12-19
Well this is my first real time installing Linux on any of my computers, and the start hasn't been promising.

After installing KUbuntu 8.10, my computer rebooted as per normal. However, nothing appeared on the screen. No BIOS, no GRUB, no Ubuntu. I could hear everything whirring, so I figured it was a graphic problem. After tying a few things (such as removing the battery from the motherboard), I finally decided to swap the monitor over with another one I had lying around...and it worked. Suddenly I had GRUB and was able to boot into Ubuntu.

However, after installing a new driver for my graphics card, the same issue happened again. I can hear that the computer is running, I just can't see anything on the screen. To make matters worse, the things I did to fix the problem the last time aren't working this time.

So, I'm pretty desperate for help, since my computer is now totally unusable.

Here are the specs:


Asus P4P800 Deluxe Motherboard
ATI X1950XT 512mb Graphics card
3 Ghz Pentium 4 CPU
1.5GB DDR RAM
DVD-RAM Drive
3 x HDD (1 x SATA 300GB, 1 x IDE 20GB, 1 x IDE 80GB)

Any help would be greatly appreciated.

---

### Post by prshah on 2008-12-19
> **loony636 said:**
> However, nothing appeared on the screen. No BIOS, no GRUB, no Ubuntu. 

I doubt this has anything to do with (K)ubuntu at all. This sounds like a pure hardware problem. 

Typically, during POST (Startup), if there is a graphics-related error, you will usually get a series of 2-3 short beeps.

If there is a memory related error, you will get continuous short or long beeps.

If there is a thermal management error (Ex, CPU too hot) you will get a continuous "ambulance-siren" like sound long-short-long-short.

The exact beeps vary from motherboard to motherboard. Are you getting any such beeps?

If you are running an Intel _original_ board, it can get this way when the CMOS battery has lost power. Replacing it, waiting about 15 mins, and then starting the system usually get it going.

I suggest you check if all cards and memory are properly seated, and [url="http://www.youtube.com/watch?v=euvuDQLaIsY"vacuum blow any dust from the tower / case[/url]. This issue can also occur if the power supply is a problem.

Linux is just a convenient scapegoat in this case; Windows will also give you the same issue.

---

### Post by burnetbj on 2008-12-20
Try to boot from liveCD again see if you get a GUI also if you unplug your monitor while it is turned on you will get a no input signal this would save the swapping monitors to test. 

What the above poster said should hold true, are you passing POST?

Also after post, but before splash screen you should get an option to boot from recovery mode are you getting any of this? If not I dont think you are getting past POST if so then you actually probably do have hardware issues


I am feeling your pain tho 
Hate those days

---

### Post by loony636 on 2008-12-20
I am getting no beeps from BIOS, which seems to indicate that everything is running correctly.

I tried simply unplugging the monitor and plugging it back in, but that didn't work. The only way to get anything to display on the monitor is to first plug it into a different monitor, and then plug it back into the original monitor.

I recently discovered something reassuring; if I simply leave my desktop to boot, it will reach the KUbuntu login screen. Once that happens, I can swap the monitors and everything will be fine. However, if I try to reboot the problem returns.

I will check if the CMOS is flat, but I doubt it since the BIOS is giving no lost date/time errors on startup.

The reason I suspected Linux is because the first time this occurred was just after KUbuntu had finished installing. That's too close to be a coincidence in my mind. But at the moment neither Widows or Linux seem the issue, since it isn't even showing BIOS.

This is a...very strange issue. I'm considering switching graphics cards, since I have an identical one in another computer. Could that solve the problem?

---

