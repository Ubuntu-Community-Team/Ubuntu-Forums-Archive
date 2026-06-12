---
title: "ACPI &amp; APCI are they different ?"
date: 2005-10-02
forum: Desktop Environments
---

### Post by railz68 on 2005-10-02
Still looking for things to try fixing the random lock-ups. I found this thread here [http://www.ubuntuforums.org/showthread.php?t=26385&highlight=xid]("http://www.ubuntuforums.org/showthread.php?t=26385&highlight=xid")

It's says to turn off APCI, but in the two examples he gives, they are different. Which one is right ?  Don't wanna do this and find I can't boot properly.

> STEP 2: TURN OFF THE APCI
- Edit "/boot/grub/menu.lst" and add the following option to the kernel

Code:
pci=noapci

Example:
Code:
kernel /vmlinuz-2.6.10-5-386 root=/dev/hdf2 ro quiet splash pci=noacpi

See how 1st it says "noapci", then in the example it's "noACPI".

Also, which ever one is right, what is it (power management ?).

---

### Post by terigox on 2005-11-09
Hello railz68!

My guess is just some typo's in there, ACPI is what you're looking for, and yes it  stands for Advanced Configuration and Power Interface, you can read up on it some more <a href="http://www.acpi.info/">here</a> if you're interested.

Hope this helps!

---

