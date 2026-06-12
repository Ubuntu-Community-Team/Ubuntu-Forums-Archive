---
title: "Com executar i instal·lar un fitxer amb extensió .bin"
date: 2008-02-25
forum: Catalan Team
---

### Post by rogespierre on 2008-02-25
sí, està en altres posts però m'estic fent un merder

tinc .bin a l'escriptori, com l'instalo? sembla que m'hi acosto pero el terminal sempre em diu un error o una mancança

segons llegeixo sembla que també és possible/necessari que al terminal m'idenfitqui, com a usuari, root... també em perdo una mica en això

gràcies!

---

### Post by patrickfromspain on 2008-02-25
primer has de marcar el fitxer com a executable:

chmod +x fitxer.bin

i despres, executar-lo:

com a root: ./fitxer.bin
com a usuari normal: sudo ./fitxer.bin

salut!

---

### Post by papapep on 2008-02-25
Hhhehehe, Patrick, has fet un "bisbe" :-D

Rogespierre, un parell de comentaris sobre el teu fil i el teu post: 

 - Cal que els títols dels posts siguin descriptius del que s'intenta fer, sinó no serveixen per a res per a la gent que ve darrera.

 - Si ja has provat coses i no te n'has sortit hauries d'explicar-les i enganxar el resultat al fòrum, a fi de veure on t'equivoques i no repetir tots el que tu ja has provat. És un manera d'economitzar entre tots el poc temps que tenim. A més, és la millor manera per a que un mateix vegi on l'erra i aprendre.

Si no ho has fet ja, seria interessant que llegissis el fil de capçalera de nom "[IMPORTANT: Si sou nous al fòrum llegiu això abans de continuar]("http://ubuntuforums.org/showthread.php?t=599965")"

---

### Post by rogespierre on 2008-02-25
ok papapep, ho tindré en compte

mmm diria q me n'he en sortit

però m'agradaria saber exactament que es el que he fet
-pq he de marcar un fitxer com a executable? q passa si no ho faig? com el defineix el sistema?
-no ser q vol dir "com a root" o "com usuari normal" només e tecletjat 
sudo ./fitxer.bin i ha funcionat

---

### Post by lluisanunez on 2008-02-25
**sudo**, com a prefix d'una comanda, significa "executa aquesta comanda com superusuari" (= root)
Això et dóna drets de root només per a la comanda en qüestió. És un sistema segur perquè impedeix que te n'oblidis,  o bé que iniciïs sessions senceres com a root, que és quan poden passar desgràcies.
A continuació et demana la teva contrasenya, per assegurar-se que el teu usuari té dret a executar comandes com a root.

Marcar un fitxer com a executable serveix per això, perquè en clicar-lo o cridar-lo s'executi, i no s'obri com a text...

---

### Post by papapep on 2008-02-25
Rogespierre, [aquí]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#head-f7bcf6fd2ecda1cbe16bd70256e94a7043a04cb2") trobaràs una explicació sobre el tema dels permisos dels fitxers que crec que t'anirà bé per a entendre uns quants conceptes de Linux/Unix.

---

### Post by SiscoGarcia on 2008-02-26
papapep, l'enllaç que has comentat és erroni, suposo que vols anar a parar [ací]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%c3%a8rpretComandes#head-f7bcf6fd2ecda1cbe16bd70256e94a7043a04cb2"), no?

---

### Post by papapep on 2008-02-26
Exacte, gràcie Sisco, ja ho he arreglat.

---

### Post by bobobot on 2009-07-07
provo el que dieu pero no m'hen surto per cap canto.

explike-ho per gent molt novella en aixo

gracies

---

### Post by papapep on 2009-07-08
Bobobot:

Posa les ordres exactes que proves i el seu resultat (el que respon el sistema operatiu). Sinó, és tremendament difícil ajudar-te.

Salutacions i benvingut/da al fòrum, i passa't pels fils de capçalera que et poden ajudar a fer-te una idea de com intentem funcionar.

---

