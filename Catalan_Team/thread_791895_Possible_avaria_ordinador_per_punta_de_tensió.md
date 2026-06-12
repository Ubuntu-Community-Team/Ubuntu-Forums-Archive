---
title: "Possible avaria ordinador per punta de tensió"
date: 2008-05-12
forum: Catalan Team
---

### Post by LitusMayol on 2008-05-12
Bones... 
No voldria seguir *taladrant* amb el tema però... 


N'hi ha que ja ho saben, pels que no: l'altre dia durant la tempesta vaig tenir un pic de tensió que féu que el meu ordinador s'apagués i m'està creant una quantitat de problemes importants(mort del ventilador, mort del firefox, mort del disc dur extern...).

Després de pensar que només havia afectat al disc dur extern i que havia tornat boig al **firefox** m'adono que va més enllà. 


Tinc tres particions amb sistemes operatius:en una hi tinc l'Innombrable, en la segona hi tinc Ubuntu i en la tercera hi tinc UbuntuStudio. 

[LIST]
[*]**L'Innombrable**es reinicia sol. Aleatòriament. De cop s'apaga i reinicia l'ordinador sense previ avís.
[*]**L'Ubuntu**ha mort. Només em deixa obrir-se en una resolució de 800x600 i va fatal. Fatal és la millor descripció. No va re, va lent, el Firefox es tanca sol... En fi. Està mort.
[*]**L'UbuntuStudio**és l'únic que sembla haver sobreviscut a la tragèdia (tragèdia per l'Ubuntu no per l'Innombrable xD).
[/LIST]


Algú se li acut perquè l'UbuntuStudio segueix funcionant sense cap problema (per sort!) i perquè els altres moren continuament?

 Jo havia pensat que potser a part del ventilador també havia petat la gràfica... però m'estranya que l'UbuntuStudio funcioni correctament. De totes maneres algú sap com comprobar que la gràfica funciona per terminal? (preferiria assegurar-me'n)



Doncs re, merci per tot. I perdoneu la meva insistència...

---

### Post by PellRoja on 2008-05-12
Jo primer de tot buscaria la manera de fer copies de seguretat dels arxius importants. Un cop fet això ja miraria d' arreglar. Per que poster tens el disc dur esconyat, o algun altre maquinari.

---

### Post by LitusMayol on 2008-05-12
> **PellRoja said:**
> Jo primer de tot buscaria la manera de fer copies de seguretat dels arxius importants. Un cop fet això ja miraria d' arreglar. Per que poster tens el disc dur esconyat, o algun altre maquinari.

El disc dur de l'ordinador sembla funcionar bé: hi ha tots els arxius on haurien de ser-hi.

Al disc dur extern no hi puc accedir.

---

### Post by CarlesOriol on 2008-05-12
Engega amb la live i fes un memtest.

---

### Post by LitusMayol on 2008-05-13
> **CarlesOriol said:**
> Engega amb la live i fes un memtest.

Bones,

l'he deixat tota la nit fent un *memtest* però... es que no en sé llegir els resultats, ni sé quan acaba... portava més de 10 hores. I ell deia que estava pel test 6 i resulta que si mirava els errors en ja n'havia trobal al 6, el 7 i el 8.

Hi ha alguna manera d'enviar els errors o saber què volen dir? N'ha trobat uns 3000...


Merci

---

### Post by papapep on 2008-05-13
És que tampoc crec que els sapiguem entendre, Litus...són especialment críptics :-)
La qüestió és que tens errors a la RAM, i pel que dius una passada d'errors. Per tant, una cosa segura és que tens difunta, o en via directa de defunció, la memòria RAM :-( Ara falta saber si tots els xips (si en tens més d'un) o només un. Hauries de  mirar quants en tens a la placa, i si en tens més d'un deixar-ne només un posat i tornar a fer-li el memtest.

---

### Post by LitusMayol on 2008-05-14
> **papapep said:**
> És que tampoc crec que els sapiguem entendre, Litus...són especialment críptics :-)
La qüestió és que tens errors a la RAM, i pel que dius una passada d'errors. Per tant, una cosa segura és que tens difunta, o en via directa de defunció, la memòria RAM :-( Ara falta saber si tots els xips (si en tens més d'un) o només un. Hauries de  mirar quants en tens a la placa, i si en tens més d'un deixar-ne només un posat i tornar a fer-li el memtest.

Bones, només en tinc un: ooooooooooooooh!... Però avui un amic em deixarà la seva per probar-ho, simplement si funciona bé l'ordinador serà que tinc 512Mb de RAM difunts.

---

### Post by Frealof on 2008-05-19
Iep!

Jo tinc un problema semblant i a part de molest comença a ser molt preocupant...

Com ha suggerit en Carles, he anat fent memtests a tots els xips de ram que tinc (3), he provat de canviar-los de slot i tots els xips em segueixen donant errors (depenent de l'Slot ho fa en un test o en un altre).

Això em porta a pensar si no es la placa la que realment tingui el problema... què en penseu?

Salut!

---

### Post by CarlesOriol on 2008-05-19
> **Frealof said:**
> 
Això em porta a pensar si no es la placa la que realment tingui el problema... què en penseu?


O tot està cascat o és la placa com tu dius. Tot i que és bastant més habitual del que sembla que sigui la memòria.

Aquest tipus d'avaries de memòria son molt xungues ja que et va petant l'ordinador sense cap criteri clar. Quan l'error es lleu dona la sensació que l'ordinador no aguanta càrrega de programes i molts cops ens fa fer diverses insta&#320;lacions del sistema pensant que tenim algun problema de configuració. Quan és més greu fastidia moltissim.

---

### Post by Frealof on 2008-05-19
Uix, pinta malament la cosa...

Bé, per acabar d'esbrinar si nomes es la Ram, faré el Memtest a les memòries a un altre PC (que no té problemes de placa) que corre per aquí... ja us diré el què.

Salut!

---

### Post by Curial on 2008-05-19
Jo comprovaria cada rack de memòria per separat. Si les proves juntes la que falla et pot estar fent la punyeta i desorienta bastant.
Quan arribis a la conclusió que ets falla quelcom, pots acabar d'estar segur reproduint el problema en un lloc diferent (cas de la memòria).


Sort.

---

### Post by Frealof on 2008-05-20
Ei bones...

Ja ho vaig fer d'anar "memtestejant" cada dimm per separat i en cada ranura (racks?) fins a esgotar possibilitats, el què potser no m'havia explicat prou bé...

Tal com ja vaig dir que faria... He provat els dimms en un altre PC, els hi he fet el memtest i no m'ha donat CAP error. Per tant si els dimms estan bé, el què pot originar les fallades hauria de ser l'altre component de maquinari, les ranures (racks?)...

Creieu que puc certificar la defunció de la Placa Base?

Salut!

---

### Post by LitusMayol on 2008-05-20
> **Frealof said:**
> Ei bones...

Tal com ja vaig dir que faria... He provat els dimms en un altre PC, els hi he fet el memtest i no m'ha donat CAP error. Per tant si els dimms estan bé, el què pot originar les fallades hauria de ser l'altre component de maquinari, les ranures (racks?)...

Creieu que puc certificar la defunció de la Placa Base?



Jo he fet el mateix i em passa el mateix, però amb una diferència: l'UbuntuStudio em funciona sense cap problema... 

que faig...?

---

### Post by papapep on 2008-05-20
> però amb una diferència: l'UbuntuStudio em funciona sense cap problema... 

Jo en el teu cas cridaria directament a un exorcista....:-D

---

### Post by Frealof on 2008-05-20
No Papapep, l'exorcista l'hauré de demanar jo... 

Un amic m'ha deixat una placa pràcticament nova i després de connectar-ho tot seguint les instruccions... he engegat, passat el memtest i no m'ha donat cap error (l'he parat quan ja portava 5 tests complets...)

Tot ha anat molt bé fins que se m'ha congelat un cop (teclat inclòs), he re-iniciat i després ja directament se m'ha apagat del tot...

De moment encara tot va tirant bé, però hi ha alguna cosa que falla i sincerament, no se m'acut què pot ser, i de fet tampoc sé massa què buscar :( 

En fi... Demà seguirem fent proves a veure què.

EDITO:
La placa i el processador avui han fet "xuf" definitivament... :( Ja ho he portat a una botiga que m'hi facin una repassada i mirin a veure què es pot salvar. En fi, esperem que amb les coses noves que hi posin tot vagi com ho ha de fer ;)

Salut i gràcies per la paciència que esteu demostrant.

---

### Post by indiosincracia on 2008-05-25
Si no t'hi vols trobar una altra vegada, t'aconsello un regulador de tensió amb bateria, això t'ho pararà tot, aquesta és la millor inversió que he fet en la meva vida, s'han acabat pantalles congelades teclats que no van, penjades, espurnes a les ranures dels slots, font d'alimentació que fa fum, o xip de la tarja gràfica (per cert, en aquest últim, sort que tenia el desodorant del water aprop).

---

### Post by LitusMayol on 2008-05-25
> **indiosincracia said:**
> Si no t'hi vols trobar una altra vegada, t'aconsello un regulador de tensió amb bateria, això t'ho pararà tot, aquesta és la millor inversió que he fet en la meva vida, s'han acabat pantalles congelades teclats que no van, penjades, espurnes a les ranures dels slots, font d'alimentació que fa fum, o xip de la tarja gràfica (per cert, en aquest últim, sort que tenia el desodorant del water aprop).

I això on ho puc trobar i què em costarà? 

Merci!

---

### Post by indiosincracia on 2008-05-25
Aquí en tens dos si remenes entre el gogle i carrer Sant Antoni en trobaràs més:)
[http://www.gnuinos.com/drupal/?q=taxonomy/term/14](http://www.gnuinos.com/drupal/?q=taxonomy/term/14)
[http://www.optize.es/servlet/SOYNTEC_SAI_UPS_SEKURY_A_600_V.A._+_KIT__132463_optize.html](http://www.optize.es/servlet/SOYNTEC_SAI_UPS_SEKURY_A_600_V.A._+_KIT__132463_optize.html)
Apa DEuu.

---

