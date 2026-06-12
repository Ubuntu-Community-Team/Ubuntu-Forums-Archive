---
title: "[SOLVED] Synaptic [sources.list-d'altres]"
date: 2008-01-24
forum: Catalan Team
---

### Post by prostata on 2008-01-24
Bon dia:

Necesito el vostre consell sobre:

El programari Kdprint que el veia a Synaptic, ara no hi és, ¿com puc fer per  que torni a ser Kdprint?

Suposso que sources.list deu tenir a veure amb els respos de synaptic, si és així ¿cóm puc saber si estic amb el sources.list totalment actualitzat, o dit d'altre forma, hi ha alguna manera d'actualitzar soureces.list?

Voldria crear un "acces directe al escriptori" de la carpeta personal. quan em possiciono sobre ella i amb el botó dret del ratolí li dic crear, el que fa es obrir-se la carpeta personal, per contra a altres aplicatius això no em passa?

Gràcies

---

### Post by papapep on 2008-01-24
> El programari Kdprint que el veia a Synaptic, ara no hi és, ¿com puc fer per que torni a ser Kdprint?


No serà que el paquet es diu **[kdeprint]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kdeprint&searchon=names&subword=1&version=gutsy&release=all")**?

> Suposso que sources.list deu tenir a veure amb els respos de synaptic, si és així ¿cóm puc saber si estic amb el sources.list totalment actualitzat, o dit d'altre forma, hi ha alguna manera d'actualitzar soureces.list?


El sources.list no s'actualitza en si mateix. A dins d'ell hi tens les referències als repositoris que tu vulguis. El que si que s'actualitza és al base de dades de paquets que hi ha als repositoris que tu has especificat dins el sources.list.

Per cert, per actualitzar la base de paquets, des d'el Synaptic crec que hi ha un botó que es diu "Actualitzar", i des del terminal cal fer:

```
sudo aptitude update
```

> 
Voldria crear un "acces directe al escriptori" de la carpeta personal. quan em possiciono sobre ella i amb el botó dret del ratolí li dic crear, el que fa es obrir-se la carpeta personal, per contra a altres aplicatius això no em passa?

Dins un terminal fas (suposant que el teu usuari sigui próstata i que a l'enllaç li vulguis dir Carpeta_personal):

```
cd /home/prostata/Escriptori
ln -s /home/prostata/   Carpeta_personal
```

També es pot fer sense anar al directori on vols crear l'enllaç, donant-li el camí absolut:


```
ln -s /home/prostata/   /home/prostata/Escriptori/Carpeta_personal
```

---

### Post by kukat on 2008-01-24
Has mirat a "Sistema" "Administració" "Fonts de Programari"? Es on pots configurar d'on venen els paquets del Synaptic. 

Després al Synaptic, en clicar a "Refresca" ja deu de actualitzar-se...

Salut!


Perdó, quan he començat a escriure encara no hi havia cap "reply"... :)

---

### Post by jodufi on 2008-01-24
Hola,

Si et vols posar la carpeta personal a l'escriptori i fer opcions "avançades" sense tocar el terminal, pots instalar-te l'Ubuntu Tweak.

Aquest et permet configurar d'una manera molt fàcil algunes configuracions del sistema.

El pots baixar des de:
[http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.2.5-1%7Eppa4_all.deb](http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.2.5-1%7Eppa4_all.deb)

O pots afegir-lo al teu sources.list seguint aquests passos:
[http://ubuntu-tweak.com/2008/01/22/ubuntu-tweak-has-repository-now.html#more-31](http://ubuntu-tweak.com/2008/01/22/ubuntu-tweak-has-repository-now.html#more-31)

---

### Post by prostata on 2008-01-24
> **papapep said:**
> No serà que el paquet es diu **[kdeprint]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kdeprint&searchon=names&subword=1&version=gutsy&release=all")**?



El sources.list no s'actualitza en si mateix. A dins d'ell hi tens les referències als repositoris que tu vulguis. El que si que s'actualitza és al base de dades de paquets que hi ha als repositoris que tu has especificat dins el sources.list.

Per cert, per actualitzar la base de paquets, des d'el Synaptic crec que hi ha un botó que es diu "Actualitzar", i des del terminal cal fer:

Si, això ja ho sé, gracies, aquí no he sabut explicar-me clarament, disculpeu...

```
sudo aptitude update
```


[/B]Idem[B]


Dins un terminal fas (suposant que el teu usuari sigui próstata i que a l'enllaç li vulguis dir Carpeta_personal):

```
cd /home/prostata/Escriptori
ln -s /home/prostata/   Carpeta_personal
```

També es pot fer sense anar al directori on vols crear l'enllaç, donant-li el camí absolut:


```
ln -s /home/prostata/   /home/prostata/Escriptori/Carpeta_personal
```

Gràcies, així ho faré,
salutacions

---

### Post by prostata on 2008-01-24
Gràcies per les vostres respostes, com li deia a en papapep, no he sabut explicar-me correctament ja que si sé que en actualitzar el que fa, dins qualsevol eina i SO, normalment es actualitzar, refrescar etc. etc.

Sobre sources.list, jo em creia que un dels seus objectius, era precisament mantenir actualitzada la base de dades dels repos de synaptic, però com ja ha dit en papapep, no és pas així.

Per en papapep, certament el nomb del programari al que jo feia referència no es deia "kdprint", com tu molt bé m'has corregit, sino kdeprint, ja está a la vista un altre cop.

I aprofitant que us tinc per aquí. el programari Ktorrents és l'unic que em surt en llengua anglesa...què puc fer??
gràcies

---

### Post by papapep on 2008-01-24
> I aprofitant que us tinc per aquí. el programari Ktorrents és l'unic que em surt en llengua anglesa...què puc fer??

Doncs si no està traduït al català, i mentre ningú ho faci, tens dues opcions: traduïr-lo tu o canviar de client de torrent :-)

---

### Post by prostata on 2008-01-24
> **papapep said:**
> Doncs si no està traduït al català, i mentre ningú ho faci, tens dues opcions: traduïr-lo tu o canviar de client de torrent :-)

;-) ;-) ;-) ;-) ;-)  encara hi ha altre opció, ¿vols saber quina??? :-) deixar-lo tal com està....

---

### Post by CarlesOriol on 2008-01-24
> **prostata said:**
> ;-) ;-) ;-) ;-) ;-)  encara hi ha altre opció, ¿vols saber quina??? :-) deixar-lo tal com està....

Pot ser si... però tu que ja portes un temps amb el programari lliure aquesta pot ser una oportunitat per començar a co&#320;laborar amb tothom que fa coses fet del que evidentment en gaudeixes.

Traduir aquest programa amb la guia d'estil de softcatalà i fins i tot amb l'ajuda dels membres de l'equip ... que et pot prendre 3 hores? 

A més de la satisfacció d'haver creat alguna cosa encara que sigui petita també tindras recompensat el teu esforç quan ensenyis als teus amics i familiars que al ubuntu i evidentment a totes les altres distribucions que l'incloguin un programa que has traduït tu.

Apa....   Vinga..... Som-hi! ..........................

---

### Post by prostata on 2008-01-24
> **CarlesOriol said:**
> Pot ser si... però tu que ja portes un temps amb el programari lliure aquesta pot ser una oportunitat per començar a co&#320;laborar amb tothom que fa coses fet del que evidentment en gaudeixes.

Traduir aquest programa amb la guia d'estil de softcatalà i fins i tot amb l'ajuda dels membres de l'equip ... que et pot prendre 3 hores? 

A més de la satisfacció d'haver creat alguna cosa encara que sigui petita també tindras recompensat el teu esforç quan ensenyis als teus amics i familiars que al ubuntu i evidentment a totes les altres distribucions que l'incloguin un programa que has traduït tu.

Apa....   Vinga..... Som-hi! ..........................

estimat carles; a mi ja m'ha passat el temps de la docència, des que vaig deixar la uni.....

el meu nivell de català es molt deficient....

com tu dius, ben dit, jo ja gaudeixo...

es clar que reconec l'esforç de les persones que intervenen en les traduccions i tenen tot el meu respecte i la meva admiració

als meus amics i familiar i saludats, ja els hi parlo del programari liure i de tot el que representa, de fet dins el coneixements informàtics que em va donar la meva llicenciatura i la meva experiència professional de més de 37 anys, procuro que tots sapiguen diferènciar entre el soft propietari i el lliure....

a la tardor de la meva vida, tinc més coses interessants a fer, això  ja us queda a vosaltres que en teniu la pila super carregada...

ja ja hi passat pels ponts de madison, ara sou vosaltres, jo ja estic per gaudir de tot el que crec que m'he guanyat, i si voleu fer-me un cop de ma, doncs gràcies sino ja em buscaré la vida, com hi fet fins avui

les meves preocupacions humanìstiques i intel-lectual ja van per altres camins, però moltes gràcies per les teves indicacions...

sempre son, per mi, molt ben vingudes....

salutacions

---

### Post by CarlesOriol on 2008-01-28
Eps. 

No era intenció meva ofendre't sinò motivar-te. 

Per cert per que no passes pel fil de benvinguda i et presentes... sempre és millor coneixe'ns una mica.

I em sembla que sempre tots els que passejem per aquí sempre estem oberts a ajudar a qualsevol que puguem. Fins i tot quan algú es nou i pregunta un dubte això serveix per que algú que sigui nou més tard pugui coneixer tant la solució com els problemes.

---

### Post by prostata on 2008-02-04
> **CarlesOriol said:**
> Eps. 

No era intenció meva ofendre't sinò motivar-te. 

Per cert per que no passes pel fil de benvinguda i et presentes... sempre és millor coneixe'ns una mica.

I em sembla que sempre tots els que passejem per aquí sempre estem oberts a ajudar a qualsevol que puguem. Fins i tot quan algú es nou i pregunta un dubte això serveix per que algú que sigui nou més tard pugui coneixer tant la solució com els problemes.


No m'has ofes Carles, només et vaig argumentar la meva resposta, però no m'has ofes, estigues tranquil....

salutacions

---

