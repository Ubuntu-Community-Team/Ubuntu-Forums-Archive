---
title: "Ubuntu 10.04 booting issues"
date: 2010-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rj.alaskan on 2010-11-15
I have a Dell Inspiron 570 desktop and when I boot Ubuntu 10.04 off of a DVD I can get to the first menu, when you select Install, Try without change, etc. But if I choose one of these options, the screen goes black and the computer restarts. Im not a computer novice by any means but this one has me stumped.

Any help will be appreciated. Thanks!

---

### Post by amauk on 2010-11-15
Have you run the CD checker thing (in that same menu)?

Maybe the CD didn't burn properly

---

### Post by rj.alaskan on 2010-11-15
> **amauk said:**
> Have you run the CD checker thing (in that same menu)?

Maybe the CD didn't burn properly

It will do the same thing with all of the items on the menu list. I burned it at 4x so it should be fine

---

### Post by sikander3786 on 2010-11-15
Can you please post your hardware specs?

Also from the same Install/Try menu, press F6 and select nomodeset. Boot and see if it helps.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by rj.alaskan on 2010-11-15
> **sikander3786 said:**
> Can you please post your hardware specs?

Also from the same Install/Try menu, press F6 and select nomodeset. Boot and see if it helps.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

I have an AMD Athlon Quad Core 2.4 GHz, 6 GB of RAM, NVidia GT240 with 512 MB video RAM, 750 GB hard drive, 

What all do you need?

I'll try the boot option deal here in a few minutes

---

### Post by sikander3786 on 2010-11-15
> **rj.alaskan said:**
> I have an AMD Athlon Quad Core 2.4 GHz, 6 GB of RAM, NVidia GT240 with 512 MB video RAM, 750 GB hard drive, 

What all do you need?

I'll try the boot option deal here in a few minutes
I think with Nvidia graphics card, you'll definitely need the **nomodeset** parameter. Lets see...

---

### Post by rj.alaskan on 2010-11-15
I am currently running openSUSE 11.1 which ive had laying around the house for a while. Not that openSUSE is painful, but I would rather be running ubuntu :D

with the nomodeset parameter, do i enter it in on the line or just select it from the mini menu that comes up when you press F6?

---

### Post by rj.alaskan on 2010-11-15
I tried the nomodeset and it did not work. :( Any other ideas?

---

### Post by sikander3786 on 2010-11-16
Check the downloaded image integrity at first.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, burn a new disc at 4X as you did with the previous one.

You can also try some other boot options like acpi=off, noapic etc. Details on the same page.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by rj.alaskan on 2010-11-18
I have verified that the dvd is fine, and it boots on my HP laptop. I also have a Windows 7 64-bit disc and a openSUSE 11.3 64-bit and they do the exact same thing. The Windows disc loads files, and then decides it is going to restart as well. This is incredibly frustrating and I was wondering if anyone else has had this problem?

---

### Post by sikander3786 on 2010-11-18
> I also have a Windows 7 64-bit disc and a openSUSE 11.3 64-bit and they do the exact same thing.

Then it might not and should not be related to Ubuntu at all.

I feel it is your hardware not letting you install any OS. Might be something heating up...

Check your PC for heat. And as an initial diagnostic, test your RAM. A RAM test might run overnight.

If you've got more than one modules of RAM, try them one-by-one.

---

### Post by rj.alaskan on 2010-11-18
> **sikander3786 said:**
> Then it might not and should not be related to Ubuntu at all.

I feel it is your hardware not letting you install any OS. Might be something heating up...

Check your PC for heat. And as an initial diagnostic, test your RAM. A RAM test might run overnight.

If you've got more than one modules of RAM, try them one-by-one.

I only recently downloaded openSUSE 11.3 and Windows 7 thats how I found out about those things. I'll run the RAM check and try the single module test, but I bought this computer in July so it shouldnt be bad yet.

---

### Post by rj.alaskan on 2010-11-18
I have identified the problem but I do not know what could be causing it.

Dug around for 20 minutes and found some older versions of Linux that were 32-bit like Ubuntu 9, BackTrack 4, and openSUSE 11.1. All three booted up.

So my computer will not boot anything that is 64-bit, even though I had been running Windows 7 Home Premium 64-bit before it BSOD'd on me.

How could this happen? And how can I fix it? Like I said I am not a novice at computer repair so whatever you tell me to get or do I will understand but I have never had a problem like this.

EDIT:

Computer Specifications:
Model - Dell Inspiron 570
Processor - AMD Athlon II X4 630
Memory - 6GB 1066MHz DDR3 SDRAM
Video - NVidia GeForce GT240 (probably not needed)

---

