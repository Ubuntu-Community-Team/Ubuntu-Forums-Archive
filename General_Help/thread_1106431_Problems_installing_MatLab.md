---
title: "Problems installing MatLab"
date: 2009-03-25
forum: General Help
---

### Post by KrisRK on 2009-03-25
Hi everyone,

I have downloaded (legally;)) the ISO-file for MatLab R2008b. I have mounted the file with the commands:

```
mount -o loop -t iso9660 /home/kriskla/Program/R2008b_Unix.ISO /media/iso/
```

This works just fine. Then I try to install:

```
/media/iso/install
```

I have also tryed to run the file by clicking on it. Nothing happens. Nada. Not even an error :( And I have looked all over the net and through forums for an answer. Have also tried different codes for installing but alas...

Can someone help me?

Much appreciate it!

---

### Post by Wayne_V on 2009-03-25
Try:

# cd /media/iso
# sh -x ./install

Might tell you more.

---

### Post by KrisRK on 2009-03-25
Thanks mate, but it only says "illegal option -."...

---

### Post by Wayne_V on 2009-03-26
You have spaces in there, right?

# sh   -x     ./install

---

### Post by Nepherte on 2009-03-26
/media/iso/install works for me. Did you run it in the terminal?

---

### Post by KrisRK on 2009-03-30
Sorry, was away in the weekend.

> **Nepherte said:**
> /media/iso/install works for me. Did you run it in the terminal?

Yes I did. It acts as there is nothing there, but I can find the path and file on the computer... :(

And I have spaces ;) 

Maybe the iso-file is corrupt. Thanks a lot.

---

