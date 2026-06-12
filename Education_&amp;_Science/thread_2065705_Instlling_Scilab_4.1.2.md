---
title: "Instlling Scilab 4.1.2"
date: 2012-10-02
forum: Education &amp; Science
---

### Post by Mruvek on 2012-10-02
i'm new Ubuntu user and I want to install scilab 4.1.2.   I downloaded scilab-4.1.2.bin.linux-i686, because 
```
sudo apt-get install scilab
```
will install the newest version (5.3 or 5.4) and i want 4.1.2, but i don't know what to do with 4.1.2.bin.linux-i686.tar.gz

---

### Post by raja.genupula on 2012-10-02
you can install a tar source like this 

```
tar -xvf scilab-4.1.2.bin.linux-i686.tar.gz 	
cd scilab-4.1.2
./configure
make 
sudo make install

```

---

### Post by Mruvek on 2012-10-02
Ok, thanks. That's exactly what I want ; )

---

### Post by raja.genupula on 2012-10-03
glad news man , now please mark your thread as solve from thread tools ,

---

