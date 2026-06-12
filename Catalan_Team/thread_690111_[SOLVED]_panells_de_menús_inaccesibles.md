---
title: "[SOLVED] panells de menús inaccesibles"
date: 2008-02-07
forum: Catalan Team
---

### Post by carevolta on 2008-02-07
Hola, avui retocant un panell inferior amb aplicacions la pantalla ha començat a "tremolar", He hagut de cancel·lar tots els processos i reiniciar.

Llavors m'he trobat que tant el panell inferior que havia creat com el superior no existien (en el seu lloc hi ha una franja en blanc) i que ni punxant el botó sobre ells ni sobre cap lloc de l'escriptori aconseguisc accedir a res més que les meues carpetes personals i l'accés directe a l'openoffice i firefox. De fet no puc ni apagar correctament l'ordinador.

Per desgràcia m'ha ocorregut com usuari administrador (hi ha altre usuari que funciona perfectament) i sense accés al terminal, almenys que jo sàpiga.

De les solucions que he llegit la majoria recomanen esborrar i/o reanomenar les carpetes gnome i gnome2. On les localitze? És l'adequat? Se us ocorre altra solució?

Salutacions des de Ca Revolta!!

Gràcies per l'atenció.

---

### Post by SiscoGarcia on 2008-02-07
Hola,

No sé com de malmès tens els quadres, però si pots situar-te a sobre i clicant-hi amb el botó contrari t'apareix l'opció d'afegir un quadre (Quadre nou), fes-ho. Llavors ja hi pots anar afegint aplicacions.

Si no apareix l'opció d'afegir un quadre nou, no sé què pots fer.

---

### Post by carevolta on 2008-02-07
hola, aquest és l'inconvenient principal: que no respon si clique sobre els panells!!

---

### Post by SiscoGarcia on 2008-02-07
Sento no poder ajudar-te més. Pel que fa a la localització de la carpeta gnome, en el meu cas són a```
  /etc/gnome /usr/share/gnome
``` Ho he trobat obrint un terminal i fent ```
whereis gnome
``` Pots fer el mateix amb gnome2. No tinc ni idea de com de segur pot ser això.

Sort!

---

### Post by papapep on 2008-02-07
Home carevoltencs!! com va tot?? A veure si passes pel fil de benvinguda i expliques alguna cosa sobre tu al personal ;-)

Respecte el tema que ens ocupa: No, les carpetes de les que parleu no són les de configuració sota /etc (que fan una altra funció), sinó les d'usuari sota el directori personal del mateix.

O sigui, suposant que l'usuari es diu carevolta, el directori serà a :

**/home/carevolta/.gnome** (atenció al punt!!!!)

---

### Post by carevolta on 2008-02-07
Hola de nou, disculpeu la meua poca solvència, però no trobe enlloc /home/..../.gnome!! a banda d'això cada vegada que minimitze o canvie la grandària d'alguna finestra aquesta comença a "tremolar", així que tot plegat és difícil treballar a gust.

Gràcies per la col·laboració.

---

### Post by papapep on 2008-02-07
No crec que tingui a veure amb la teva poca perícia, crec que algun desastre t'ha passat amb l'entorn gràfic.

Jo el que faria és reinstal·lar el paquet que conté tot el tema aquest.

```
sudo apt-get update
sudo apt-get --reinstall install ubuntu-desktop
```

---

### Post by carevolta on 2008-02-07
Bo, ens anem acostant a la solució! Ara una altra pregunta? Hi ha algun comandament per accedir a terminal si no puc accedir des dels panells de menús perquè han desaparegut? O alguna altra via alternativa? És l'altre inconvenient que tinc des del principi, que només sé (com a novato que sóc) arribar a les apliacions des dels menús o els accesos directes i a l'escriptori tan sols tinc el firefox i l'openoffice.

---

### Post by lluisanunez on 2008-02-07
> **carevolta said:**
> 
Per desgràcia m'ha ocorregut com usuari administrador (hi ha altre usuari que funciona perfectament) i sense accés al terminal, almenys que jo sàpiga.


No necessites entrar al Gnome com usuari administrador,  i no és recomanable. Si ho vas fer així, les carpetes que has d'esborrar són a 
/root/.gnome

---

### Post by papapep on 2008-02-07
Ostres, Carevolta, tal i com t'ha dit la Lluïsa, entra com a root a l'entorn gràfic és pecat mortal de necessitat!!! Et pot portar uns maldecaps de tres parells de nassos...
Per això es creen els usuaris "normals", de veritat.

---

### Post by carevolta on 2008-02-07
Bo, he anat provant i després de reinstal·lar (suposadament) el paquet, el resultat és que tot continua igual, només que quan intente accedir m'apareix una advertència dient-me que s'ignorarà el fitxer $HOME/.dmrc.
Continuarà...

---

### Post by papapep on 2008-02-07
Però això amb quin usuari?

---

### Post by carevolta on 2008-02-07
Potser ja m'estic embolicant del tot. A vore: si no m'equivique he entrat en una sessió de terminal des de la pantalla d'inici i com a administrador he provat els comandaments que m'has dit (l'altre usuari continua igual, sense problemes i preferisc que continue així per si de cas).
I des d'allí he actualitzat els paquets, o això crec. La proposta de esborrar/reanomenar la carpeta root/.gnome tampoc em dóna resultats.

---

### Post by carevolta on 2008-02-07
Ara he provat amb una sessió GNOME a prova de fallades i tot torna al seu lloc, ja tinc panells!!!! Però, clar des d'ací hauria de solucionar el desgavell i intentar recuperar la configuració anterior i és el que ara no sé com fer.

---

### Post by papapep on 2008-02-07
Jo no vull ser insistent...però és que és igual que no et funcioni l'entorn gràfic com a usuari root, no l'has de fer servir per a res. Qualsevol cosa que vulguis fer amb privilegis d'administrador des de l'usuari normal pots fer-ho sense el més mínim problema.

---

### Post by carevolta on 2008-02-07
Ei, no és insistència teua, és cabotoneria meua. Crec que ja està tot resolt: he fet les modificacions des de GNOME a prova de fallades i ara tot torna al seu lloc.
Felicitats pels 1.000 pots i per la paciència.

---

### Post by papapep on 2008-02-07
Doncs ara et toca explicar com ho has arreglat per si algú altre s'hi troba que pugui aprofitar la teva experiència :-D (ah! i marca el fil com a resolt!)

---

### Post by carevolta on 2008-02-08
Bon dia, per descomptat tenia intenció d'acabar de fer tots els passos. Tan sols que no sé ben bé si ho tinc resolt correctament. He canviat la configuració des d'una sessió de GNOME com a terminal, però encara em diu que s'ignorarà el fitxer 
$HOME/.dmrc. Així que crec em caldrà tornar enrere i estudiar tots els passos abans de concloure definitivament el fil.

---

