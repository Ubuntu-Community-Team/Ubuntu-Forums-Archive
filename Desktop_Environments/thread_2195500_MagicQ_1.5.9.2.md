---
title: "MagicQ 1.5.9.2"
date: 2013-12-24
forum: Desktop Environments
---

### Post by Frankiewizard on 2013-12-24
I have been trying to launch <Magicq> in the terminal ! and I get this 
[HTML]frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ ./Desktop/magicq_linux_v1.5.9.2/magicq
./Desktop/magicq_linux_v1.5.9.2/magicq: error while loading shared libraries: libQt5PrintSupport.so.5: cannot open shared object file: No such file or directory
frankiewizard@frankiewizard-Presario-CQ62-Notebook-PC:~$ 
[/HTML]

What am I missing here. Cheers.........................................................

Using UbuntU 13.10 (64 bits)

---

### Post by ajgreeny on 2013-12-24
You need to install **libQt5PrintSupport****5** which should give you that library file

---

### Post by Frankiewizard on 2013-12-26
Cheers >>>> it is all ready installed. 
I have decided to do a double boot using <12.04 LTS 32 bits> with ChamSys 1.5.8.6 & it seem to work.

---

### Post by Frankiewizard on 2013-12-26
Cheers >>>> it is all ready installed. 
I have decided to do a double boot using <12.04 LTS 32 bits> with ChamSys 1.5.8.6 & it seem to work.

---

### Post by Frankiewizard on 2013-12-26
Have found out that the only magicq which functions on UbuntU 13.10 is >> v1_5_8_6. Now isent that strange !

---

