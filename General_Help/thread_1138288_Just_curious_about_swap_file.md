---
title: "Just curious about swap file"
date: 2009-04-26
forum: General Help
---

### Post by metalclaw on 2009-04-26
I installed ubuntu without creating swap  file (i have 4GB of ram so i figured i dont need it), and now sometimes ubuntu freezes. I'm just curious if that might be the reason, or is it something else? 
also firefox is sometimes running really slow...

---

### Post by danwood76 on 2009-04-26
You still need a swap partition.
It will cause some applications to act strangely, you can just create a swap at the end of your hard disk and then add it to your fstab.

Heres an example fstab line:
```

/dev/sda1  none  swap  sw  0  0

```
then do a swapon from the terminal and it will work.

I have 4GB of RAM but quite often I see at least a small amount of swap in use.

---

### Post by fragos on 2009-04-26
IMHO a swap file is a good thing to have in case memory fills up. Linux is designed with the swap file to deal with this situation -- I'm not sure how well behaved it will be without one. Having enough memory so that swap is rarely used is a performance booster. On my box 1GB does the trick but we all have different ap mixes and I don't leave aps I'm not using open. Hibernation requires swap space equal to physical memory.

---

### Post by metalclaw on 2009-04-27
thanx, i'll do that as soon as i come home... hope that will help...

---

