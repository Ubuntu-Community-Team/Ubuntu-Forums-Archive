---
title: "Using the Dell Recovery Partition"
date: 2009-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Odd_sam on 2009-08-01
I was curious about Dell's Recovery Partition. I am currently dual booting with Windows Vista and I wish to reload Vista. I don't mind what dell has put on the computer as far as additions and it's easier to just reload vista via the Recovery Partition which will do a factory reimage. I am curious if it will wipe out my ubuntu partition if I do this. I would much rather reload vista with the OEM disk vs possibly wiping out ubuntu. Does anyone have any suggestions on how to do this/if using the recovery partition would be safe to use?

---

### Post by wojox on 2009-08-01
If it's a factory image reinstall chances are it will take over the whole drive. I don't think it will give many options.

---

### Post by Odd_sam on 2009-08-01
That's what I was thinking. But then I wondered how it would do the image if it reformats the hard drive. Cause doing that would erase the image its trying to copy to the hdd. I doubt it would load it to the RAM because the image has to be bigger than 4gb and what about people who want to do that and don't have enough ram... So one would think it doesn't wipe the entire drive, maybe just every block except for the ones occupied by the image.

---

### Post by gbrainin on 2009-08-02
If it is like the recovery partition that comes with the Ubuntu-preloaded machines (and I suspect it is), then it in fact repartitions the drive to its factory condition.  I assume you're right about it not touching the recovery partition itself.

---

### Post by Odd_sam on 2009-08-02
That's what I suspected. Thanks.

---

