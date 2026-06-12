---
title: "Poweredge 840 install problem."
date: 2010-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by john.k.bracey on 2010-09-10
This might be a dumb question, please forgive me if so.  I've recently acquired a spare poweredge 840 that I'm trying to install 10.04 on. The install completes successfully but when I reboot the machine I get a "No boot device available" message.  This is may not an Ubuntu issue per se, but wondered if any here had run into this before?

I can boot to the live cd and even mount the virtual drive (it has a SAS controller) so it would seem that it's something simple.

Thanks in advance.

---

### Post by john.k.bracey on 2010-09-10
OK, was a dumb mistake after all >.<

had a bad setting in the bios; somehow it wasn't looking for the virtual drive in the boot sequence.

thanks all.

---

