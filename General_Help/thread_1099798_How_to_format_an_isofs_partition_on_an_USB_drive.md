---
title: "How to format an isofs partition on an USB drive"
date: 2009-03-18
forum: General Help
---

### Post by Gr8world on 2009-03-18
Ok, my father gave me a 1Gb USB drive but when I insert it in my Ubuntu box it mounts two things: one "887 Mb Media" which is formatted as fat32 and the other "DEME" which is formatted as isofs. The case is that I can't format "DEME" with gParted because it is isofs and I can't format it with Brasero because it's not a CD. 

And if I do ```
mkfs -t ext3 /dev/scd1
``` it says 

```
mke2fs 1.41.3 (12-Oct-2008)
/dev/scd1: Read-only file system while setting up superblock
```

So my problem is, I want to format both "887 Mb Media" and "DEME", so I get the full 1Gb free on the USB drive, but the question is HOW?

Sorry for the long speech and my bad English...

---

### Post by igor. on 2009-03-18
You can try this.

First of all, open up gparted to find out the device name of the USB drive. Make sure you have the correct name - or you may lose all your data. The device name is something like /dev/sdb or /dev/sdc. I'll refer to it as /dev/sdX.

In a terminal, type this:
```
sudo dd if=/dev/zero of=/dev/sdX
```

Then reboot your computer and try to reformat the USB drive.

But be extremely careful, entering the wrong name will wipe whatever device you are talking to - perhaps your primary hard drive.

---

### Post by Gr8world on 2009-03-18
Yes, I did this but it'll only format "887 Mb Media" because it has the name /dev/sdc
and "DEME" has the name /dev/scd but actually they are on the same drive. 

I can format "887 Mb Meadia" with gParted but not "DEME".

---

### Post by Gr8world on 2009-03-18
And if I do ```
sudo dd if=/dev/zero of=/dev/scd
``` 
Then it says 
```
dd: writing to `/dev/scd': No space left on device
1018649+0 records in
1018648+0 records out
521547776 bytes (522 MB) copied, 3.98797 s, 131 MB/s
```

Sure because it is read only.

---

### Post by Gr8world on 2009-03-19
And yes, by the way thank you for your response.
But I'm still stuck here...

---

### Post by igor. on 2009-03-19
Hmm, even linux thinks you have a CD inserted, which is probably why it will not let you write to it. Not sure what to do here.

---

