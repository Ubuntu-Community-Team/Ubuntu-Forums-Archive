---
title: "compiz blacklisted card"
date: 2010-04-29
forum: Desktop Environments
---

### Post by andrea000 on 2010-04-29
I used this command sudo gedit /usr/bin/compiz to unblacklist
my video card in ubuntu 9.10 now that i upgraded to 10.04
this command doesn't work can someone tell me a way to do it.

---

### Post by S.A.A on 2010-05-13
```
sudo apt-get install ghex
sudo ghex2 /usr/bin/compiz
```

:)

---

### Post by andrea000 on 2010-05-14
> **S.A.A said:**
> ```
sudo apt-get install ghex
sudo ghex2 /usr/bin/compiz
```

:)

Thank you S.A.A

ok all i get are some numbers when i open that file in ghex2.
what am i looking for i looked for my card (8086:2982) but
found nothing what do i edit to unblacklist the card?

---

### Post by S.A.A on 2010-05-18
Ok.. sorry for being late:

Just go ahead to the end of the file and start looking for "8086:2982" on the right (It will take some time till you find it) and then replace the number 2 or 8 or any other number into another one.. like 8086:2983 then save..

---

