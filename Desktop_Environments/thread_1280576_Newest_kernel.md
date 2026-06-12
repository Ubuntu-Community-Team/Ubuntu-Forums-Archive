---
title: "Newest kernel"
date: 2009-10-02
forum: Desktop Environments
---

### Post by dvlchd3 on 2009-10-02
Has anyone else had issues with the latest kernel update?  I just updated last night, upon restart, I receive a cpc error, system halting right after selecting the new kernel in GRUB.

When booting into the old kernel, all is fine...any help?

---

### Post by dvlchd3 on 2009-10-02
My mistake, I actually receive the following error on boot:

```

crc error

System halted...
```

The kernel version I upgraded to is 2.6.28-15-generic from 2.6.28-11-generic

Anyone else experience this problem, or have a potential solution?

---

### Post by acidPython on 2009-10-02
I thought the newest kernel was 2.6.30?

---

### Post by wojox on 2009-10-02
No it's 2.6.28-15-generic on 9.04. I haven't had any problems though to answer your question.

---

### Post by dvlchd3 on 2009-10-02
Searching around, it seems this is a "Cyclic redundancy check - is a non-secure hash function designed to detect accidental changes to raw computer data, and is commonly used in digital networks and storage devices such as hard disk drives"  (Wikipedia [http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check))

Also, other threads have recommended checking your harddrive, cd-drive, and memory.  I do know I have some bad memory sectors, however, it never really seemed to affect anything before now.

It also seems odd that this would only happen for the newest kernel version, but not the past versions.  Is there something in the new release that would cause this error to occur?

---

### Post by steveneddy on 2009-10-04
That's to be expected when running Beta software.

It just comes with the territory.

Hardy and Intrepid don't experience those issues due to the fact that those earlier releases are "stable".

---

