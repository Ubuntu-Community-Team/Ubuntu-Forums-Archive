---
title: "Can't &quot;Try without install&quot;"
date: 2009-06-15
forum: General Help
---

### Post by vadik2009 on 2009-06-15
Having an original Ubuntu 9.04 CD from Canonical and trying to "Try without install" it on a usual desktop, I get a message "init: rc-default main process (2812) terminated with status 127" while booting. What's wrong and what to do?

---

### Post by leandromartinez98 on 2009-06-15
Must be a defect on the CD. Try another one.

---

### Post by vadik2009 on 2009-06-15
That would be great, but, unfortunately, this CD runs OK on my notebook...

---

### Post by leandromartinez98 on 2009-06-15
It can still be a defect of the CD. I wouldn't go forward testing it in the Desktop without trying another CD first. Much less trying to install it from that CD, supose you get at the end a corrupted instalation, then you will have headaches.

---

### Post by vadik2009 on 2009-06-15
Maybe that wasn't the best decision again, but I also tried 6.10 and 8.04 on the same desktop &#8212; they just hung up in the process of "Trying without install"... And that were really working CDs...

---

### Post by wpshooter on 2009-06-15
Have you checked the integrity of the Ubuntu/Canonical CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by leandromartinez98 on 2009-06-15
> **vadik2009 said:**
> Maybe that wasn't the best decision again, but I also tried 6.10 and 8.04 on the same desktop — they just hung up in the process of "Trying without install"... And that were really working CDs...

Ok, then it seems that it is not a CD problem then. It is hard to know what can be going on with so few information. Do you have the CD of some other distribution (Debian, Fedora...) to test. Or any other bootable CD at all?

---

### Post by philcamlin on 2009-06-15
maybe its a problem with your cd tray?:(

---

### Post by donkyhotay on 2009-06-15
Could be an incompatibility, what hardware specs does that computer have? Also I would run the integrity test (even though the disc is most likely fine) as well as the memtest on the disc.

---

### Post by leandromartinez98 on 2009-06-15
A similar problem was posted here, although I'm not sure if they
found a solution:

[http://ubuntuforums.org/showthread.php?t=763265](http://ubuntuforums.org/showthread.php?t=763265)

---

### Post by skillllllz on 2009-06-15
Could be a failing optical drive, do you have another drive you could test in that desktop? Could also be faulty RAM, try running the Memory Test from the CD's boot menu.

It could even be that some hardware in the desktop is causing the some kind of conflict. I remember more than one occasion where a PCI modem or serial add-in card, caused this type of failure. Try removing anything that is not neccesary to boot, like PCI modems, network cards, USB or Firewire cards, etc. and then try to boot from the CD again. Please let us know what you discover.

---

### Post by rosswmcgee on 2009-06-16
Try installing with F4 safe mode.

---

