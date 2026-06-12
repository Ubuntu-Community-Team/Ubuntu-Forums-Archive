---
title: "Hardware, BIOS, HDD, or Software issue?"
date: 2013-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hogfan on 2013-01-04
I have been experiencing a strange problem on my Dell 14Z for about the last month. A lot of times when returning from Hibernation or simply when cold booting the laptop, I get a message stating no boot device found and then the laptop tries to PXE boot.  Powering off and back on usually fixes the problem, but it is very annoying.  The first few times this happened I freaked out thinking my HDD was failing.  However, I have run multiple Dell Diagnostics tests, multiple short & long tests on the HDD with Seatools (Seagate HDD) and no problems are found. S.M.A.R.T. tests also pass from the Disk Utilities in Ubuntu. I did ome digging on the Dell site and found that the current BIOS version is A06 & my installed version was A03.  There was also a Segate HDD firmware update that addressed an issue with HDD spin-up time.  I thought this was most likely the culprit.  So I installed WIN7 in a separate partition so that I could perform these two upgrades from within WIN7 (since there's no linux versions of these updates).  Of course I had to re-install GRUB2 to get my sytem boot back to Ubuntu after killing the WIN7 partition.  However, after all of this I still have the same issue randomly when booting up.  So my question is this: The 14Z is less than a year old, does this sound like a possible hardware issue that I should get addressed with Dell ASAP?  Does it sound like the MB/Controller or the HDD?  I can't see the HDD being the issue since it passes all tests, and I can't see it being GRUB since the boot device is never found.  Suggestions? Thanks.

-hogfan

---

### Post by takuie on 2013-01-04
Try updating bios to a10.  I had similar problems on an older laptop and this seemed to fix it for me.  I don't know how to update bios through Ubuntu, but dell had an easy bios update via windows.  Best of luck to you.

---

### Post by hogfan on 2013-01-04
My bad, I meant to say Dell "XPS 14Z".  As far as I can tell, the latest BIOS available for this model is A06.

-hogfan

---

### Post by gerrman97 on 2013-01-09
Hello. This is a wonderful topic ;-). Kidding. I would say maybe it could be a MB to HDD contact error with the pins. What kind of hd is it. SATA? probably because its so new. You could purchase or borrow a SATA hd from a nearby computer store. Or buy a brand new one. I have 3 hds per type and style of computer. I have an hp frankenstien computer. 3 hds all IDE. My newer Dell that i had, was a laptop it had 3 SATA hds. Point is, i know alot about hd problems. Sometimes this happens with my hp. Try reseating the hd. And then try to test the port with a different hd. If it does the same thing, its your motherboard. If it boots right away, hd. If you want more advice pm me. Ill give you my email and website address. Good luck!

---

