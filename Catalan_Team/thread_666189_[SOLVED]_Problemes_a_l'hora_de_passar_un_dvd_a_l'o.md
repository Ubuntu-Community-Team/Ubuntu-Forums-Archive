---
title: "[SOLVED] Problemes a l'hora de passar un dvd a l'ordinador"
date: 2008-01-13
forum: Catalan Team
---

### Post by lo gambusí on 2008-01-13
Salut!

Vull fer una còpia de seguretat d'un dvd que tinc a casa. Lo tema està en que ho he fet en lo thoggen, en lo dvd::rip i en lo k9copy, i en los tres casos me'l detecta però no me dixa copiar-lo, me dóna error de lectura. No sé si pot ser cosa de falta de codecs (que no ho crec, perquè altres dvd's sí me'ls llig) o de protecció que deu tenir este dvd en concret (perquè he provat en un altre dvd i sí me'l passa). He anat provant en diferents dvd's i mentre alguns me'ls llig i se'm penja just al començar el ripeig, d'altres directament ni me'ls llig i me diu que potser (?!) falta el libdvdcss2. L'he provat d'instal·lar des de la consola i me diu>           
El paquet libdvdcss2 no té versió disponible, però un altre paquet
en fa referència. Això normalment vol dir que el paquet falta,
s'ha tornat obsolet o només és disponible des d'una altra font.
E: El paquet libdvdcss2 no té candidat d'instal·lació

Provant amb el k9copy me comença lo ripeig també, però de repent me dóna error, se'm tanca la finestra i diu que l'aplicació ha fallat i ha causat el senyal 11 (SIGSEGV). Copio la traça enrera:> (no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1234204992 (LWP 7350)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x080ab330 in ?? ()
#7  0xbf7d8608 in ?? ()
#8  0x0813ef38 in ?? ()
#9  0x088509c0 in ?? ()
#10 0x0884f038 in ?? ()
#11 0xbf7d86a8 in ?? ()
#12 0x080a7680 in ?? ()
#13 0x088509c0 in ?? ()
#14 0x0885003c in ?? ()
#15 0xbf7d8618 in ?? ()
#16 0x080aca4b in ?? ()
#17 0x00000001 in ?? ()
#18 0x088509c0 in ?? ()
#19 0xbf7d8658 in ?? ()
#20 0x080ad637 in ?? ()
#21 0x088509c0 in ?? ()
#22 0x0885089c in ?? ()
#23 0xbf7d8658 in ?? ()
#24 0x080adac6 in ?? ()
#25 0x00000021 in ?? ()
#26 0xb69a78ac in __pthread_mutex_unlock_usercnt ()
   from /lib/tls/i686/cmov/libpthread.so.0
Backtrace stopped: previous frame inner to this frame (corrupt stack?)


La veritat és que ja no sé per on pegar-li... Alguna idea? Moltes gràcies.

---

### Post by lo gambusí on 2008-01-13
Res, pensava tenir instal·lat lo paquet libdvdcss2 i no'l tenia. L'he descarregat en .deb i l'he instal·lat, i ara ja funciona.

Gràcies igualment!

---

### Post by kukat on 2008-01-13
Ja que has obert aquest tema, una pregunteta ràpida

Quan vaig passar un dvd amb el thoggen (Un pont cap a Therabitia) hem va anar de meravella, però durant tot el film surt una linia verda... A que pot ser degut? Al anticopy de la peli?

---

### Post by the8thstar on 2008-01-13
I've seen this happen when the film resolution exceeds the PAL sttings.

---

