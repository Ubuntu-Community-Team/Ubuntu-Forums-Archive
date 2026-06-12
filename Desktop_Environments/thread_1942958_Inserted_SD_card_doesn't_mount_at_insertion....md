---
title: "Inserted SD card doesn't mount at insertion..."
date: 2012-03-18
forum: Desktop Environments
---

### Post by Moozillaaa on 2012-03-18
It's my digital cam SD card, which I set to 'Do Nothing' when inserted. Now it doesn't even show under 'Computer' to mount.

How do I reverse the setting of inserted media / Do Nothing???

---

### Post by Moozillaaa on 2012-03-18
It still auto mounts in Hardy (another partition), and if I reboot 10.04 with the card inserted, it does show up mounted...

---

### Post by Moozillaaa on 2012-03-18
Must have had something to do with fstab file...

I yanked it while mounted (booted with card INSERTED), then rebooted without the card, THEN re-inserted the unclean UNmount, and it mounted properly.

And it started when I did the setting to do NOTHING AT INSERTION??? 

I am believing this is a bug; if advisable, I could try to re-create the situation.

---

### Post by kurt18947 on 2012-03-18
Not trying to be smart but is it doing exactly what you told it to do -- nothing? Including not mounting?  Is there a setting to mount but not open any files?

---

### Post by Moozillaaa on 2012-03-18
> **kurt18947 said:**
> Not trying to be smart but is it doing exactly what you told it to do -- nothing? Including not mounting?  Is there a setting to mount but not open any files?

No, it is not doing exactly what the setting was set to.

I didn't make full disclosure in the first post. What WAS happening was an F-Spot pop up, with action options for 'Just Inserted Media'. I chose 'Do Nothing', and that was the last time it appeared ANYWHERE, after the next unmount. Nowhere did it appear to even MOUNT, when inserted afterward.

It is a bug I'm about 99% certain.

---

### Post by mister_p_1998 on 2012-03-19
Try mounting the card in an XP system then cleanly unmount. Ubuntu wont mount an uncleanly unmounted device. I've had this before on mine and the only way to fix it is to mount/unmount in XP, VirtualBox is fine.
Steve

---

