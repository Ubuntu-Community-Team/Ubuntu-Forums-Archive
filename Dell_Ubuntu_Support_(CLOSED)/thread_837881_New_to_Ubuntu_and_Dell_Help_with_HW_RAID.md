---
title: "New to Ubuntu and Dell Help with HW RAID"
date: 2008-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dupreesdiamond on 2008-06-22
Greetings. I will save you all the gushing regarding Ubuntu, as that would take a while...

Anyway I was gifted a Dell Precision 390 64bit workstation which was riddled with Viruses.  So I DLed Ubuntu 8.04 desktop edition, slapped it in and installed XP via virtual box all in about an hour (SWEEET!!) 

currently there is one 80GB SATAII HDD installed but I want to install 3 more 500GB SATAII drives in this puppy and set it up as a RAID5 array.  I was poking around the BIOS and it appears that the dell has hardware raid support built in but I am not sure how I go about taking advantage of this once my new drives get in.  So this is the root of my question, what do I need to do to get the other 3 disks set up as RAID5 and access this disk space from Ubuntu and share it out to my network (share video/audio to my XBOX Media Center for one) and store important files (family photos, financials).

So...I am at your mercy.  New to RAID (read things about it but no hands on experience), New to ubuntu (though not Linux, had a SuSE box running for the past few years on a 9 year old system that I built back when I had time on my hands), New to this Dell (my other PC is a low end desktop that is 5 years old).

So I am at ground 0 here in this journey and looking for some help to get going down this path.

Thanks for your patience

---

### Post by rickyjones on 2008-06-23
> **dupreesdiamond said:**
> Greetings. I will save you all the gushing regarding Ubuntu, as that would take a while...

Anyway I was gifted a Dell Precision 390 64bit workstation which was riddled with Viruses.  So I DLed Ubuntu 8.04 desktop edition, slapped it in and installed XP via virtual box all in about an hour (SWEEET!!) 

currently there is one 80GB SATAII HDD installed but I want to install 3 more 500GB SATAII drives in this puppy and set it up as a RAID5 array.  I was poking around the BIOS and it appears that the dell has hardware raid support built in but I am not sure how I go about taking advantage of this once my new drives get in.  So this is the root of my question, what do I need to do to get the other 3 disks set up as RAID5 and access this disk space from Ubuntu and share it out to my network (share video/audio to my XBOX Media Center for one) and store important files (family photos, financials).

So...I am at your mercy.  New to RAID (read things about it but no hands on experience), New to ubuntu (though not Linux, had a SuSE box running for the past few years on a 9 year old system that I built back when I had time on my hands), New to this Dell (my other PC is a low end desktop that is 5 years old).

So I am at ground 0 here in this journey and looking for some help to get going down this path.

Thanks for your patience

1. Google the hardware RAID controller's product # and/or serial # to see if it is supported hardware.
2. Install your new disks and use the BIOS RAID utility to configure your RAID5. Load up Ubuntu and see if it recognizes one large drive or three smaller drives.
3. If it is not supported then you can use MDADM to create and manage a RAID5 volume. It might be a tad slower but will be quite usable.

Hope this helps!

Sincerely,
Richard

---

### Post by dupreesdiamond on 2008-06-23
Thank you!  The help is much appreciated and  I will update this thread in the end with my learnings.

---

