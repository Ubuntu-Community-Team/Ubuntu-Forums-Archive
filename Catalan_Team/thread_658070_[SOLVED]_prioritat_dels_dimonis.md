---
title: "[SOLVED] prioritat dels dimonis"
date: 2008-01-04
forum: Catalan Team
---

### Post by guillemsola on 2008-01-04
Bon any a tothom

Fa dies que li dono voltes a una qüestió i no se quina seria la manera més "elegant" de resoldre-la.

Estic intentant executar el procés dimoni amule amb una prioritat baixa. El perquè és degut a que l'executo a un mini-ordinador arm que té molt poca potència i intento que el  servidor UPNP ushare tingui la màxima prioritat. (ja que a vegades hi tinc petits talls en la visió d'arxius multimèdia)

L'ushare l'executo amb un nice -20 des de el crontab cada vegada que engego la màquina. Però l'amule que s'executa com a servei a l'inici no se com dir-li que tingui un nice més alt.

He pensat a crear un script que detecti el nº de procés de l'amule per posar-ho a l'ordre renice i que això s'executi cada vegada que engego la màquina.

És aquesta una bona manera de donar un valor nice diferent a un servei que s'engega a l'inici?

A l'espera dels vostres consells....

---

### Post by jordilin on 2008-01-04
Fes servir la comana "start-stop-daemon" on hi ha la opcio -N o --nicelevel on li pots passar la prioritat. Pots investigar mes fent un cop d'ull a /etc/init.d i mirar els daemons que s'executen en l'ubuntu.
Executa 
man start-stop-daemon per mes info.

---

### Post by CarlesOriol on 2008-01-04
Si
concretament edites /etc/init.d/amule-daemon
i tal com diu en jordi cerques la linia start-stop-daemon (29) i afegeixes el parametre -N amb la prioritat que vulguis.

---

### Post by guillemsola on 2008-01-05
Gràcies per les respostes, ja ho he resolt tal i com m'heu dit. A més ara que veig que puc remenar aquests scripts d'inici ja estic rumiant a veure que més puc fer. XD

Salut!

---

