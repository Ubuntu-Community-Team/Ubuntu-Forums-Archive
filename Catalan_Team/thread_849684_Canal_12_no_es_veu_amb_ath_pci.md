---
title: "Canal 12 no es veu amb ath_pci"
date: 2008-07-04
forum: Catalan Team
---

### Post by anigwei on 2008-07-04
Hola,

A l'eeepc faig servir una versió modificada del nucli ([http://www.array.org/ubuntu/index.html](http://www.array.org/ubuntu/index.html)), se suposa que adaptada per aquesta màquina.

El problema és que no es connecta a la meva wireless perque està al Canal 12. Fent un iwlist scan, les llista totes excepte la meva del canal 12.

Quan configurem una tarja wifi se li ha de dir el pais on estem perquè sàpiga quins canals pot utilitzar, pot tractar-se d'això? Com es configura?

Ara per ara funciono amb ndiswrapper.


Salutacions i gracies!!

---

### Post by CarlesOriol on 2008-07-05
Es estrany... precisament avui comentàvem que la wifi del eee és una de les més potents i versàtils que he vist mai.

Pot ser que la teva màquina tingui algun problema? He vist en un altre fil que deies que el ubuntu-eee et va lent. A mi em corre moltíssim. No entenc que et pot passar.

Has re-compilat el nucli per que funcioni el wifi? el ubuntu-eee ja ho du tot fet.

---

### Post by anigwei on 2008-07-06
He estat molt temps amb Gutsy (Vaig instal·lar eeeXubuntu i després migrar a Ubuntu) i ha estat anant molt temps com una seda, wireless inclosa.

Però vaig passar-me de llest i vaig provar la Ubuntu-eee Hardy, i han començat els problemes a dojo:

1) S'escalfa més (amb gutsy no pujava de 53-55, ara estant IDLE està als 56-58).
2) Més lent de reflexes, fins i tot aturant Compiz...
3) Mirant una peli cada X segons fa un salt com si faltés potència de CPU (cosa que amb Gutsy no passava ni escalant la velocitat a 300Mhz).
4) Els OSD no furul·len (ni aplicant les instruccions adients, el paquet .DEB, etc)

Amb consol que tot milloraria, vaig instal·lar el nucli que algú s'ha dedicat a optimitzar per l'eee (El d'array.org). Amb aquest nucli:

1) Arranca més ràpid
2) Continuen els reflexes lents
3) No veu xarxes sense fils situades al Canal 12 (amb Ndiswrapper sí).



En fi, actualment estic provant la eeeUbuntu ([http://www.eeebuntu.org/](http://www.eeebuntu.org/)), a veure quins resultats dóna i en última instància passaré altre cop a Gutsy (la Xandros, tal com dieu, MAI!! ;).

Salut!

Ara

---

