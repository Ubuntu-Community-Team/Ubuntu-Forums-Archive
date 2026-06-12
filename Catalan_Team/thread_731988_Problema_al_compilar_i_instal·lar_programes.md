---
title: "Problema al compilar i instal·lar programes"
date: 2008-03-22
forum: Catalan Team
---

### Post by Satboy on 2008-03-22
Hola,
 He Intentat d'instal·lar el joc Burgerspace tal i com indica en **Cubells** al Planeta Ubuntu, però m'ha passat el què em succeeix molt sovint quan intento instal·lar un joc.Quan arribo a la ratlla on diu:

**./configure && make && sudo make install**

Em succeeix això:

administrador@administrador-desktop:~/burgerspace-1.6.1$ ./configure && make && sudo make install
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output... configure: **error: C++ compiler cannot create executables**

És normal que em passi això gairebé sempre??

 Moltes gràcies.

 Siau!;)

---

### Post by lluisanunez on 2008-03-22
Diu que et falten les eines per compilar
```
apt-get install build-essential
```

---

### Post by Satboy on 2008-03-22
> **lluisanunez said:**
> Diu que et falten les eines per compilar
```
apt-get install build-essential
```

 Hola,
 Moltes gràcies Lluïsa, això ara va de conya!! :wink::wink:

 P.D.És normal que em faltessin les eines per compilar? No les porta, ja per defecte, l'Ubuntu? 

 Siau! :wink:

---

### Post by CarlesOriol on 2008-03-23
> **Satboy said:**
>  P.D.És normal que em faltessin les eines per compilar? No les porta, ja per defecte, l'Ubuntu? 

1. Tots els paquets "oficials" no estan al cd. A la versió dvd n'hi ha uns més però no tots.

2. Per defecte és una traducció malevola de default cal dir predeterminadament. (excepte si consideres que és un defecte que no les dugui :-D )

---

