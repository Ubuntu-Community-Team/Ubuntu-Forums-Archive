---
title: "Crash!"
date: 2005-01-06
forum: Desktop Environments
---

### Post by techn9ne on 2005-01-06
I moved my mb and h/w to a new case I try and boot up and it says:

Unable to open /dev/console
Kernel Panic!

I have a dual boot w/ windows and it works fine with windows so its not a h/w issue.

What can I do to this this?

I tried using recovery console and it gave me same error.

---

### Post by Rancoras on 2005-01-06
You didn't add or subtract any hardware in the move?  Move any cards on the mobo?  everything is exactly as it was, just in a new case?

---

### Post by techn9ne on 2005-01-06
No I didnt change any h/w . I moved some PCI things to different slots.

Is there a rescue mode on the disc?

---

### Post by techn9ne on 2005-01-06
Ok I fixed it. What happened is the IDE cables didn't get put on the right place and grub was getting confused. Windows was working because its the first partition but the kernel was loading and then getting confused 'cause the partitions weren't lining up like it expected.

---

