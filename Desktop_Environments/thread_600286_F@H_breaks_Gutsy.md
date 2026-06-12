---
title: "F@H breaks Gutsy"
date: 2007-11-02
forum: Desktop Environments
---

### Post by DFreeze on 2007-11-02
I recently upgraded to Gutsy on my desktop. It took half an hour, and apart from some minor itches (USB / SD drives don’t mount, nVidia won’t work) the system seemed ok. But yesterday it suddenly didn’t boot anymore, spewing some lines about Folding At Home not finding something. 

So I tried booting in recoverymode, and I discovered the only kernels that were offered were the Feisty ones. My upgrade didn’t finish right, and I’m left with a hybrid Feisty – Gutsy system…

True, I should have deactivated F@H before doing the upgrade, I suppose, but I had completely forgotten about it. Is there a way to recover from this mess, and make F@H not bootup (I have it load as a service) from the command prompt? Or does the kernel mess indicate the system is borked and a fresh install is the only way out?

I tried to rename /etc/init.d/folding to …/folding.OLD, just to see what happens, but that changes nothing. How do I disable services?

---

### Post by stinger30au on 2007-11-02
if u put the ubuntu live cd in and boot off it you should be able to see your data and copy it to dvd etc before scrubbing it and starting again

---

### Post by DFreeze on 2007-11-03
I reinstalled from the CD, since I have my /home on a separate partition. That took just half an hour, and I was back in business. Too bad the upgrade didn't work out, but trying to recover from it would take many times half an hour...

---

