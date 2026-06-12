---
title: "Darwinia on Edgy"
date: 2006-10-19
forum: Gaming &amp; Leisure
---

### Post by Bagnaj97 on 2006-10-19
On Ubuntu Edgy Darwinia failed for me with the error
```
/usr/local/games/darwinia/lib/darwinia.bin.x86: /usr/local/games/darwinia/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

I fixed it by removing libgcc_s.so.1 from the darwinia lib directory. If you have the same problem you can fix it by typing:

```
sudo rm /usr/local/games/darwinia/lib/libgcc_s.so.1
```

Assuming you have darwinia installed in /usr/local/games

---

### Post by maxol on 2006-11-02
Many thanks for this!

---

### Post by szundi on 2006-11-07
Thanks!

---

### Post by PriceChild on 2008-07-04
Still works on hardy, woo :)

---

