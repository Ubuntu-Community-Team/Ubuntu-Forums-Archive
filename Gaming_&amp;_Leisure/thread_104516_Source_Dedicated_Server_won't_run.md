---
title: "Source Dedicated Server won't run"
date: 2005-12-16
forum: Gaming &amp; Leisure
---

### Post by netelemental on 2005-12-16
Hey, whenever I try to run the hldsupdatetool.bin no matter what I do it says ```
-bash: ./hldsupdatetool.bin: No such file or directory
```
I have tried posting on the steam forums but they couldn't figure it out. I am using an AMD64 X2 processor too which might have an effect. Any help?

---

### Post by netelemental on 2005-12-16
Ah and you might want to know that I DID chmod +x it and also tried chmodding it to 777.

---

### Post by mindflayer.net on 2006-03-03
I am facing the same issue. I think it's missing 64-bit libs on Ubuntu 64.

---

### Post by netelemental on 2006-05-02
Do you think the newer versions of ubuntu will fix this? Or should I switch to a different OS?(bsd or another linux distro)

---

### Post by im_an_elf on 2006-10-17
](*,)   I did a great deal of this because the error message is not very descriptive.

```
-bash: ./hldsupdatetool.bin: No such file or directory
```

I tried this:

```
sudo apt-get install ia32-libs
```

I am currently running Dapper Drake on a amd64 X86_64 machine.

That is a 64 bit machine.

Oh and it worked.

---

### Post by Shmio on 2008-01-29
worked like a charm...thanks guys

---

