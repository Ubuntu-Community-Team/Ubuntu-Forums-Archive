---
title: "Problems with partitions list with Feisty"
date: 2007-01-15
forum: Development CD/DVD Image Testing
---

### Post by domcio on 2007-01-15
I have problems with installing Feisty herd2 alternate iso on my Toshiba Tecra A2. When it comes to partitioning there is no manual partitioning options, and partitions list with other options is very weird. There is no problem on 6.10.

Regards

---

### Post by pochu on 2007-01-15
Please domcio, search for this bug at Launchpad, and if it hasn't been reported, do it.

Thanks for testing
Pochu

---

### Post by domcio on 2007-01-15
> **pochu said:**
> Please domcio, search for this bug at Launchpad, and if it hasn't been reported, do it.

Thanks for testing
Pochu

Thanks Pochu, i just filled in a bug report #79490, unfortunately it went to Ubuntu instead of Ubuntu/Feisty. Should it work this way?

regards,
domcio

---

### Post by pochu on 2007-01-16
> **domcio said:**
> Thanks Pochu, i just filled in a bug report #79490, unfortunately it went to Ubuntu instead of Ubuntu/Feisty. Should it work this way?

regards,
domcio
Yes, that's fine.

I've seen your bug, but I've not confirmed it, because I don't have that problem :D

Regards
Pochu


P.D.: Thanks for your report!

---

### Post by domcio on 2007-01-16
> **pochu said:**
> Yes, that's fine.

I've seen your bug, but I've not confirmed it, because I don't have that problem :D

Regards
Pochu


P.D.: Thanks for your report!

Is there a way to make a "screenshot" during ubuntu install?

---

### Post by Henrik on 2007-01-16
> **domcio said:**
> Is there a way to make a "screenshot" during ubuntu install?

Yes. Pressing the PrtScr button should work. If you have a working network in the live session you can upload it here or in a bug report.

---

### Post by pochu on 2007-01-16
But he is using the alternate CD. Does the PrintScreen work there?

---

### Post by Henrik on 2007-01-16
Erm, no. Sorry my bad. It would work if you ran it in a virtual machine though. [http://virtualbox.org/](http://virtualbox.org/) works nicely.

---

### Post by domcio on 2007-01-16
> **Henrik said:**
> Erm, no. Sorry my bad. It would work if you ran it in a virtual machine though. [http://virtualbox.org/](http://virtualbox.org/) works nicely.

But in virtual machine you don't use a real HDD, do you? I'll try a Desktop CD and see if it works for me.

---

### Post by pochu on 2007-01-16
You can take a photo!!! :D

---

### Post by domcio on 2007-01-17
> **pochu said:**
> You can take a photo!!! :D

Yeah, I thought about it too ;)  but for now i just did an dist-upgrade to Feisty from Edgy and it all went well, both fdisk and parted see partition list as they should. 
I have also tried a desktop CD, but since it uses gparted everything is ok there, so it looks like there is a problem with partitioning only on alternate CD and netinst (they use the same packages, aren't they?) 

regards,
domcio

---

### Post by pochu on 2007-01-17
Then you should report a bug at Launchpad. Please do it if you haven't done it yet (first search for duplicates).

Thanks
Pochu

---

### Post by domcio on 2007-01-17
Ok, so here are 3 photos of my laptop screen in attachment:
- feisty_part_01.jpg shows first screen during partitioning
- feisty_part_02.jpg shows screen after choosing cdrom-retreiver
- feisty_part_03.jpg shows screen after choosing "No" and then "Go back"

hope you like it ;) I've also completed my bug report.

---

### Post by pochu on 2007-01-17
And where's the bug?

---

### Post by domcio on 2007-01-17
> **pochu said:**
> And where's the bug?

here you go:

on 1'st screen there is no manual partitioning option though it's displayed that I can use that option (well description is not fully visible on this photo). What is this cdrom-retriever by the way - see results on 2'nd photo??

on 3'rd screen all partitions are displayed incorrectly,  and if I don't see what system is going to do I won't take a risk.

when I run partman from installed version of Feisty or from Desktop CD terminal it looks ok (see next photo)

---

### Post by pochu on 2007-01-18
Thanks, but I said where the bug report is :D

---

### Post by domcio on 2007-01-18
> **pochu said:**
> Thanks, but I said where the bug report is :D

OK, it was a little confusing :p , it's still the same bug report #79490, just added some comments. :cool:

---

### Post by pochu on 2007-01-18
Ok, I didn't look again to the report. My fault.

Regards
Pochu

---

