---
title: "hard freezes/random reboots: video driver problem or power supply overloaded?"
date: 2009-03-08
forum: General Help
---

### Post by evencoil on 2009-03-08
I installed Intrepid on a brand new custom built box about 2 months ago. Everything has been working fine, except that the system is pretty unstable. 

The exact circumstances of crashing/freezing have been hard to pinpoint but I --think-- that when I have compiz on with lots of neat effects, this tends to cause the system to go into a completely unresponsive hard freeze with no messages in any system logs. Since turning off these effects a few days ago I haven't had any freezing problems.

So I thought problem solved, this must be a video driver problem and since I can live without compiz, no big deal. But then today I have had the system reboot (not freeze like before) twice with no warning and no messages in any of the system logs. At the time I had an external hard drive plugged in that I usually do not and I was also doing some fairly cpu-intensive video converting.

So now I'm thinking this looks like my power supply is inadequate? But I have a ThermalTake 70% efficiency 500W PS for the following:
  Intel Q6600 (quad-core) 2.4G
  4 GB RAM
  512 MB Geforce 9400 GT video card
  1 SATA 7200rpm 1TB hard drive
  A DVD-RW drive
  a wireless ethernet PCI card

It seems like my PS should be plenty for that, doesn't it?

Anyone have any ideas? Perhaps thoughts on how I can go about troubleshooting this further. I would prefer not to order out for another power supply and go through all that hassle, although of course that would be the best way to check this.

---

### Post by kestrel1 on 2009-03-08
Sounds like an overheating problem or memory issue.
Make sure that you CPU isn't overheating. The next time it freezes you could reboot & enter the BIOS & check the section that has your processors heat & the fan speeds etc.
If you have more than one stick of RAM installed you could try removing one & see if you can replicate the problem. Obviously swap the sticks about to test them all.
This could also be a PSU problem, as these can be very hard to troubleshoot. You could try getting hold of a PSU test module. I have one & it tells me if any of the lines are sending incorrect voltages etc. I think the most likely is overheating though.

---

### Post by evencoil on 2009-03-08
ah yes so I should have remembered to say that I checked for overheating (as you suggested by looking at the BIOS after a crash/reboot) and its running cool as can be in the 35-45C range.

The RAM idea is a good one I'll check that.

---

### Post by kestrel1 on 2009-03-08
OK, if the overheating is not an issue, then check the RAM. It is always possible that the GPU is getting a little hot as well & failing. Have you cleaned all fans & checked the ventilation around the GPU?

---

### Post by evencoil on 2009-03-08
yeah all the fans are running great and everything is airy, clean and open. I'm running on 1 RAM stick now. Did you mean also that I should permute which RAM slots in my motherboard I am using?

---

### Post by kestrel1 on 2009-03-08
You could try changing the slot, but I don't think that will make any odds unless the contacts are slightly dirty or not making good contact.
If you could borrow a RAM stick to check out if you get the problem, that may help.
Another Graphics card, preferably the same, to check that out or another PSU. PSU's are known to cause various problems & can be hard to find out the exact cause. If it isn't supplying the correct voltage to the main board, that could cause this sort of problem when you put a load on the system, but there is always the possibility that it isn't the PSU.

---

### Post by miegiel on 2009-03-08
There's a mem test option in grub. You can set it in a loop to run over night and see the results in the morning. How ever if it is your psu, memtest might still crash or give errors for lack of juice. On that note 500W seems more then enough for your hardware, but the psu can still be defective.

---

### Post by evencoil on 2009-03-17
so I had success with removing one stick of RAM and was able to keep my system up for 6 days, 3 of them with compiz on full blast.

when I went to do some tests to see if it was the RAM stick or the DIMM slot, or what, I eventually deduced that something bizarre was going on. A check to my motherboard manual indicated that since I have 2 RAM sticks and 4 DIMM slots, I had to make sure to put in the RAM sticks so that they were on the same channel. I had not realized this and before they were on separate channels. Now things appear to work perfectly and the system seems stable as a rock (knock on wood).

so thanks for the RAM suggestion, turned out to have saved me quite a bit of money and headaches!

---

### Post by kestrel1 on 2009-03-18
Always a good idea to check the manual if possible. It is a pain when the RAM has to be in the correct sockets to work correctly.
At least you seem to be working now. :)

---

### Post by miegiel on 2009-03-18
You might still have a problem but just not notice it. You have 2 2GB strips, so as long as you use less then 2GB you are only using 1 strip. IIRC in single channel the second strip is only used when all the memory in the first strip is used.

In dual channel both strips are used at the same time, kind of like raid0 but with memory instead of disks ([_wikipedia on dualchannel_]("http://en.wikipedia.org/wiki/Dual_channel")). In dual channel your memory is also twice as fast as in single channel, so you should only use single channel if you really have no choice.

Seriously consider running mem test in a loop over night (see grub boot menu) and check the results in the morning.

---

### Post by evencoil on 2009-03-19
I didn't quite understand that...

But I see, I think it was my mistake in what I wrote in my previous post--from that wikipedia article I see that my terminology was incorrect; where I said "channel" I should have said "bank". 

Before, each stick was in a different color slot, i.e. they were on the same channel, but in different banks. This seemed to cause instability.

Then I moved them to the same colored slot, i.e. different channels same bank, and now the system appears stable.

I think I'll run a memtest anyway, though!

---

