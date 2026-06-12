---
title: "Method required to safeguard against live CD access to PC files!"
date: 2009-06-20
forum: General Help
---

### Post by Rytron on 2009-06-20
Hi.
Is there a straight forward way that still permits ssh & samba but stops people accessing my files via a live CD?

Would I need to use something like these:

```
chmod 0750 $HOME
```
or
```
chmod 0700 $HOME
```

Not sure exactly what the two above commands do, so I'd appreciate if someone could explain them. Thanks.

---

### Post by michy99 on 2009-06-20
Disable booting from CD in bios and set a bios password. Of course, someone could remove the battery long enough to reset the bios, or remove the disk and connect it to another system.

---

### Post by sdennie on 2009-06-20
If someone has physical access to your machine, the only way to prevent them from reading your data is by having it encrypted.  Permissions are enforced by the kernel and configuration files.  If you mount a disk using different configuration files, you can access whatever data you want unless it's encrypted.  In which case, you can still delete/modify/corrupt the data but, you can't read it.

---

### Post by aysiu on 2009-06-20
It depends on what you mean by "safeguard."

If you just want to prevent a casual stroller-by from booting a live CD, you can disable booting from CDs in the BIOS and add a BIOS password, as well as adding a Grub password and removing the recovery mode option.

Of course, if the person strolling by has about a half-hour and a few screwdrivers, she can easily reset the BIOS password. But if she's truly a casual stroller-by and has only a few minutes, it won't be worth it for her to take the computer apart just to boot a live CD (or to remove the hard drive).

If, however, you're leaving your machine alone with untrustworthy individuals for long periods of time, they can do whatever they want to your computer and data. Encryption is the only way to protect your files... and that will only prevent them from being seen, not from being deleted.

---

### Post by Rytron on 2009-06-21
How about using chattr to prevent data deletion via a live CD or other methods?

---

### Post by aysiu on 2009-06-21
> **Rytron said:**
> How about using chattr to prevent data deletion via a live CD or other methods?
That won't work. It just changes permissions on stuff, right?

With a live CD, permissions mean nothing.

---

### Post by tubbygweilo on 2009-06-21
Physical access is everything. 

If you feel uneasy about leaving your wallet containing say house keys, credit cards, debit cards, love letters, photos of friends.... at a location then you should also feel uneasy about leaving your pc at the same location.

Encrypt the disk, remember the pass phrase and still keep an eye on your pc and you should be safe.

---

### Post by Rytron on 2009-06-21
Thank you all for the advice.

---

