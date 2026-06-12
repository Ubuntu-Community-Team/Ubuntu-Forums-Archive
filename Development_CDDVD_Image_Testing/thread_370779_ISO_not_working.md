---
title: "ISO not working"
date: 2007-02-26
forum: Development CD/DVD Image Testing
---

### Post by Juzz on 2007-02-26
I downloaded the amd64 ISO yesterday - the md5 sum did not correspond to the one in the md5sums file.
The ISO was 701 MB and it would stop the loading after a while - the loader bar stopped moving and the CD stopped reading.

However I was able to get the i386 download to load up and run.

I was testing this on my Medion notebook with an AMD Turion.
Previous CD images of the 64bit versions did load - was this just a single upload gone wrong?

---

### Post by pochu on 2007-02-26
Hey Juzz!

Probably that was a occasional issue.  You can try to download today's iso, and I think it will go well.

Best regards
pochu

---

### Post by Juzz on 2007-02-26
It seems that I can only almost get my wireless network up and running with the current CDs (before going through an actual install).
It would however be nice if it could work - the i386 CD I tried yesterday could actually see my router, but even though I gave it the encryption key all attempts at getting the wireless running was in vain.
My notebook has a rt61 wireless card. Any thoughts on getting it running?

---

### Post by Juzz on 2007-02-26
Todays amd64 ISO ends up in a busybox prompt "(initramfs)" - not entirely sure what I need to do from there?
The md5sum checks out - otherwise getright would have complained...
:?

I am now trying to fetch the i386 build from today...

---

### Post by Juzz on 2007-02-26
I downloaded the i386 ISO from monday and somehow I got the wireless network up and running... Not by using Network Manager - but in terminal using iwconfig and dhclient...

I am now finalizing the install (and thus writing this from the install) :)

EDIT:
Now my newly installed Feisty system is up and running for the first time - now to fiddle with the rest of the software to install ;)

---

### Post by Juzz on 2007-02-27
Todays amd64 ISO also leaves me hanging at a busybox prompt and doesn't go any further - I have tried to leave out some of my usb stuff, but it still ends up at the prompt :?

Is this the intent of the devs? How do you get any further from there?

Like I wrote yesterday - the previous amd64 ISO images did load up fully...

Are any one else experiencing this?

---

