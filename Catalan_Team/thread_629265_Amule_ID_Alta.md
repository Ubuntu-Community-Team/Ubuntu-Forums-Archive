---
title: "Amule ID Alta"
date: 2007-12-02
forum: Catalan Team
---

### Post by Curial on 2007-12-02
Déu vos guard a tots,

El meu amule està treballant amb la ID baixa i el servidor em dóna un missatge com aquest:NG : Your 4662 port is not reachable. Please review your network config.

He seguit les instruccions que donen a [http://www.amule.org/wiki/index.php/Firewall](http://www.amule.org/wiki/index.php/Firewall) però no sé si ho he fet bé (pel que dedueixo no! ;-) ).

No entenc que hi té a veure el router, firewall, .... i tot plegat.He consultat diferents comentaris referent al tema i no me'n surto.

El que vull és compartir arxius des d'enllaços edonkey a una velocitat normal, amb això en tinc prou, fins i tot estic disposat a fer servir un altre aplicació.

Bons ubuntaires, què m'aconselleu?

Gràcies d'antuvi.

---

### Post by muleta on 2007-12-02
Els Servidors ed2k ja fa temps que van deixar de funcionar, però et pots connectar als Razorback i a la xarxa KAD.

---

### Post by papapep on 2007-12-02
Curial: el router hi té a veure pel fet de que quan arriben connexions de fora de la teva xarxa i busquen el port 4662, el router no ho envia al teu ordinador (si tens un router adsl "normal"). 

Aquest cas encara el veuràs més clar si t'imagines una xarxa amb tres ordinadors que comparteixen la connexió a internet. Si un d'ells està executant l'amule, el teu ordinador surt pel router a internet a buscar el que vols descarregar, però quan els clients que volen connectar al teu ordinador intenten arribar-hi, primer han de passar pel router. Si no li dius on és el teu ordinador (quina IP té) no sap on enviar els paquets de dades.

Doncs el cas és el mateix amb un ordinador. Li has de dir al teu router (cada un és diferent i has de buscar fòrums específics del tema) que quan reb intents de connexió entrants al port 4662 els ha d'enviar a la ip del teu ordinador.

Ah! I si tinguessis el tallafocs activat també cal dir-li que deixi entrar les connexions.

---

### Post by Curial on 2007-12-02
En el cas del router és un CCT Zyxel inalàmbric de Telefònica que ja intentaré cercar alguna informació relativa.

Respecte al firewall, és una protecció del propi ubuntu?

En tal cas com la puc configurar-lo/desactivar per a que no m'interfereixi? (potser és poc recomanable??).

Que me'n dieu?

Gràcies moltes.:)

---

### Post by papapep on 2007-12-02
Respecte el router, crec que aquí trobaràs informació al respecte: [http://www.bandaancha.st/foros.php?temid=535531](http://www.bandaancha.st/foros.php?temid=535531)

> Respecte al firewall, és una protecció del propi ubuntu?

Per saber si tens el tallafocs activat, ves a Sistema > Administració i si hi tens una opció que es diu **Firestarter**, executa-la.
Aquesta és la interfície gràfica per a gestionar el tallafocs. Clica al quadrat per aturar-lo.
Si no tens la opció cap problema. T'en pots oblidar.

---

### Post by lluisalguero on 2007-12-02
> **Curial said:**
> En el cas del router és un CCT Zyxel inalàmbric de Telefònica que ja intentaré cercar alguna informació relativa.

Respecte al firewall, és una protecció del propi ubuntu?

En tal cas com la puc configurar-lo/desactivar per a que no m'interfereixi? (potser és poc recomanable??).

Que me'n dieu?

Gràcies moltes.:)


Mira't això a veure si et pot servir d'ajuda, aquest fòrum hi trobaràs de tot...

[http://www.adslayuda.com/Zyxel650.html](http://www.adslayuda.com/Zyxel650.html)

---

### Post by torracastanyes on 2007-12-02
Veig que utilitzes els ports originals de l'amule. Segons els entesos, és convenient  canviar-los perquè hi ha proveïdors que els bloquegen.

Diuen que els més segurs són del 50000 al 60000.

Pots canviar-los a Preferències>Connexió>ports TCP-UDP (millor canviar-los tots dos) i després canviar-los també al router i al tallafocs, si en tens.

 Pots trobar més informació als fòrums d'amule en castellà:

[http://forum.amule.org/index.php?board=21.0](http://forum.amule.org/index.php?board=21.0)

---

### Post by lluisalguero on 2007-12-02
Jo vaig servir el 8888 TCP i 8478 UDP...per si et serveix d'ajuda

---

### Post by papapep on 2007-12-03
Lluís, de ports pots fer servir els que vulguis (només són una convenció) sempre que no creïn un conflicte amb cap altre programa (que no intentin fer servir el mateix), que els tinguis redirigits al router cap al teu pc i oberts al tallafocs (de tenir-ne).

I, torracastanyes, no hi ha ports més segurs que altres. Tots són portes obertes al món.

---

### Post by lluisalguero on 2007-12-03
> **papapep said:**
> Lluís, de ports pots fer servir els que vulguis (només són una convenció) sempre que no creïn un conflicte amb cap altre programa (que no intentin fer servir el mateix), que els tinguis redirigits al router cap al teu pc i oberts al tallafocs (de tenir-ne).

I, torracastanyes, no hi ha ports més segurs que altres. Tots són portes obertes al món.

Només ho he dit per informació, ja que normalment els que venen per defecte al amule, estàn sobresturats.

---

### Post by papapep on 2007-12-03
Crec que estàs barrejant conceptes. Independentment del port que tinguis tu assignat a l'amule, accedeixes als mateixos servidors en les mateixes condicions. No millora ni empitjora el rendiment el port que facis servir, és només una convenció que tu empres arbitràriament. La única condició per a que et funcioni correctament és que tinguis els ports redirigits al router i se t'assigni una ID alta.

---

### Post by torracastanyes on 2007-12-03
Gràcies, papapep.

Potser el terme "seguretat" no és el més adient, en aquest cas. 

Em refería al fet que no tots els ports es poden utilitzar per a qualsevol cosa.

Per exemple, (ho dic de memòria, així que pot ballar algun número)  del 0 al 99 estan reservats al sistema i no els pot utilitzar l'usuari, del 99 al 1024, en ubuntu i altres linux, estan reservats per a root, i hi ha programes, com amule, que utilitzen determinats ports per defecte que convé evitar, be per problemes de saturació, com diu en Lluís, o bé perquè alguns proveïdors puguin restringir-los, a més dels conflictes que pot crear tenir instalats diferents programes que treballin amb els mateixos ports.

Aquí hi ha una llista orientativa:
 
[http://www.adslzone.net/puertos_orden.html](http://www.adslzone.net/puertos_orden.html)

---

### Post by papapep on 2007-12-03
> Em refería al fet que no tots els ports es poden utilitzar per a qualsevol cosa.

Si que es pot. Ningú t'obliga a fer servir un port específic per un servei concret. Són només convencions que ens ajuden a no haver de mirar on tenim el mysql, el postgresql, el pop3, el smtp o el ssh, per exemple, cada cop que toquem una màquina (dels jocs no en tinc idea, parlo de servidors).

Res t'impideix canviar-ho. Una altra cosa és que sigui sensat o no fer-ho per altres qüestions tècniques derivades. ;-)

---

### Post by kukat on 2007-12-03
Jo vaig obrir els ports del meu router posant la meva direcció IP (per a saber-la ifconfig a la consola), en el firefox, i així et surt la pantalla de configuració del router. Modifiques l'entrada NAPT i li afegeixes els ports de l'emule, i ja els tens oberts.  Busca per la xarxa informació més concreta però és una cosa així. 

I el que anava a dir: Una vegada tingues els ports oberts i no tingues el firewall vigila dues coses: Que la teva direcció no acabe en 0, ja que l'amule li asigna una ID baixa a eixies direccions. Tan sols tens que apagar el router i tornar-lo a encendre ( no sol passar) i també tindre en compte que quan més arxius compartixques, més ràpid t'anirà. 

Salut!

---

### Post by Curial on 2007-12-03
De moment sembla que no tinc cap tallafocs activat.

Respecte al router ja miraré la informació que meu passat.

Moltes gràcies a tots.

---

### Post by torracastanyes on 2007-12-03
[QUOTE=Res t'impideix canviar-ho. Una altra cosa és que sigui sensat o no fer-ho per altres qüestions tècniques derivades. ;-)[/QUOTE]

Ara l'has dit!

Són precisament aquestes qüestions sobrevingudes les que fan que els usuaris "de a peu" passem díes trencant-nos la closca per resoldre un petit problema com aquest.

---

