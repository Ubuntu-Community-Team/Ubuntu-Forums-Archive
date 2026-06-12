---
title: "Can only mount dvds/cds with &quot;mount /dev/scd0&quot;"
date: 2009-05-22
forum: General Help
---

### Post by hanzomon4 on 2009-05-22
Well Ubuntu has magically broke it'self again. The problem is that when ever I put a cd into the dvd drive it doesn't mount. I can hear it spin up but then nothing happens. Going to the computer section in nautilus and trying to mount the drive via the right click menu produces a "Unable to mount location can't mount file" error dialog popup. 

I can mount the drive by going to the CL and typing "mount /dev/scd0". Interesting thing is when I go to the computer section in nautilus the CD-RW/DVD RW drive icon still shows that nothing is mounted. I do however see that cdrom0 is mounted.

Any ideas

---

### Post by KhurramM on 2009-05-22
First: U have to see that your auto mount is active.

Second: If devicd is shown in MyComputer, double clicking it will auto mount it, u dont need to cli every time.

For auto mount, u need to search that. ;)

---

### Post by hanzomon4 on 2009-05-29
Nope... it was powertop telling me to stop polling the cd/dvd drive

The fix
```
 sudo hal-disable-polling --device /dev/cdrom --enable-polling
```
Then manually mount a cd then eject. It should work automatically the next time.

---

