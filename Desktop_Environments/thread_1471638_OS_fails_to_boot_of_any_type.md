---
title: "OS fails to boot of any type"
date: 2010-05-03
forum: Desktop Environments
---

### Post by Versial on 2010-05-03
I believe my computer was subject to a power surge. After a storm the PSU no longer worked. So I bought a new PSU and hooked it all up. I have checked it three times all ready to make sure that I hooked up everything the way it should be and made sure the power was to to 115 on the back. The computer will power on and I can access the bios, however, when it reaches the point that it should be loading the OS, with Ubuntu I just receive Grub error 21.  With any windows OS, the computer just reboots every time it reaches that point.

So far I have checked the CMOS, defaulted the BIOS, verified the Hard Drive to another computer, verified the RAM to another computer, reformatted twice (trying the different OS's), and changed SATA cables. Still nothing. I am at a loss.

---

### Post by TBABill on 2010-05-03
Try downloading a bootable hard disk utility. I used SeaTools from Seagate. What I found when I had a similar problem was that my hard drive failed to a point the tools could not recover from it. It must have been more than some bad sectors. I had my wife stop at a Best Buy and pick up a new 1TB hard drive and I had Ubuntu up and running in no time. It was about $80 but they can be had for much less for a smaller one.

Just a note: my BIOS had a Hewlett Packard disk utility built in. It tested my HD as just fine. Seagate's tool did not. Replacing it was the cure. Don't always trust the little utility from the computer manufacturer if yours has one.

---

### Post by Versial on 2010-05-04
I have already verified the hard drive to another computer and the computer booted up and ran off a freshly installed ubuntu.  So I know the hard drive is still good.

---

### Post by HarrisonNapper on 2010-05-04
Looks like error 21 is that it's not detecting a bootable HDD. Make sure you're cabling your HDDs the same way they were originally, then check your BIOS and make sure the HDD appears in your BIOS under boot devices (set boot device and HDD priorities, as well).

[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

---

### Post by Versial on 2010-05-04
I figured out the problem, stupid me didn't see another set of sata connections on the motherboard (wires blocked =\) but those are working just fine, so I believe during the "surge", something went wrong with a small piece of the motherboard not allowing the original set of sata connections to initiate booting. Thanks for the replies.

---

