---
title: "executable file"
date: 2009-05-26
forum: General Help
---

### Post by m_adel on 2009-05-26
hi..

how can i find executable file for certain program such :
executable file for gnochm program

---

### Post by Boondoklife on 2009-05-26
> **m_adel said:**
> hi..

how can i find executable file for certain program such :
executable file for gnochm program

If you know that the name of the file is gnochm then you could try```
which gnochm
```but if the issue is that it is not in your path then you could try```
sudo find / -name gnochm
```

---

### Post by pro003 on 2009-05-26
and by 'executable' you mean what? .exe .run .bin, etc?

you can find [here]("http://debian.oregonstate.edu/debian/pool/main/g/gnochm/gnochm_0.9.11-2_all.deb") a deb package

and for CHM file I recommend you xchm

```
sudo aptitude install xchm
```

---

### Post by m_adel on 2009-05-26
thnx

---

### Post by pro003 on 2009-05-26
> **m_adel said:**
> thnx

ur welcome man ;)

---

