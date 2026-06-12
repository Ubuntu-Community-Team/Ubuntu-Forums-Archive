---
title: "[SOLVED] diversos idiomes en document openoffice"
date: 2008-10-04
forum: Catalan Team
---

### Post by guillemsola on 2008-10-04
Hola,

m'han passat un document fet amb word que he de completar amb l'openoffice. Aquest document està en català, però la correcció ortogràfica la fa en castella :(

Si vaig a documment-opcions-llengues tinc el català com a llengua per al document. Així doncs aquest document emmagatzema en algun altre lloc que té parts en castellà i parts en català, ja que si faig la correcció ortogràfica i per cada paraula torno a seleccionar el diccionari en català s'ho aprèn.

Algú sap com fer perquè un document sigui tot en el català?

Suposo que es deu poder tenir més d'un idioma en un document però al manual del openoffice writer no n'he trobat cap referència a aquest tema.

gràcies

---

### Post by lpargemi on 2008-10-04
Hola

Quan dius 

> Si vaig a documment-opcions-llengues

et refereixes a 

```
 Eines>Opcions>Configuració de la Llengua>Llengües ?
```

Amb les proves que jo he fet (català, castellà i francès) el corrector sempre m'entra amb la llengua que he triat aquí amb l'opció com a Occidental i marco com a "Només per al document actual"

No sé si es el mateix que fas tu.

Salut

Lluís

---

### Post by lluisanunez on 2008-10-04
Has de seleccionar el text (tot el text que ha d'anar en català), aleshores Format > Caràcter > Llengua
I el mateix per als fragments que hagin d'anar en altres idiomes

---

### Post by orestesmas on 2008-10-04
En OpenOffice la qüestió de l'idioma del document està fortament relacionada amb els estils de paràgraf.

Per tenir un document amb diverses llengües barrejades (per exemple, si cites fragments en altres llengües) cal definir un estil per cada llengua  i associar-los als paràgrafs corresponents.

Si només tens una llengua cal que editis l'estil per omissió i li assignis el català, i després assignis aquest estil a tots els paràgrafs del document. Si tens altres estils (per les capçaleres, etc) assegura't que derivin del teu estil per omissió.

Això obliga a treballar amb estils. Molta gent ho troba un pal, perquè li és més còmode anar canviant l'estil manualment en el moment que ho necessita, però això no és un ús adient d'un processador de textos.

---

### Post by guillemsola on 2008-10-05
gràcies per les respostes, ja reconquerit el document :)

> Has de seleccionar el text (tot el text que ha d'anar en català), aleshores Format > Caràcter > Llengua
I el mateix per als fragments que hagin d'anar en altres idiomes

En la meva versió de openoffice està a la mateixa pestanya on tries el tipus de lletra, potser per això no ho veia. Jo ho buscava més aviat a paràgraf o document.

Salutacions

---

