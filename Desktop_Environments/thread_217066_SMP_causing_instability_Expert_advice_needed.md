---
title: "SMP causing instability Expert advice needed"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Dadgumit on 2006-07-16
Ubuntu has been a long hard road for me. I have trouble shot countless issues and installed so many times I cry to think of it. (if you don't want to hear my whining, skip the next paragraph).

I have about 3 pounds of duct tape thus far. I have a new network card (ubuntu no play nice with my onboard), I have legacy usb disabled (so I need to get a ps2 to start windows with grub), I have had to install with breezy and upgrade because something about my hardware just wouldn't work with the drake installer, I have had to hand edit my xorg.conf to get my dell 1680x1050 to work correctly. Each small battle has been rewarded with that "YAY" moment when it finally worked.

HOWEVER, I now have a problem that I can't find the slightest bit of write up on. (google has failed me :().

I was trying to figure out how to get SMP working and it was no dice whatsoever. I tried everything and just nothing would make that second proc show up.

Well, I needed something from my windows partition so I decided to boot into windows, it hung.

I figured I must have done something in the bios while troubleshooting something from before, and sure enough I had "ACPI APIC Support" disabled (not that I have any clue what that means, mind you). Well, I enabled it and windows booted fine.

Well the great thing was (or so I thought at the time), when I booted back into my nemisis (ubuntu), it was recognizingthe second core!! hooray!

Not hooray. It is hard to describe what is happening, but I will try. The most obvious symptom is that if I were typing right now with "ACPI APIC Support" and thus dual cores enabled, it would look something like ttthisssssssssssssss alllllll            ttthhhheeeee leeeeeeeeetttteeerrrrssss aaaarreeee appearing multiple times with each keystroke (and no, it isn't the repeat rate, strangely enough, if I hold a key down, it repeats normally). The second most obvious symptom is that windows are hard to select, and the mouse doesn't seem to want to do like it's supposed to when clicked (although the pointer always goes where I want it to with normal sensitivity).

The whole OS reminds me of certain programs in windows that aren't good on SMP machines (google earth used to do it fairly bad) where it would do everything really spastically and fast. When you set the affinity of th app to one core or the other it would be fine.


So any help anyone can provide would be greatly appreciated, I would hate to give up on ubuntu after all the carp I have gone through to get it running. but I am at my wits end :(


Here are my system specs in case you need them:

Mobo: A8R MVP Xpress 200 Chipset
CPU: AMD64 X2 3800+
GPU: X800XL Radeon
Mem: 2Gig corsair value select
HD: Sata Raptor 80 Gig

---

### Post by Dadgumit on 2006-07-16
nothing?

---

### Post by Ahriman on 2006-08-03
What kernel are you running?

I have the same processor, different motherboard, and when I installed the smp kernel (2.6.15-26-k7-smp) I havent had any problems at all (although I agree, it would be nice to be abel to set affinity)

---

