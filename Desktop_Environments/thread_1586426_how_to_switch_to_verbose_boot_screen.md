---
title: "how to switch to verbose boot screen?"
date: 2010-10-02
forum: Desktop Environments
---

### Post by davidmaxwaterman on 2010-10-02
This is the same for my laptop and my desktop systems.

Occasionally, when I try to boot my computer, it will get stuck and all I can see if the UBUNTU log and a series of dots - the colour of the dots isn't changing like normal, but is just static.

How can I, at that point, switch to the verbose screen with all the messages, so I can see what it's doing or why it is stuck?

I've tried ctrl-alt-fX, but none of those make any difference. The only things I've been able to do is ctrl-alt-del to restart it.

Thanks,

Max.

---

### Post by Alessandro.g89 on 2010-10-03
you have to edit the kernel command line in the bootloader (grub/grub2/lilo?) and remove the "quiet" word.

since you do that BEFORE the system boots, you're not able to know if it will get stuck or not

---

