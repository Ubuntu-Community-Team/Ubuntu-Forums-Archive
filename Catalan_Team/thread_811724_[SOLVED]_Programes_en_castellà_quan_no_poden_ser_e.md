---
title: "[SOLVED] Programes en castellà quan no poden ser en català"
date: 2008-05-29
forum: Catalan Team
---

### Post by rajoar on 2008-05-29
Hi han programes que s'instal·len segons l'idioma que té el sistema per defecte, però com per desgràcia hi han programes que no estan traduïts al català, llavors s'nstal·len en anglès, encara que disposin del castellà. ¿En aquests casos hi ha alguna forma de dir-los que agafin el castellà?...

---

### Post by RainCT on 2008-05-29
No s'insta&#320;len en cap llengua concreta, sinó que s'insta&#320;len totes les llengües amb el programa (excepte amb els paquets del dipòsit main, en aquest cas els paquets d'idioma sí que estan separats), i és la teva configuració la que determina en quina llengua surt.

Però bé, respecte al que preguntes, executant els programes que vulguis des de la terminal, de la següent manera, te'ls hauria d'obrir en castellà: "LANG=es_ES.UTF-8 <nom_del_programa>". Suposo que pots editar els menús (amb l'Editor de menús Alacarte) per posar-hi aquesta ordre.

---

### Post by CarlesOriol on 2008-05-29
La resposta d'en Sigfried és molt interessant.

Rajoar: er curiositat. Amb quin programa et trobes en aquesta situació?

---

### Post by rajoar on 2008-05-29
Efectivament RainCT, és tal com tu dius..., no s'instal·len en cap idioma sinò que habiliten l'idioma segons la teva configuració...
El que jo voldria és que, per defecte, si un programa no està en català agafés el castella i en canvi agafa l'anglès...
Bé, de totes maneres, i també tal com tu dius, utilitzant "LANG=es_ES.UTF-8 <nom_del_programa> en el terminal funciona bé...
El que no funciona es posant aquesta mateixa ordre a l'editor de menús..
No sé quina ordre hauria de posar-hi perquè funcionés...

---

### Post by RainCT on 2008-05-29
> **rajoar said:**
> El que no funciona es posant aquesta mateixa ordre a l'editor de menús.. No sé quina ordre hauria de posar-hi perquè funcionés...

M'ho temia... Doncs ara mateix l'únic que se m'acudeix és fer a la terminal "sudo touch /usr/local/bin/<nom programa>; sudo chmod +x /usr/local/bin/<nom programa>; sudo gedit /usr/local/bin/<nom programa>" (això per a cadascun dels programes que vulguis, canviant <nom programa> pel nom corresponent) i quan t'obri l'editor de text escriure-hi el que t'he dit de "LANG=es_ES.UTF-8 <nom programa>". Llavors, pots posar "/usr/local/bin <nom programa>" a l'entrada del menú i hauria de funcionar.

(Si no vols posar-los a /usr/local/bin també pots crear els fitxers en un directori qualsevol del teu home).

---

### Post by rajoar on 2008-05-29
Je...je...Carles,
No, no tinc cap problema en dir-ho... és Nero Linux..., sí, sí ja sé que em diràs ¿com és que fas servir aquest programa?, però és que, de moment, no he trovat cap més alternativa per poder gravar Blue Ray... Espero poder-ne trovar alguna aviat i no haver d'utilitzar el Nero...
Bé, ara vaig a provar el que m'ha indicat RainCT...

---

### Post by rajoar on 2008-05-30
RainCT,
OK! la solució.

---

### Post by CarlesOriol on 2008-05-31
> **rajoar said:**
> de moment, no he trovat cap més alternativa per poder gravar Blue Ray... 

Vaja, no en tenia ni idea.

Espero que sigui cosa de poc temps que ja puguis escriure'ls en programari lliure i en català.

---

