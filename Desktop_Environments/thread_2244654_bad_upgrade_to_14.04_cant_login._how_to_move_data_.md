---
title: "bad upgrade to 14.04 cant login. how to move data to 12.04 on same hdd"
date: 2014-09-17
forum: Desktop Environments
---

### Post by mrezstreet on 2014-09-17
I had a older 13.0x ubuntu install that wouldnt update..moved to 14.04 and the password would not work... It was the only os on the drive, so made a new 12.04 disk and installed ( no option to reinstall or repair?? ) it along with the bad 14.04. How can I get my 1000+ pictures and docs off the 13.ox>14.04 install then format that partion? I looked all over and didnt search it right...or was to dumb to know I found the info.

Thanks tons you ubuntu guruz

---

### Post by ian-weisser on 2014-09-17
This assumes that your data still exists and is uncorrupted. It seems like you did at least one repartition and perhaps two full installs. While Ubuntu will try very hard to preserve the data in your /home directory, the unexpected occasionally does occur.

1) Boot from a live USB. The version may not matter - any will work for simple file management. If you know what version or flavor you want to install, it will save you a step later.

2) Mount the hard drive, and insert/mount your backup media.

3) Copy all your data to the backup media.

4) Eject and remove your backup media.

5) Now that all your data is safe, install whatever you want in either partition.

---

### Post by mrezstreet on 2014-09-18
I will give it a shot. thanks!

---

### Post by mrezstreet on 2014-09-18
any way to get to it via pathing ( and I have no idea what pathing ) from the 12.04?

---

### Post by mrezstreet on 2014-09-18
ok when I try to go to home on 14.04 it tells my I dont have permission to view content? am I out of luck?

---

### Post by ian-weisser on 2014-09-18
> **mrezstreet said:**
> any way to get to it via pathing ( and I have no idea what pathing ) from the 12.04?

Mount the partition, if it's not already mounted.
If you can't locate it, then it may not be mounted.

Uh, if you plan to reinstall or repartiton after preserving your data, be aware that backing up to a different partition on the same disk offers only limited protection. A typo can still wipe out your data.


> **mrezstreet said:**
> ok when I try to go to home on 14.04 it tells my I dont have permission to view content? am I out of luck?

From within 14.04, perhaps. That's why it's better to use a LiveUSB or the 12.04.

You should be able to use sudo to access from within 14.04. Beware copying that way, though - the new new copies will be owned by root.

---

### Post by mrezstreet on 2014-09-20
I need to take a free part of the hdd and format it to be safe place to dump the data and keep it safe from me lol. I did mount the 14.04 from within 12.04 and via live disk...still didnt let me to see anything. but it still shows like 9gb of uses space on that space.
If I can save the data im going o be so happy. a summer of photography work would be saved! So how would I get that data from within 12.04? I could dump it on a removable drive

---

