---
title: "couldn't mount a dd image"
date: 2007-12-07
forum: Desktop Environments
---

### Post by Nabilsar on 2007-12-07
The loop back device didn't work correctly on ubuntu 7.04 i'm sure the command is correct i tried it on knoppix any one has a solution to repair it???

---

### Post by bingoUV on 2007-12-07
In what way did it not behave correctly? Mout unsuccessful? Any errors? Is the loop module loaded in your kernel? Check with the following command : 
```

sudo /sbin/lsmod | grep loop

```

If the above command does not print anything, load the module by
```

sudo /sbin/modprobe loop

```
and try again.

---

