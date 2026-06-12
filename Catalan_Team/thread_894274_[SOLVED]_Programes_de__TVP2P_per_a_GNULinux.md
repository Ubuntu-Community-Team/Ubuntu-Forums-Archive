---
title: "[SOLVED] Programes de  TVP2P per a GNU/Linux?"
date: 2008-08-19
forum: Catalan Team
---

### Post by LitusMayol on 2008-08-19
Bones familia!

Us poso una mica en context... Sóc bastant, tirant a molt, *futbolero*. A part del *Barça* sóc de l'Arsenal (de la Prèmiere anglesa -per si hi ha algú que no li agrada el futbol-). 

Doncs bé, el *Barça* entre *Tv3*, *LaSexta* i els bars (ho sento no tinc el plus!) el puc veure. Però l'Arsenal no és tan fàcil... L'any passat vaig treballar a un bar que cada cap de setmana passava o bé l'Arsenal o bé el Manchester United (i ho feia durant el meu torn!!! :) ). Per tan el vaig seguir prou bé. Fa dos anys el mirava a través de [RojaDirecta]("http://www.rojadirecta.org/"). Però aleshores encara anava a mig camí entre **Windows** i **SuSe**, i per mirar el futbol feia servir el nostre amic de les finestres.


Aquest any ja no estic al bar on el passaven, i m'agradaria poder seguir l'Arsenal (si més no poder-ne veure un partit cada 15 dies almenys...). Jo voldria saber si algú coneix algun equivalent per a **Ubuntu** de **PPStream**, **SopCast** i companyia...

La veritat en aquest tema de mirar la TV per P2P vaig peix peix. Amb el **Windows** tan el **PPStream** com el **SopCast** em van funcionar de conya; però suposo que fer-los funcionar amb el **Wine** és massa enrabassat i segur que tinc alguna alternativa ja existent a **Ubuntu**.


Algú sap com solucionar-ho?


Merci!:lolflag:

---

### Post by oriolsbd on 2008-08-19
Doncs no cal. :-)

Tens dues opcions:

1- A RojaDirecta, alguns dels enllaços et deixen veure directament el partit pel navegador.

2- Hi ha una versió de SopCast per a Linux. Te la pots baixar aquí: [http://download.sopcast.cn/download/sp-auth.tgz](http://download.sopcast.cn/download/sp-auth.tgz)

Descomprimeix el fitxer, i et deixarà dos fitxers en el subdirectori sp-auth. Un d'ells és directament l'executable de SopCast, i es diu "sp-sc-auth". Per fer més fàcil la seva utilització, el pots copiar a /usr/bin (amb sudo).

Per executar el programa, has de copiar l'enllaç "SopCast" del partit des de la web de RojaDirecta. Per exemple, imagina que l'enllaç és "sop://sop.rojadirecta.com:3912/6002". Amb el programa SopCast que ens hem baixat obrirem la connexió amb l'enllaç. Des d'un terminal (no importa en quin directori estiguis) executa el següent:

sp-sc-auth sop://sop.rojadirecta.com:3912/6002 3908 8908 >/dev/null &

Ara l'ordinador ja s'està baixant online el partit. Per mirar-lo, has d'anar a qualsevol reproductor de vídeo de Linux (per exemple el Totem, el VLC, etc.), i obrir la següent ubicació:
[http://localhost:8908/tv.asf](http://localhost:8908/tv.asf)

El "8908" d'aquesta URL ha de ser el mateix que s'ha indicat en el "sp-sc-auth". Realment és el port pel qual t'arriba el stream, i pots utilitzar-ne algun de diferent. Ara podràs veure l'esdeveniment per SopCast. Aquest normalment té un retard més gran que si es fa per enllaç directe (uns 30 segons).

NOTA: Les instruccions del Sopcast són agafades i "retocades" d'un correu que vaig enviar a uns amics fa uns mesos (per les últimes finals de la NBA). Suposo que encara funciona igual.

De les dues opcions que hi ha (visualització Web o per Sopcast) et recomano la primera, però ja va bé tenir el SopCast instal·lat per si un partit no té cap enllaç per a visualitzar-lo directament al navegador.

Salut!

---

### Post by LitusMayol on 2008-08-19
Renoi **oriolsbd**!

Em sorprèn, pensava que seria més complicat (compte, que encara no ho he provat...). Aparentment és més senzill fins i tot que usant **Windows**. 

Ara sóc a la feina, així que arribi a casa ho provo i us en dic alguna cosa.


Merci ja avançadament!

---

### Post by LitusMayol on 2008-08-19
Torno a ser jo!

En principi sembla que funciona (no sabia que les "*no p2p*" es veiessin a través del **FireFox**).

He fet tot el que m'has dit: baixa't el paquet, descomprimit, enviat a */usr/bin*... Però a la programació ara no hi ha res i no ho puc provar.
:lolflag:

Em sap greu! hehe

Aquest dissabte juga l'Arsenal. Demà si m'enrecordo ho provo però si em passa com avui (que no quedava res per veure quan he arriabt de la feina) dissabte us dic què.

De moment: *[SOLVED]*  ;)

---

