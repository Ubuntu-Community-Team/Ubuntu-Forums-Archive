---
title: "I'm laoding and running 8.10 from a 4GB SD card"
date: 2009-01-02
forum: General Help
---

### Post by hatewindows on 2009-01-02
My question is--Why does each and every program run a little slower then it would if i was using the HD? I did a full install of ubuntu 8.10 even the boot sector is on the flash memory card-My usb is 2.0

I would think that the flash card would run rings around the Hard drive No?

Thanks for any help and or any tweeks to overcome this problem.. 

Happy holidays!!                 MARK

---

### Post by Slim Odds on 2009-01-02
> **hatewindows said:**
> I would think that the flash card would run rings around the Hard drive No?                 MARK

FLASH reads are very fast. FLASH writes are very slow.

If the entire system in on FLASH, that bad boy will be dead in no time.

---

### Post by Tim Sharitt on 2009-01-02
The speed of a flash drive varies from manufaturer and models. Even though some flash drives claim fast serial access, the random access which you normally see is often considerably slower than their HDD counterparts.

---

### Post by Slim Odds on 2009-01-02
> **Tim Sharitt said:**
> The speed of a flash drive varies from manufaturer and models. Even though some flash drives claim fast serial access, the random access which you normally see is often considerably slower than their HDD counterparts.

That is incorrect. The random access is much faster than the HDD which must move the physical head to read data. The FLASH is pure solid state and hence, no head movement.

The problem is that his swap, etc. is on the FLASH device. This will require writing to the FLASH. That is bad (slow and it will wear out the device).

---

### Post by hatewindows on 2009-01-02
Can i change any settings to use my HD as a swap area?

---

### Post by dcstar on 2009-01-02
> **hatewindows said:**
> My question is--Why does each and every program run a little slower then it would if i was using the HD? I did a full install of ubuntu 8.10 even the boot sector is on the flash memory card-My usb is 2.0

I would think that the flash card would run rings around the Hard drive No?

Thanks for any help and or any tweeks to overcome this problem.. 


The Live USB install application is designed to be used with RAM based devices, or you could install one of the eeePC Ubuntu distros which are also optimised for solid state drives.

---

