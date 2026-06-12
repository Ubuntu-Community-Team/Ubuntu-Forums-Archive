---
title: "Mini 9 Hibernate"
date: 2009-02-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by techstop on 2009-02-02
Hi all. I bought a Mini 9 with Windows XP a few months ago (no ubuntu dells available in Australia unfortunately), and just the other week I installed 8.10. Everything is working great, except for suspend/hibernate.

If I suspend, something seems to drain the battery in the background so that the next morning, it's completely flat.

If I hibernate, I get an error like;

```
btusb_intr_complete: hci0 urb efdcb380 failed to resubmit (2)
```

and after about 45 secs the netbook turns off. (no power LED) If I then power on, it seems to go through the whole boot process (BIOS POST, grub, ubuntu splash screen etc), and I have to log into a "locked screen" but then I have my session ready the way I left it. ie. it seems to have hibernated

So, two questions;

1. Is suspend meant to drain the battery like it does?
2. Is there any way to get hibernate working better? ie faster to shut down, and without going through the whole boot process again. OR, is it working the way it's meant to?

Cheers...

---

### Post by mister_pink on 2009-02-02
I think the answer to both questions is "thats just the way it is". Suspend requires power as it keeps the current session in RAM, which requires constant power to store information. 

Hibernate puts the session detail onto the hard disk and then completely powers off the machine. This means that when you turn it back on it has to go through the bios etc as this is what must happen when you first turn the power on to a machine. 

I am surprised that suspend completely flattens the battery overnight though, I have never left my laptop suspended that long but I thought it only needed a little power.

---

