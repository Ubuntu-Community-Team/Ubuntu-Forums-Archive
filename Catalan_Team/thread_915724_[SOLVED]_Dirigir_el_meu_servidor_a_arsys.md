---
title: "[SOLVED] Dirigir el meu servidor a arsys??"
date: 2008-09-10
forum: Catalan Team
---

### Post by kukat on 2008-09-10
Bon Dia Gent! Per fi tornem a la rutina, després de dos mesos currant tots els dies  com un boig (vaja vacances, eh? jajaja), i de no poder fer pràcticament res amb l'ordinador, tornem a la rutina! (meravellosa rutina..jaja)

Doncs res, que m'he fet amb la web del grup: pellikana.cat, a través d'Arsys, i vaig molt perdut. La web ja la tinc pràcticament feta a /var/www (amb Kompozer i l'editor de text! jejej) però ara no tinc ni idea de que fer per a que es veja a través d'Arsys el meu ordinador (provisionalment, mentre aconseguim algún que faça de servidor) 

Vaig fer alguna cosa amb la web NO-IP per a que la IP dinàmica puga convertir-se en una estàtica i eixes coses

Però que tinc que configurar al Apache o al DNS o on siga i a Arsys per a que es veja el meu ordinador, o siga, la pàgina web en si? 

Si teniu alguna guia o alguna cosa, en seria de gran utilitat. Vaig un poc perdut!

Gràcies!

PD: perdoneu per el rotllo....

---

### Post by papapep on 2008-09-10
...a veure, que jo ho entengui..:

 - Vols dir que has registrat el domini pellikana.cat a través del serveis de registrador d'Arsys, oi? :-)
 - que estàs creant el lloc web a casa teva, i que vols redirigir el DNS a la ip de casa teva?


> Vaig fer alguna cosa amb la web NO-IP per a que la IP dinàmica puga convertir-se en una estàtica i eixes coses

No, no vas convertir la ip de dinàmica a estàtica, el que vas fer és crear un domini (no-ip.com, per exemple) que es vincula sempre a la ip que tinguis en aquell moment. Indiferentment de que la ip sigui 1.2.3.4 o 4.3.2.1, posant no-ip.com, els servidors de DNS porten la petició a la ip correcta en cada moment.

O sigui, que com que tu ja tens un domini propi, no crec que et donguin el servei de franc. Que jo recordi, tan dyndns com no-ip ho permeten de franc quan agafes dominis dels seus.

No sé si he respost, part, dels teus dubtes. La resta del tema tècnic del teu servidor no té, encara, sentit fins que això no estigui arreglat. ;-)

---

### Post by kukat on 2008-09-10
si, les dos primeres preguntes es això.
Estic fent el servidor al meu ordinador (de moment, per que el que volia gastar de servidor està estropejat, però per anar tirant)
I si, a No-IP vaig fer un domini (per que, no ho se....jajjaj)
Doncs...com dirigixc el meu domini "pellikana.cat" de arsys al meu ordinador?? 
Com la ip és dinàmica pensava que tenia que fer alguna mena de truc per a que no variara amb el servei de No-Ip...però ja estic rallant-me!
Tindré que configurar alguna cosa a l'Apache, no? tinc el Webmin que ho fa més fàcil, però es que vaig perdut...
Gràcies!

EDITO: Vaig començar amb aquest tutorial, però fent-ho amb Ubuntu: [http://www.forat.info/2008/03/05/como-montar-un-servidor-web-con-linux-debian/print/](http://www.forat.info/2008/03/05/como-montar-un-servidor-web-con-linux-debian/print/), però clar, tampoc se segur el que faig..jajaj es la primera vegada que pose a la pràctica açò, a pesar d'haver donat teòricament alguna cosa, una vegada començes a fer-ho es altre món.

---

### Post by papapep on 2008-09-10
Jo el primer que faria és parlar amb Arsys a veure si ells tenen alguna solució prevista per temes així (redirecció de dominis a ip dinàmica), que no ho crec, però començaria per aquí.

Un cop solucionat això, has de redirigir el port 80 tcp (http) del teu router a la ip de la xarxa, i port 80 tcp, de l'ordinador que faràs servir de servidor.

El tema de l'apache és molt fàcil, no cal ni webmin ni res, ja ho veuràs quan hi arribem.

---

### Post by kukat on 2008-09-10
Al panell del control del parking, tinc un apartat que diu DNS on pots afegir 

Dominio (pellikana.cat)
Entrada DNS
Tipo de entrada DNS (per defecte A)
Valor: 

???
ni idea. Els ho he preguntat. A veure que tarden en respondre estos de arsys...jajaj
Gràcies!

---

### Post by Tomàs M. on 2008-09-10
El tema no-IP o un d'equivalent és condició necessària, però no suficient.
Tot i que jo de servidors de noms no en sé i d'altra gent que volta per aquí sí que t'hi podrà ajudar, si no m'equivoco ho pots solucionar a [http://editdns.org/](http://editdns.org/). No sé si Arsys t'ho solucionaria, però al lloc on tinc registrats jo uns quants dominis, no hi puc configurar res de registres CNAME, que és el que necessites.
Resumint: a can Arsys has de dir-los que els DNS's són a can editdns (ns1.us.editdns.net, i el mateix amb 2 i 3), i a can editdns ho has de configurar perquè el domini que has comprat redireccioni cap al subdomini que t'has agafat a no-IP mitjançant el registre CNAME (i que redireccionarà cap al teu ordinador perquè a can no-IP saben en tot moment quina IP tens, sempre que ho hagis configurat bé :) )
Més que res per si un altre dia ho he de tornar a fer, em vaig guardar una petita guia a [http://tomasmallafre.blogspot.com/search?q=domini+propi](http://tomasmallafre.blogspot.com/search?q=domini+propi)
Ës per a utilitzar un domini propi a blogger, però segurament et servirà. I si no, segur que algú altre t'ho explica millor que jo.
Sort!

Edito perquè a editdns també tenen redireccionament a IP's dinàmiques, però aquí no sé com funciona; potser et pots estalviar haver de passar per no-IP:

Free Dynamic DNS
Do you have a dynamic IP from your cable or DSL company? You can automatically update your IP address for your domain as soon as it changes.

Torno a editar per al tercer capítol :-P
Un cop ho hagis fet, pots donar una mirada a [http://host-tracker.com/](http://host-tracker.com/) ; si ho has fet bé, en qüestió d'hores veuràs com es va propagant el domini.

---

### Post by kukat on 2008-09-10
de moment els d'arsys han contestat açò: "En respuesta a su consulta, indicarle que por el momento en Arsys.es no disponemos de Servicio de DNS dinámicas, por lo que no es posible realizar esta configuración."
Vaig a pegar-li una miradeta a el que m'has dit a veure...
Gràcies!

---

### Post by kukat on 2008-09-10
m'he registrat a EditDNS, però no se el que fer....

He vist que al panell de control de Arsys si que està l'opció del CNAME que dius més amunt. "Tipo de entrada DNS: CNAME"
Que hi faig al EditDNS? pose el domini "pellikana.cat"?? uff...vaig perdut perdut...perdoneu i moltes gràcies.

---

### Post by Tomàs M. on 2008-09-10
> **kukat said:**
> 
He vist que al panell de control de Arsys si que està l'opció del CNAME que dius més amunt. "Tipo de entrada DNS: CNAME"

Ep! doncs prova de posar-hi el subdomini de no-ip, potser amb això serà suficient.

---

### Post by papapep on 2008-09-10
Si et rellegeixes el post d'en Tomàs amb tranquilitat veuràs que ja t'ho ha dit:

 - Al registre CNAME de Arsys has de fer que el teu domini pellikana.cat apunti al servidor de DNS de EDITDNS. O sigui, que al cname posi el seu servidor. Segons diu en Tomàs: ns1.us.editdns.net
Això pels tres registres CNAME de Arsys.

 - A EDITDNS has de fer que el registre CNAME apunti al domini que vas configurar en el seu moment, o un de nou, a no-ip. O sigui, has de modificar també el CNAME que tens a EDITDNS a fi de que apunti a ell, p. ex.:  pellikana.no-ip.org (aquest l'has de saber tu quin és, clar).

Les peticions demanant per veure el lloc web pellikana.cat arribaran als servidors d'Arsys, aquests reenviaran la petició, gràcies als registres que hauràs configurat, al d'EDITDNS. Immediatament aquests, al seu temps, enviaran la petició als servidors de NO-IP els quals miraran quina ip tens en aquell moment i te les enviaran (les peticions) al teu router, el qual (buffff) les redirigirà, un cop l'hagis configurat correctament al teu servidor web que les atendrà (un cop hagis configurat l'apache, clar)....guais, no? :-D

---

### Post by kukat on 2008-09-11
Açò es el que tinc a EditDNS: [http://img178.imageshack.us/img178/2374/capturahm4.png](http://img178.imageshack.us/img178/2374/capturahm4.png), he posat el de NO_IP com una entrada CNAME...

Omplic a Arys:

Dominio: pellikana.cat
Entrada DNS: ns1.us.editdns.net.
Tido de entrada DNS: CNAME (no?)
Valor: Aci no se que posar (???¿¿) Aquesta es l'entrada que no se.....buffff....segur que es una tonteria..j.ajaja

Ja esta quedant tot mes o menys clar, però encara hi tinc algún dubte...moltíssimes gràcies, de veritat, i feliç diada!!! A veure si avui, 11S podem fer anar la web ...jejej!

---

### Post by kukat on 2008-09-11
al final s'ha quedat aixi!!!
[http://img55.imageshack.us/img55/7439/capturareadeclientelh0.png](http://img55.imageshack.us/img55/7439/capturareadeclientelh0.png)
No se si ho he fet bé...he posat al valor "pellikana.cat"
no se...jjejjeej
I al EditDNS he ficat això de URL FORWARD i he posat la direcció de NO-IP...no se si era això el que tenia que fer....:confused:
Gràcies!

---

### Post by Tomàs M. on 2008-09-11
Ara comptaré fins a 3 i oblidaràs tot el que t'he dit... és broma :-P

A veure, em sembla que és millor que no vagis provant a sorts, perquè així és molt complicat. Jo començaria provant amb el subdomini de no-IP al registre CNAME d'Arsys; ho proves i al cap d'un parell d'hores comproves si s'està propagant amb l'altre enllaç que et vaig donar. Si no funciona, mirem la solució d'editdns (ho he mirat pel damunt però em sembla que la configuració que hi has posat no és correcta).

---

### Post by kukat on 2008-09-12
Bon dia!!!
Vaig posar anit abans de gitar-me el subdomini de NO-IP a Arsys
[http://img521.imageshack.us/img521/4156/capturareadeclientemozixu2.png](http://img521.imageshack.us/img521/4156/capturareadeclientemozixu2.png)
però amb el HostTracker (ara a les 9,14) sols ixen 217.76.128.34 (51 entrades)
a No-Ip tinc açò: [http://img133.imageshack.us/img133/3705/capturanoipcomthedynamipo9.png](http://img133.imageshack.us/img133/3705/capturanoipcomthedynamipo9.png),
Falta configurar l'Apache, no se si serà per això! i la IP del NO-IP correspón amb la que tinc.....
Gràcies!!!!!!!!!!!!!!

---

### Post by Tomàs M. on 2008-09-12
Em sembla que l'entrada que tens de CNAME a Arsys  hauria de ser pellikana.sytes.net, sense el pellikana.cat al darrera. El que no tinc clar és què va a "entrada" i què a "valor"
Què et diu el hostracker?
Si escrius localhost al navegador, veus el teu web?
A no-IP em sembla que ja ho tens bé.

---

### Post by kukat on 2008-09-12
Si, quan pose localhost m'ix la web
i quan pose 192.168.0.71 també, ja que vaig configurar el eth0 , per a que sigera eixa IP. (seguint el manual de [http://www.forat.info/2008/03/05/como-montar-un-servidor-web-con-linux-debian/print/](http://www.forat.info/2008/03/05/como-montar-un-servidor-web-con-linux-debian/print/))

Jo ho pose així
Domini: pellikana.cat
Entrada DNS: la de NO-IP (pellikana.sytes.net)
Tipo de entrada: CNAME
Valor: Jo tampoc se que posar, i havia posat pellikana.cat, per això surt el pellikana.cat al darrere,crec....
no se....

El hosttracker sols en mostra la ip 217.76.128.34, que es una de les que ja estava....no se....

---

### Post by Tomàs M. on 2008-09-12
Doncs ara ja no en sé més :confused: No hi ha ningú per aquí amb un domini a Arsys? Jo provaria amb pellikana.cat a "entrada" i [http://pellikana.sytes.net](http://pellikana.sytes.net) a "valor" al registre CNAME...

Fixa't que [http://pellikana.sytes.net](http://pellikana.sytes.net) ja funciona (tu no ho pots veure); ara només queda configurar-ho correctament a can Arsys.

---

### Post by Compact on 2008-09-12
Jo tinc un .cat a Arsys (encara que no faig servir el seu DNS) i a entrada has de posar el registre en si (el que anirà davant del domini) i a valor el domini a què va associat si és un CNAME, la ip si és un registre A, etc.

---

### Post by kukat on 2008-09-13
si pose pellikana.sytes.net a Valor, em diu açò "ERROR: Para este tipo, el valor debe ser del estilo subdominio.pellikana.cat o correo.pellikana.cat."
???? buffff....els d'Arsys podrien fer les coses un poc més intuitives..jejejej
Gràcies a tots!!!

---

### Post by kukat on 2008-09-13
Ok. He preguntat a Arys i diuen: "En respuesta a su consulta, indicarle que para redirigir el dominio que nos indica necesitará cambiar el Parking actual por un Plan Redirigido: http://www.arsys.es/hosting/redirigido"

Doncs....per a que serveix el DNS del Parking que ve per defecte al registrar el domini????? Si no queda més remei contractaré el Plan Redirigit eixe...Vosaltres direu! jejeje

Gràcies!

---

### Post by Tomàs M. on 2008-09-26
> **kukat said:**
> si pose pellikana.sytes.net a Valor, em diu açò "ERROR: Para este tipo, el valor debe ser del estilo subdominio.pellikana.cat o correo.pellikana.cat."
???? buffff....els d'Arsys podrien fer les coses un poc més intuitives..jejejej
Gràcies a tots!!!

Iep! Com tens aquest tema? L'altre dia per una història vaig comprovar que la meva teoria funciona (al registrador tinc configurats els DNS's d'EditDNS i des d'aquí arribo fins a la meva màquina passant per no-IP, mitjançant un "URL forward" a EditDNS).
Per tant, jo ara provaria:
1-Eliminar l'entrada CNAME d'EditDNS
2-"URL forward" amb "forwarded URL" [http://pellikana.sytes.net](http://pellikana.sytes.net)
3-"Nueva entrada en zona DNS" a Arsys: entrada, pellikana.cat; tipo, A; valor, ns1.us.editdns.net (potser abans hauràs d'eliminar l'entrada actual que apunta a 217.76.128.34 -aquesta IP deu ser d'Arsys?-)

Si al cap d'unes hores funciona, repetiria el pas 3 amb ns2.us.editdns.net i ns3.us.editdns.net

Sort!

---

### Post by kukat on 2008-09-26
Ie!!
Tinc novetats!!! He estat provant amb un hosting gratuit....Per que no hi havia manera de fer-ho, i per què crec que no vaig a poder fer-me un servidor des de ma casa. 

Tinc aquesta captura on em diuen que canvie els dos servidors d'arsys....[http://img337.imageshack.us/img337/2617/screenshot000webhostcomal1.png](http://img337.imageshack.us/img337/2617/screenshot000webhostcomal1.png) , en el hosting gratuit OOOwebhost.com i m'expliquen (com podeu veure a la imatge) que canvie els servidors DNS del meu domini.

I aquesta altra és d'Arsys, que he encontrat on canviar els servidors!! i ara que estic pensant...probablement és el lloc on tenia que canviar-ho, no en el parking..no?? [http://img257.imageshack.us/img257/5606/screenshotreadeclientemdh3.png](http://img257.imageshack.us/img257/5606/screenshotreadeclientemdh3.png), mare, es que porte un embolic....

Doncs això, que quan pose els dos servidors que em donen a 000webhost, em diu que la IP (jo pose la que hi ha a la dreta...:confused:) no és la del servidor...no se...porte un embolic!!!!
Però crec que ja està un poc mes clar, a pesar de no saber ja per on tirar......bufff...

Gràcies!

---

### Post by Tomàs M. on 2008-09-27
> **kukat said:**
> Ie!!
...

Doncs això, que quan pose els dos servidors que em donen a 000webhost, em diu que la IP (jo pose la que hi ha a la dreta...:confused:) no és la del servidor...no se...porte un embolic!!!!
...

Gràcies!

Pots penjar una imatge d'això?

---

### Post by kukat on 2008-09-29
En resum, el Panell de Control de 000Webhost (el hosting gratuit): [http://img337.imageshack.us/img337/2...hostcomal1.png](http://img337.imageshack.us/img337/2...hostcomal1.png)
Els servidors de noms que porta Arsys per defecte:
[http://img257.imageshack.us/img257/5...lientemdh3.png](http://img257.imageshack.us/img257/5...lientemdh3.png)

Els servidors de noms que li fique jo de 000webhost (jo crec que la IP no es la que pose, però es que no hi ha altra!:confused:)
[http://img90.imageshack.us/img90/4527/capturareadeclientemoziss5.png](http://img90.imageshack.us/img90/4527/capturareadeclientemoziss5.png)

Missatges que ixen: 
[http://img301.imageshack.us/img301/6773/capturalapginaahttpssecfw0.png](http://img301.imageshack.us/img301/6773/capturalapginaahttpssecfw0.png)

[http://img223.imageshack.us/img223/812/capturareadeclientemozitx7.png](http://img223.imageshack.us/img223/812/capturareadeclientemozitx7.png)

Gràcies, però crec que es això, que la IP no correspon amb la que pose, però clar...quina és si no es eixa????:confused:
Salut!

---

### Post by Tomàs M. on 2008-09-29
Segons la imatge de l'altre dia, - [http://img337.imageshack.us/img337/2617/screenshot000webhostcomal1.png](http://img337.imageshack.us/img337/2617/screenshot000webhostcomal1.png) -, 64.235.52.170 correspon al nom server17.000webhost.com, no a ns01.000webhost.com...

A veure, edito perquè per una altra banda et diuen que el teu domini apunti a ns01.000webhost.com, però clar, aquest nom té una altra IP; fent-hi ping contesta 66.197.153.229 (ei, però jo de tot això no en sé!). Segur que cal posar la IP a Arsys, a més del nom?

---

### Post by kukat on 2008-09-29
si, posa que hi ha que posar la IP...doncs no se m'havia ocurrit fer un ping....vaig a provar-ho a veure..jejje

---

### Post by kukat on 2008-09-29
doncs m'ha deixat canviar-ho!! jajajaj a vorem....
Gràcies, ja et conte les novetats (si m'ho he carregat tampoc passa res, que ja no veig altres alternatives! jejejej:))

---

### Post by kukat on 2008-09-30
SIIIIIIIIIii!!!!!!!!!!!!!!!!!!
Doncs ja funciona!!!! Moltíssimes Gràcies!!!!!! 
[http://www.pellikana.cat/](http://www.pellikana.cat/)

De moment queda molt per fer, però ja puc veure com va quedant (que no es el mateix veure-ho al teu ordinador que en els altres..jejeje) 

Moltíssimes Gràcies!!!!!!! Ja està tot solucionat!!

---

### Post by SiscoGarcia on 2008-10-02
Enhorabona kukat! Estic remenant pel vostre web a la vegada que escolte "Resistirem". Que tingueu sort! ;)

---

### Post by kukat on 2008-10-03
Gràcies! Si no fora per aquest forum..jajjejeje

Tota la web feta amb Kompozer i el bloc de Notes, amb l'ajuda del GIMP, per supost..jeje
Bé, el llibre de visites en PHP l'he descarregat i l'he adaptat a la web, per què era massa feina fer tot el codi PHP..jejej:D Però ja es pot firmar!!

Moltes gràcies! 

Pd:ufff...ara una tranquilitat..jejeje

---

### Post by jaume69 on 2008-10-03
M'alegro que per fi et funcioni.

Vaja "merders" que tens que fer per a tenir un Domini propi,jo al principi em pensava que era més fàcil però ara ja he vist que no.

I total perquè algun dia arribi un "....às" t'hi foti codi dolent te la Hakeji i au!,tot a can pistraus.

Ademés que un Servidor que et funcioni o respongui bé i ràpid,deuen ser els més cars!!

Però bé,és un risc que suposo que has de pendre.

____________________________
Salut.

---

