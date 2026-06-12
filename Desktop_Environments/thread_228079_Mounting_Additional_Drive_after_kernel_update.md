---
title: "Mounting Additional Drive after kernel update"
date: 2006-08-02
forum: Desktop Environments
---

### Post by metalcoat on 2006-08-02
Hello I followed the kernel.org upgrade to 2.6.17 guide on these forums and have updated my kernel. The thing is that whenever i try to mount the additional drive i get
```
mount: /dev/hdb1 already mounted or /home/chris/extra busy

```
but if i revert back to the other kernel it works fine and fstab mounts it like it should. I did not change any options except removed some video capture support as i would not need them and specified my processor P4.
The only reason i updated kernels was to get my zire 72 to work (may I add wonderfully now in kpilot[no workarounds:-D ])

---

### Post by metalcoat on 2006-08-02
I forgot to add that in fdisk no partition even shows up and it is a ext3 format and ext3 support is in the kernel

---

### Post by metalcoat on 2006-08-06
Well after almost giving up on the new kernel I found a page about EVMS and to patch the kernel and everything. I didn't feel like recompiling so I just deleted the evms package and rebooted no more errors and everything mounts like a champ.:grin:

---

