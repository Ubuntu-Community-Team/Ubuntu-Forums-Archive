---
title: "Ubuntu on Intel i3, i5, and i7 Systems"
date: 2011-01-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fjgaude on 2011-01-02
How is Ubuntu 10.10 doing on computers that use the Intel i3, i5 and i7 CPUs? I'm about to build a system with one of these and am wondering the issues, if any.

Thanks!

---

### Post by cascade9 on 2011-01-02
At least some issues with the i3/i5 Intel video (get a video card) and some random networking/audio problems (maunfactuer specific, only some of them put dodgy network/sound cards on the motherboard). 

Why is this is 'dell ubuntu support' BTW?

---

### Post by fjgaude on 2011-01-02
> **cascade9 said:**
> At least some issues with the i3/i5 Intel video (get a video card) and some random networking/audio problems (maunfactuer specific, only some of them put dodgy network/sound cards on the motherboard). 

Why is this is 'dell ubuntu support' BTW?

I noticed the Dell 580s and thought it would be a good box to imulate but with Linux. If I built one I'd be using the Gigabyte GA-H55N USB3 MB. Any thoughts?

---

### Post by 67GTA on 2011-01-03
Running on studio 1569 laptop with i5 m430, and runs fine. Everything works out of the box except for broadcom wireless (wl driver is on cd). I would get dedicated video card as mentioned. I have seen several reports of i5/i7 intel integrated graphics having problems. This machine came with ati hd4570. I was surprised that even the software eject key worked with the slot loading cd drive. I had to hunt down the driver for win7, and all other distros wouldn't recognize it. I am pleased with the i5, but haven't really played with the i7 family. Combined with the new 200 line kernel patch, it is super snappy.

---

### Post by 67GTA on 2011-01-03
> **cascade9 said:**
> 

Why is this is 'dell ubuntu support' BTW?

Are you building from dell?

---

### Post by cascade9 on 2011-01-03
> **fjgaude said:**
> I noticed the Dell 580s and thought it would be a good box to imulate but with Linux. If I built one I'd be using the Gigabyte GA-H55N USB3 MB. Any thoughts?

I assume that you mean a inspiron 580, the optiplex 580s are AMD. Either of them are fairly generic AMD or i3/i5 builds, nothing new there. 

I'd get a P55 chipset over the H55, but then again, I'd get an AMD over Intel.

---

### Post by fjgaude on 2011-01-03
> **cascade9 said:**
> I assume that you mean a inspiron 580, the optiplex 580s are AMD. Either of them are fairly generic AMD or i3/i5 builds, nothing new there. 

I'd get a P55 chipset over the H55, but then again, I'd get an AMD over Intel.

Thanks for the suggestions... I used AMD for years up until the Intel Core 2 came out, then...

I just ordered a Lian Li Q11 box and will go with the H55 MB... we will see how Ubuntu plays with the mix. I'm not a gamer but a graphic designer with a wish to have the computer small, sitting on the desktop. I do require fast and quick. We'll see how the Intel GMA works out. If not then a good PCIe X16 video board added.

Thanks to all for the input!

---

### Post by cascade9 on 2011-01-04
> **fjgaude said:**
> Thanks for the suggestions... I used AMD for years up until the Intel Core 2 came out, then...

I just ordered a Lian Li Q11 box and will go with the H55 MB... we will see how Ubuntu plays with the mix. I'm not a gamer but a graphic designer with a wish to have the computer small, sitting on the desktop. I do require fast and quick. We'll see how the Intel GMA works out. If not then a good PCIe X16 video board added.

If you are going intel, forget i3 (totally outclassed by AMD CPUs in the same price range) and the dual core i5s are pretty poor value as well. i5-750 (and other i5 quads) are the best choice. 

Intel GMA should work,but there has been some issues with the i3/i5 video. If it doesnt work, a nice cheap GT210 will do the job just fine (with nvidia drivers), or get an ATI if you want to use the open soruce drivers. IMO anyway.

---

### Post by fjgaude on 2011-01-04
I've gone with the Intel and Gigabyte, i5-655 and H55N-USB3. Will post my results in Hardware when I've completely tested the new build.

---

### Post by cascade9 on 2011-01-04
> **fjgaude said:**
> I've gone with the Intel and Gigabyte, i5-655 and H55N-USB3. Will post my results in Hardware when I've completely tested the new build.

*blinks* an i5-655k? That is an overclockers CPU, its an i5-650 thats unlocked, with intel TXT (trusted execution) and intel VT-d (Virtualization Technology for Directed I/O) removed......

---

### Post by fjgaude on 2011-01-04
> **cascade9 said:**
> *blinks* an i5-655k? That is an overclockers CPU, its an i5-650 thats unlocked, with intel TXT (trusted execution) and intel VT-d (Virtualization Technology for Directed I/O) removed......

Right... take a look at my signature: I'm an overclocker and use VMware. This CPU is for that! If it isn't I'll send it back within 30 days.

After the Sandy Bridge iTX MBs come out and settle down, in two years, I'll likely get one of those. <smile>

---

### Post by cascade9 on 2011-01-04
> **fjgaude said:**
> Right... take a look at my signature: I'm an overclocker and use VMware. This CPU is for that! If it isn't I'll send it back within 30 days.

VMware is one reason why I would have gone for a quad core- besides the extra cores, they are 8MB cache models, the dualcores are only 4MB. No intel VT-d sort of sucks as well. 

The i655 should overclock higher than a 750 (I'd expect about 4GHz with the 655, about 3.6-3.7 with the 750), but the extra cache would more than make up for it IMO. 

The other reason why I was thinkqaudcore is it seems a bit strnage to go from a 8400 @ 4.0GHz to another dualcore that probably wont be a huge amount faster.... 

> **fjgaude said:**
> After the Sandy Bridge iTX MBs come out and settle down, in two years, I'll likely get one of those. <smile>

+  a new CPU to suit, and new RAM as well probably.....

---

### Post by fjgaude on 2011-01-04
What makes you think the i5-655K doesn't have VT-d?

---

### Post by cascade9 on 2011-01-04
> **fjgaude said:**
> What makes you think the i5-655K doesn't have VT-d?

Intel. 

[http://ark.intel.com/Product.aspx?id=48750](http://ark.intel.com/Product.aspx?id=48750)

If there was VT-d, it would be listed, like here- 

[http://ark.intel.com/Product.aspx?id=43550](http://ark.intel.com/Product.aspx?id=43550)

---

### Post by fjgaude on 2011-01-04
Okay, but you have it wrong on the VT-x technology. Of course with the chip open we can't have Trusted Execution... So I think all is alright, no have to send it back.

---

### Post by cascade9 on 2011-01-04
> **fjgaude said:**
> Okay, but you have it wrong on the VT-x technology. Of course with the chip open we can't have Trusted Execution... So I think all is alright, no have to send it back.

Ummm.....I never, ever wrote 'VT-x' in this thread. I said 'no VT-d', which is 100% accurate ;) 

I wonder what you mean by 'open'. Did you mean unlocked?  TET, I dont know why intel cut it from that chip, but having unlocked multipliers has nothing to do with it being removed.

---

### Post by fjgaude on 2011-01-04
By open is meant that all the voltages and multipiers are adjustable, Vcore, Vtt/QPI, PCH and Graphics core, plus, of course, VRAM voltage which has little to do with directly with the CPU, except the relative freqs tied to multipliers, etc.

VT-d, okay!

Let's let it go!

---

### Post by cascade9 on 2011-01-04
> **fjgaude said:**
> By open is meant that all the voltages and multipiers are adjustable, Vcore, Vtt/QPI, PCH and Graphics core, plus, of course, VRAM voltage which has little to do with directly with the CPU, except the relative freqs tied to multipliers, etc.

Which has nothing to do with TET (or TXT if you perfer). 

> **fjgaude said:**
> VT-d, okay!

Let's let it go!

OK, seeing how for once I didnt make the mistake, no problem :lolflag:

---

### Post by fjgaude on 2011-01-04
Very good and thanks for the suggestions.

I forgot to state my priorities in what I'm doing: 1) quiet, 2) fast, 3) quick, and really the driver: get a small footprint machine on my desktop, meaning something small. So my tradeoffs took all these into consideration.

---

