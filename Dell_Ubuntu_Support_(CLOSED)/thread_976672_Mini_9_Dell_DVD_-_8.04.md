---
title: "Mini 9 Dell DVD - 8.04"
date: 2008-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RichTJ99 on 2008-11-09
Hi,

I was curious, is the Dell DVD that came with my Ubuntu mini 9 a restore DVD or an install DVD? 

I have not made any changes yet & was curious about that.

Thanks,
Rich

---

### Post by aikiwolfie on 2008-11-09
With my M1330n I got a Ubuntu install CD and a restore iso on the desktop that I could burn to DVD. Well a dual layered DVD actually. As the Mini 9 has no optical drive I'd be surprised if there wasn't some sort of restore partition.

---

### Post by gpw1 on 2008-11-09
The DVD is a Image of Ubuntu at a "point in time" and NOT an install Disk. My Mini came without any wireless drivers. I knew that DELL uses broadcom wireless that require a wrapper. I was forced into  installing a ISO of the Ubuntu 8.4 after I installed a Intel WM3945ABG wireless card that I got on Amazon.com. This card works out of the box in Linux. My Mini now works super. You can only use the Restore disk to return your Mini to the Factory settings only.

---

### Post by RichTJ99 on 2008-11-09
Ahh, ok, so I dont need to back anything up. What wireless card does the mini use by default?  I keep reading about the 8.10 wireless issues & to spend 20 bucks on fleabay for a 3945 card might be the ticket to troublefree computing.

If you wanted to restore to Lpia 8.04 with the 3945 card, would it work out of the box the same as whatever card is in the mini now if you restored it?

---

### Post by superm1 on 2008-11-09
The mini9 comes with a broadcom card that is fully supported with a linux driver from broadcom.  It doesn't require any wrapper such as ndiswrapper or firmware such as b43 requires.

---

### Post by RichTJ99 on 2008-11-09
I keep reading about people installing 8.10 on their mini's & the wifi networking stops working.  I was curious if a different card (such as the mentioned intel wifi card) would stop that issue.  For under $20 bucks, it sounds OK to me.

---

### Post by superm1 on 2008-11-10
Why rush into 8.10 in the first place?  8.04 is well supported on the device.

---

### Post by wx0112 on 2008-11-10
The dell ubuntu DVD was a restore ISO and made a modified ubuntu with hardware drivers. Everything on Mini9 perfectly worked after installation of this disc. But the only damn-it was the the limitation memory - only 883MB, even if you have 2GB:confused:

---

### Post by RichTJ99 on 2008-11-10
While I do have 2gb of ram, it still runs fast.  My bigger concern is getting virtual box running which I cant seem to make it work even using the 386 to Lpia conversion.  I can just see things being a pain in the neck with applications going forward.

---

### Post by ArKay on 2008-11-10
> **RichTJ99 said:**
> Ahh, ok, so I dont need to back anything up. What wireless card does the mini use by default?  I keep reading about the 8.10 wireless issues & to spend 20 bucks on fleabay for a 3945 card might be the ticket to troublefree computing.

If you wanted to restore to Lpia 8.04 with the 3945 card, would it work out of the box the same as whatever card is in the mini now if you restored it?
Last I was aware it was an install disk - so exactly how it handles data already in place I do not know.

I would back up first, just in case, before using it. I used it to set up the 32GB SSD I got, but haven't used it over an existing install so I don't know for sure... but it went through the normal Ubuntu install process as far as I can tell.

Sorry if that doesn't help as much as it could - but that's what I know. If it handles a machine with a previous install differently I don't know.

---

### Post by nrdlevans on 2008-11-10
You have 2GB of ram on a Dell Mini using 8.04 which actually uses sees and uses the 2GB of ram? 

The inability of the Dell Mini to see 2GB of ram is my primary reason to move to 8.10.  Using 8.10 I have been able to my memory recognized. Virtual box is working under 8.10.  Like you I have been having issues getting it to work under 8.04.  If you solved the RAM problem, I probably would not have any reason to use 8.10.

---

