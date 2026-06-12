---
title: "Cannot get to ubuntu."
date: 2009-02-25
forum: General Help
---

### Post by Pakiepiphany on 2009-02-25
When i load up my computer and it gets to the boot screen, it gives me an option to choose between loading windows or ubuntu.
The problem is that my keyboard sensor doesn't turn on until i load windows for some reason so it wont let me go down to ubuntu and keeps defaulting to windows.
Im using the microsoft wireless comfort keyboard 1.0a, model 1045.
And no I don't have a wired keyboard available, any advice?

Many thanks!

---

### Post by blueridgedog on 2009-02-25
I or another user could potentially talk you through mounting your Ubuntu install via a live CD and editing your boot options to boot Ubuntu first, but then you would have the same problem as before, but it would apply to windows.  Without a keyboard that the BIOS recognizes you will not be able to make multiple choices.

---

### Post by Pakiepiphany on 2009-02-26
Thanks but i figured it out lol, long and dumbb story but i got it to work.
;]

Edit: though i do have a new problem, when im on ubuntu i can't figure out how to access all my other files i can only acess the files on the partition, is there anyway to acess my documents that i have on the windows partition?

---

### Post by blueridgedog on 2009-02-26
Can you post the output of

```
sudo fdisk -l
```

---

