---
title: "acerhk que no es carrega"
date: 2008-04-23
forum: Catalan Team
---

### Post by climent on 2008-04-23
Tinc un portàtil Acer que necessita les acerkeys per activar o desactivar el botó de la wireless. Ja ho tenia correcte, però he fet una instal·lació neta amb el Hardy i, en intentar descomprimir (i instal·lar) un arxiu que es diu acerhk.ko al final de la llista em diu "[acerhk.ko] error", com si no es pogués crear. Faig sudo make, make install i demés i no hi ha manera. He googlejat però no trobo solucions. Algú pot aportar una mica de llum?

---

### Post by papapep on 2008-04-23
Enganxa'ns tant la ordre completa que li dones com el missatge que et retorna.

---

### Post by climent on 2008-04-23
Aquí ho teniu:
climent@climent-portatil:~/Escriptori/acerhk-0.5.35$ sudo make && install
[sudo] password for climent: 
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
En el fitxer inclòs dès de /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 dès de /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 dès de scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function 'usage':
scripts/basic/fixdep.c:131: avís: implicit declaration of function 'fprintf'
scripts/basic/fixdep.c:131: avís: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:131: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: avís: implicit declaration of function 'exit'
scripts/basic/fixdep.c:132: avís: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c: In function 'print_cmdline':
scripts/basic/fixdep.c:140: avís: implicit declaration of function 'printf'
scripts/basic/fixdep.c:140: avís: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c: En el nivell principal:
scripts/basic/fixdep.c:143: error: 'NULL' undeclared here (not in a function)
scripts/basic/fixdep.c: In function 'grow_config':
scripts/basic/fixdep.c:156: avís: implicit declaration of function 'realloc'
scripts/basic/fixdep.c:156: avís: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: avís: implicit declaration of function 'perror'
scripts/basic/fixdep.c:158: avís: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c: In function 'is_defined_config':
scripts/basic/fixdep.c:174: avís: implicit declaration of function 'memcmp'
scripts/basic/fixdep.c: In function 'define_config':
scripts/basic/fixdep.c:187: avís: implicit declaration of function 'memcpy'
scripts/basic/fixdep.c:187: avís: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c: In function 'use_config':
scripts/basic/fixdep.c:206: error: 'PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:214: avís: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c:220: avís: implicit declaration of function 'tolower'
scripts/basic/fixdep.c:222: avís: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c:206: avís: unused variable 's'
scripts/basic/fixdep.c: En el nivell principal:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or '...' before 'size_t'
scripts/basic/fixdep.c: In function 'parse_config_file':
scripts/basic/fixdep.c:227: error: 'len' undeclared (first use in this function)
scripts/basic/fixdep.c:233: avís: implicit declaration of function 'ntohl'
scripts/basic/fixdep.c:244: avís: implicit declaration of function 'isalnum'
scripts/basic/fixdep.c: In function 'strrcmp':
scripts/basic/fixdep.c:261: avís: implicit declaration of function 'strlen'
scripts/basic/fixdep.c:261: avís: incompatible implicit declaration of built-in function 'strlen'
scripts/basic/fixdep.c: In function 'do_config_file':
scripts/basic/fixdep.c:272: error: storage size of 'st' isn't known
scripts/basic/fixdep.c:276: avís: implicit declaration of function 'open'
scripts/basic/fixdep.c:276: error: 'O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:278: avís: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:278: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:280: avís: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:282: avís: implicit declaration of function 'fstat'
scripts/basic/fixdep.c:284: avís: implicit declaration of function 'close'
scripts/basic/fixdep.c:287: avís: implicit declaration of function 'mmap'
scripts/basic/fixdep.c:287: error: 'PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: 'MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:287: avís: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function 'parse_config_file'
scripts/basic/fixdep.c:296: avís: implicit declaration of function 'munmap'
scripts/basic/fixdep.c:272: avís: unused variable 'st'
scripts/basic/fixdep.c: En el nivell principal:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or '...' before 'size_t'
scripts/basic/fixdep.c: In function 'parse_dep_file':
scripts/basic/fixdep.c:304: error: 'len' undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: 'PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:308: avís: implicit declaration of function 'strchr'
scripts/basic/fixdep.c:308: avís: incompatible implicit declaration of built-in function 'strchr'
scripts/basic/fixdep.c:310: avís: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:310: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:311: avís: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:313: avís: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c:314: avís: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c:306: avís: unused variable 's'
scripts/basic/fixdep.c: In function 'print_deps':
scripts/basic/fixdep.c:343: error: storage size of 'st' isn't known
scripts/basic/fixdep.c:347: error: 'O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:349: avís: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:349: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:351: avís: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:355: avís: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:359: error: 'PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: 'MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:359: avís: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function 'parse_dep_file'
scripts/basic/fixdep.c:343: avís: unused variable 'st'
scripts/basic/fixdep.c: In function 'traps':
scripts/basic/fixdep.c:378: avís: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:378: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:380: avís: incompatible implicit declaration of built-in function 'exit'
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [acerhk.ko] Error 2

---

### Post by climent on 2008-04-26
uf, quin llistat que m'ha sortit

---

### Post by pespin on 2008-04-26
Has provat a fer un ./configure abans?

---

### Post by climent on 2008-04-29
Sí, ho he provat, i res. De tota manera, he decidit passar de l'adaptador propi del portàtil i provar-ne un USB. Resulta que és un D-Link i, tot i que he tingut algun problema, sembla que l'he pogut instal·lar i fer-lo córrer.
Ara que això, ja és una altra història (o sigui, un altre fil)

---

