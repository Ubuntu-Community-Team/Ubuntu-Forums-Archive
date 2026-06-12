---
title: "Just upgraded to Oreo on my phone, MTP stopped mounting"
date: 2017-09-13
forum: Desktop Environments
---

### Post by sirwizkid on 2017-09-13
Hi All,
I just put the Oreo update on my phone this weekend, and now MTP comes up with a error every time I try to mount my phone filesystem.    Has anyone else seen this?

Unable to mount Pixel
Unable to open MTP device '[usb:004,010]'

That's the popup spam that comes up.  sometimes one or two boxes with sequential numbers, one time 4 boxes....  

I suspect Google changed something, but can't verify that.

I didn't see any other mtp messages about this in this forum...

---

### Post by jeremy31 on 2017-09-17
You may have to enabled developer mode/USB debugging, then plug the phone in and see if it asks you to trust the computer.  You may find that clearing the list of trusted devices gets it working
I just did the Oreo update of my Nexus 6P and it still works

---

### Post by gdhgdh on 2017-09-17
I have the same issue and found an easy workaround.

Browse to Settings -> System -> Developer options -> Select USB Configuration (it's about half way down the list).

Choose 'MTP (Media Transfer Protocol)' in the popup. Even if it is already selected, tap it again!

For me, that means File Explorer in Ubuntu pops open with the normal 'Internal shared storage' option. From there I can browse the files on the phone.

---

### Post by gifford on 2017-10-22
Thanks gdhdh! It worked for my pixel after a lot of head scratching.

---

