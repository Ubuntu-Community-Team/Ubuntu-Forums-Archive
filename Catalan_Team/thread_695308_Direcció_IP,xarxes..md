---
title: "Direcció IP,xarxes."
date: 2008-02-12
forum: Catalan Team
---

### Post by jaume69 on 2008-02-12
Hola macus,només voldria saber si hi ha molta gent que estigui navegant per internet darrera un Proxy.

He sentit a dir que és millor,en quan a problemes de conexió i per a navegar per tot tipus de webs,o que tens més cobertura com si diguéssim...

Normalment et donen un IP dinàmica i vas canviant d'ubicació cada vegada que et connectes.
O també te la poden donar Stàtica i igual que la dinàmica dona els mateixos efectes,o sigui que et canvia de direcció cada vegada que connectes.

No sé si val la pana tenir una direcc.Stàtica per per exemple una Web,etc.
I si el preu és molt més alt.
No sé,gràcies.  ):P


________________________________
:popcorn:

---

### Post by CarlesOriol on 2008-02-13
Buff.... quin poti-poti de conceptes!! Crec que el més important és que confons enrutador amb proxy. 

Un proxy no té res a veure amb l'assignació d'ips es sols un punt en la xarxa que serveix de repetidor d'informació (normalment a més fa de filtrat de continguts i caché).

 No té res a veure amb que sigui millor o pitjor... què és millor el color vermell o un cd rom?

El tipus de configuració d'ip segons entenc del teu mail te l'ofereix el proveïdor de servei enrutant-te una adreça concreta ip fixa o mitjançant un programa que es diu dhcp t'ofereix la primera lliure que troba.
Val la pena tenir una ip fixa sobretot si vols localitzat el teu ordinador remotament (per posar qualsevol tipus de servidor web, correu, unprogramaquethagisinventat), crear ponts entre diversos llocs d'internet... 

Però si sols és per emmagatzemar el web, no et val la pena per diverses raons 1. el sobrecost, 2. L'ample de banda que necessitaràs i que empraràs, 3. Et caldrà un ordinador sempre connectat.

Jo de tu de moment començaria amb una dinàmica cercaria algun lloc per emmagatzemar els meus webs i usaria una eina tipus dyndns per localitzar remotament el meu ordinador.

---

### Post by jaume69 on 2008-02-13
Doncs vaia(..*..),aquí no ai playa....

Jo crec que el millor seria que si tens un ordinador a casa(Adsl),la companyia proveïdora t'hauria de donar o tenir una adreça fixe per a cadascú o cada client.

(El telèfon fixe que tinc a casa no el  tinc amb cap adreça de Pontevedra o Baracaldo......),ja sé que és diferent però no deixa de ser un servei de PAGO l'Adsl igual que una línea telefònica.

No sé si se m'enten...

P.D.Per l'únic que val la pena és per als Hackers informàtics,que poden fotre destrosses a algú i després no els troben...

Però bé,la vida és dura...

---

### Post by papapep on 2008-02-13
> Jo crec que el millor seria que si tens un ordinador a casa,t'haurien de donar o tenir una adreça fixe per a cadascú o cada client.

Ei !!, pagant te la posen sense cap ni un problema: 12 leuros mensuals més :-D

Segons ells, se'ls acabaven les ip's amb l'[IPV4]("http://ca.wikipedia.org/wiki/IPv4") i per això havien de cobrar. Ara que es comença a implantar l'[IPV6]("http://ca.wikipedia.org/wiki/IPv6") ja m'explicaran quina excusa posaran... :-)

---

### Post by CarlesOriol on 2008-02-13
Es purament especulació d'adreces:

Ells tenen 10 adreces i saben que poden agafar 20 clients per que 10 no coincidiran mai... les seves estadistiques tindran.

Però això es pot solventar... el que es una estafa és la garantia d'ample de banda (on amb un adsl de 10 Mb on pots baixar fins a aproximadament 1000 Kb/seg (repeteixo APROXIMADAMEN) ... sols et garanteixen 4 Kb/seg... si això ho fessin amb l'aigua o l'electricitat segurament hi hauria revoltes socials... però la informàtica sols importa a quatre crios i a tres pirats.

---

### Post by lluisanunez on 2008-02-13
És especulació perquè amb una IP dinàmica ho tens mé difícil per a oferir serveis web, encara que hi han trucs. Per tant, si vols muntar serveis web des del teu ordinador, et cobraran una tarifa més alta.

---

### Post by papapep on 2008-02-13
Inicialment donaven ip's fixes a "tuti plen", però un cop varen veure que això també seria un negoci van tancar l'aixeta....són uns cabronets de pebrots...
El divertit és que les connexions que tenien ip fixa d'abans fa temps que les estan intentant reconvertir a ip dinàmica de totes totes. A una delegació de la feina ens han intentat regalar ordinadors, mesos de franc i les mil i una a canvi de passar a dinàmica. Però com que ens cal fixa, "all i aigua" (no rima, ja ho sé :) )

---

### Post by lluisanunez on 2008-02-13
A la meva feina ens han passat a tots a DHCP. Probablement han millorat la feina dels que havien de configurar els PCs de la gent (no molt, només que ja no han d'entrar uns quants numerets), i d'un *plumasso* han perdut la possibilitat d'identificar els ordinadors d'on venien les coses (tant bé que anava).
El mateix ha passat amb el correu: ara 80.000 persones tenim el correu del mateix domini (co msi anéssim d'uniforme), quan abans treballàvem amb subdominis, és a dir, que sabies de quin departament era cadascú només mirant l'adreça.
Cada cop més em trobo amb decisions preses amb aquesta miopia...:confused:

---

### Post by jaume69 on 2008-02-13
```
Però això es pot solventar... el que es una estafa és la garantia d'ample de banda (on amb un adsl de 10 Mb on pots baixar fins a aproximadament 1000 Kb/seg (repeteixo APROXIMADAMEN) ... sols et garanteixen 4 Kb/seg... si això ho fessin amb l'aigua o l'electricitat segurament hi hauria revoltes socials... però la informàtica sols importa a quatre crios i a tres pirats.
```Home,jo crec que ells et donen la velocitat real,la que especifiquen al paper,però hi ha molts paràmetres(servidors,...) que dificulten que pugui anar sempre al cent per cent.

Jo quasi les úniques ocasions que puc veure com la conexió va a tope és en baixades de Isos i en alguns programes...,pocs.:mad:

---

### Post by papapep on 2008-02-13
> Home,jo crec que ells et donen la velocitat real,la que especifiquen al paper,però hi ha molts paràmetres(servidors,...) que dificulten que pugui anar sempre al cent per cent.

hehhehehe, home, algunes màquines hi ha pel mig, però t'asseguro que ells no et donen el que t'han de donar (i si tu ets un privilegiat en aquest sentit, enhorabona). Jo amb la connexió que tinc actualment (3 megues amb timofònica) no em puc queixar comparat amb les que he tingut anteriorment a d'altres llocs i amb d'altres companyies. A vegades m'acosto als dos megues i mig!, però són uns lladregots. 
Molta propaganda i poc ample de banda real. Si això ho fessin amb algun altre producte (us imagineu anar a comprar un cotxe i que li faltessin les rodes o els seients del darrera? o que a un restaurant amb menú de tres plats, postres i beguda només te'n posessin un de plat???, o que al cinema a mitja película acabessin la sessió??  :) ) hi hauria un autèntic daltabaix i els foterien a la perrera...

---

### Post by eselma on 2008-02-14
> **jaume69 said:**
> Home,jo crec que ells et donen la velocitat real,la que especifiquen al paper,però hi ha molts paràmetres (servidors,...) que dificulten que pugui anar sempre al cent per cent.

Jo quasi les úniques ocasions que puc veure com la conexió va a tope és en baixades de Isos i en alguns programes...,pocs.:mad:

A vegades oblidem que la connexió ADSL la rebem mitjançant un parell telefònic que està previst per un ample de banda d'uns 3 kHz (uns 6 kbits/s). Els primers mòdems que tenia anaven a una velocitat [COLOR="Red"]vertiginosa[/COLOR] de 300 kbaud (llavors 300 kbits/s); després es va incrementar a 600, 1200, 2400, 4800, 9600... fins a 56 kbits/s (amb compressió CCITT). L'ADSL que teníem primer a 256 kb/s (uns 25 kBytes/s útils) ara pot anar a 3 Mb/s, i a vegades més.

Recordo que fa uns quants anys, en un congrés ens van explicar les proves que s'estaven fent per a la implantació de l'ADSL, llavors encara inexistent al nostre país. Ens van dir que un dels problemes era que, encara que tècnicament era possible arribar als 5 Mb/s i més, moltes línies suportaven difícilment amples de banda útils de més de 1 Mb/s: es retornaven massa paquets ATM. 

Bé, les línies que tenim ara són les mateixes, només que més velles. És com si volguéssim fer passar un TGV per les vies de Rodalies de RENFE (perdoneu la comparació).

Al meu parer, el que fan les companyies és oferir més i més ample de banda -estan en "campanya electoral" permanent- sense tenir en compte les possibilitats reals de cada línia, que pot estar més propera o més allunyada de la central. Al capdavall, encara que els equips terminals siguin de les companyies (a vegades ni això) les línies són les de *Timofònica *de tota la vida.

---

