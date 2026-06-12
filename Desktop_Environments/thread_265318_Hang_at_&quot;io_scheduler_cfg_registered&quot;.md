---
title: "Hang at &quot;io scheduler cfg registered&quot;"
date: 2006-09-25
forum: Desktop Environments
---

### Post by BorgHunter on 2006-09-25
I recently had some power supply issues that prompted me to replace the very same power supply. Upon the replacement thereof, Linux suddenly started to hang, every time, on "Ok, booting the kernel...". Entering recovery mode, I note that it specifically hangs at "io scheduler cfg registered". The only thing that changed with my system configuration is the floppy drive, which is connected to the motherboard but is receiving no power due to the new power supply, which oddly includes no connection for it. Oh well, it's not like I care anyway. I tried loading it both with and without disabling the floppy in BIOS before booting; no dice. Windows, which incidentally is on a separate hard drive, works fine. Thoughts?

---

### Post by BorgHunter on 2006-09-26
Make that "io scheduler cfq registered". The g and q look quite similar...

---

### Post by BorgHunter on 2006-09-27
Upon adding the following to my boot options: "noapic acpi=off nofb", I get another message: "PnPBIOS: Resource structure does not contain an end tag". It still hangs at the same instant, though. And I've noticed that a very old kernel from Breezy does manage to boot, but obviously the nVidia drivers don't want to work, and I don't want to imagine what other conflicts I'd have if I tried to load that kernel. I'm completely stuck here, guys. Any thoughts?

---

### Post by BorgHunter on 2006-09-29
I take it I've managed to stump everyone...I can't get into Linux at all until this problem is resolved. Are there *no* thoughts at all?

---

