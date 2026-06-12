---
title: "what does SMART data mean ?"
date: 2010-07-05
forum: Desktop Environments
---

### Post by AM_SOS on 2010-07-05
hi,

can someone please point to some link which explains how to interpret the results of the SMART test performed by Palimpsest in 10.04 ?

i am specifically looking for info on the physical state of the HDD.

thanks!

---

### Post by hansdown on 2010-07-05
Hi AM_SOS.

Be careful with Palimpsest. There have been instances of it falsely reporting bad sectors in hard disks.

[http://www.google.com/search?client=ubuntu&channel=fs&q=how+to+interpret+the+results+of+the+SMART+test+performed+by+Palimpsest+in+10.04+%3F&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=how+to+interpret+the+results+of+the+SMART+test+performed+by+Palimpsest+in+10.04+%3F&ie=utf-8&oe=utf-8)

---

### Post by philinux on 2010-07-05
> **AM_SOS said:**
> hi,

can someone please point to some link which explains how to interpret the results of the SMART test performed by Palimpsest in 10.04 ?

i am specifically looking for info on the physical state of the HDD.

thanks!

If it says SMART Status Green Blob Disk is healthy, thats good.

The one parameter to watch now and then is the "Reallocated Sector Count".

All HD's will eventually reallocate bad sectors themselves.

My 2 year old pc with two HDs has zero reallocated sectors.

[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

As an alternative to palimpsest there is gsmartcontrol in the repo.

---

### Post by AM_SOS on 2010-07-05
thanks philinux and hansdown !

this SMART data has had me worried for some time now.

philinux you say that your 2 yr old PC has 0 reallocated sector count and this has me even more worried about the health of my toshiba A200's HDD.

i reproduce below the "Assessment" and "Value" entries under the "reallocated sector count" Attribute in the Palimpsest SMART test. this is the only parameter which is marked with red in the SMART report. all others are either all green or simply unavailable.
```

Assessment - Warning

Value - 

Normalised :    100
Worst :         100
Threshold :     50
Value :         23 sectors
```

can you tell me what these stats imply for the health of the internal HDD ?

thanks!

---

### Post by philinux on 2010-07-05
[http://www.almico.com/sfarticle.php?id=2](http://www.almico.com/sfarticle.php?id=2)

As it's coming up red I would make sure I kept regular backups.

Keep an eye on the number of reallocated sectors every few days. It might stay the same or go up.

---

### Post by AM_SOS on 2010-07-05
thanks philinux,

now i know why SMART is so important.
unfortunately, most of the very useful details in the link you provided are double dutch to me as i am at best an amateur when it comes to hardware.

so when you ask me to monitor the result of the SMART test every couple of days, what exactly do you have in mind ? i mean, how am i supposed to know when it is doomsday for the HDD ?
when these values become half ? or one fourth of what they are now ?

and more importantly, what will be the options before me since i will not be going in for a replacement of the internal HDD ?

let me also bring to your notice the interesting fact that in terms of overall performance the HDD seesm to be doing ok. e.g. there is no noticeable sound while the drive is working, and neither has the computer slowed down.

thanks!

---

