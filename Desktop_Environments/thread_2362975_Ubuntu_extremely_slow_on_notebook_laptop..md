---
title: "Ubuntu extremely slow on notebook laptop."
date: 2017-06-04
forum: Desktop Environments
---

### Post by kendingro on 2017-06-04
I'm running Ubuntu from an external 250gb hard drive. I installed Ubuntu 16.x meticulously on the HDD and set the boot order to search for the hard drive. 

This HP Stream 12 Notebook PC is equipped with 2gbs of available RAM. I know Ubuntu uses the host machine's hardware to run itself but how much RAM does Ubuntu actually use? 

The desktop is slow in general but when running a process like Firefox or running through package and repository updates in the terminal, Ubuntu grinds to a near halt. 

Is there anything I can do to improve the performance of Ubuntu with the cards delt to me?

---

### Post by TheFu on 2017-06-04
Welcome to the forums.

Host machine hardware? Are you trying to run Ubuntu with Unity on a netbook with only 2G of RAM inside a virtual machine ... running off an external USB2 HDD?

I tried to find an HP model that was 12inch. On their website, they have 11 and 13, 14, 15 inch laptops. Didn't see a 12inch.

If so, a few things.
[LIST=1]
[*]Switch to a smaller, less demanding, Ubuntu version - Lubuntu/Ubuntu-Mate or Xubuntu. Stay with 16.04.1.
[*]Use USB3, not USB2
[*]Buy more RAM. 4G is the min for running virtual machines
[*]Get a faster CPU (Celeron N3050 is a dog and nobody, even on chromebooks, are happy with it.) - more RAM and USB3 will help more. I don't know how to say this nicely. NOBODY should attempt to run **any** OS on an N3050.  It is 50% slower than cheaper, old, Celeron CPUs.
[*]Don't use slow virtualization like virtualbox.
[*] Dual boot.
[/LIST]

If you can post the true method you are running and the real hardware being used, we could properly set expectations.  I hope you don't have that Celeron CPU that others in the same class from HP use.  My lowest limit on a CPU for a desktop/laptop is a passmark of 1500 or greater.  There are some really, really cheap laptops made in the $150-ish price range new with better performance, but you really have to be cautious. Lots of laptop makers are putting terrible CPUs into these things.

I call it like I see it, based on the little data provided. Please correct anything I assumed that is  wrong.

---

