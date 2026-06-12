---
title: "Configuración modem/router - Connexió ADSL"
date: 2008-05-29
forum: Catalan Team
---

### Post by tacubuntuforums on 2008-05-29
Hola:

Tinc un petit mòdem/router Thomson-SpeedTouch 530 v6 que vaig configurar sense problemes amb DHCP i per connectar-me amb ADSL a wandoo (ara orange).

Pero ara vull fer servir un altre Thomson-SpeedTouch 511 (més gran, amb més connectors al hub) que havia estat configurat per connectar-se a *Telefónica* [COLOR="Red"](correcció: es SpeedTouch 510)[/COLOR]

Porta un CD de configuració per windos i connectar-se a Telefónica amb lo que sembla un protocol PPPoE amb un programet instalat al sistema windos. No cal dir que no hi-ha cap indicació per Linux (segurament entenen que els usuaris de Linux son molt més intel.ligents per no fer servir Windos i potser tenen raó en part) :-)

(Aixó del PPPoE no sé de  que va. M'imagino que fa una trucada telefònica, tipus ppp, per confirmar les dades de l'usuari i "obrir les portes" a la connexió adsl). Amb l'altre módem no sé com funciona tot peò no tinc que apretar cap icono ni llençar cap programet per iniciar la connexió, com es fa amb les connexions ppp.)

Vaig reinicialitzar el mòdem (que vull configurar) i he accedit, per protocol http a l'adreça 10.0.0.138 a les pàgines de configuració.
He canviat les dades que m'ha semblat necesari perquè fes servir DHCP. Ara, al engegar-lo, les 3 llumetes del mòdem es tornen de color verd, tot indicant que el mòdem: ja està engegat, ja te una connexió DSL sincronitzada i ja té una a la LAN.

Així doncs després d'engegar els serveis de xarxa al pc amb la mateixa configuració que faig servir per l'altre mòdem (el petit), em puc comunicar amb el mòdem i les taules d'enrutament em semblem bé al pc i al módem/router, però no puc accedir a internet des del pc i crec que tampoc des de el mòdem. M'he connectat al modem per telnet i allí he llençat pings contra el meu pc i contra altres adreces IP vàlides de fora però només rebo respostes del meu pc.

Alguna idea de que he de fer sense passar pel Windos per configurar-lo ni per fer-lo servir?

Gràcies

---

### Post by jodufi on 2008-05-29
La majoria de routers es poden configurar utilitzant un navegador. Això hauria d'estar explicat en el manual del router.
Normalment la direcció per a entrar al router és 192.168.0.1 i la contrasenya admin, però millor ho mires al manual.

---

### Post by papapep on 2008-05-29
Doncs jo no sóc capaç de trobar informació a internet (el qual és una mala senyal) al respecte d'aquest Thomson-SpeedTouch 511 que dius.
I quan dic que no trobo informació, no em refereixo a sobre com configurar-lo amb Linux, sinó sobre el dispositiu mateix...

---

### Post by tacubuntuforums on 2008-05-29
jodufi:
Puc entrar a les páginesde configuració, tal com explico.

---

### Post by tacubuntuforums on 2008-05-29
Bueno, no crec que el modem sigui tan particular. Es el que donava la Telefónica cap a l'any 2006. He donat el model per ser més precís (mai se sap). La qüestió es una mica més general...què pot passar segons les diferents formes poden existir de connectar-se i com es fa des-de Linux per provar i trobar la solució.

Tinc els manuals però el camí explicat es:
a) instal.lar un programa de configuració a Windows
b) rearrancar windows
c) arrancar un programa (que crec que funciona amb PPPoE) per la connexió ADSL.
d) tot aixó es per connectar-se a Telefónica i no sé com pot variar amb una altre companyia

Se que hi ha gent que es connecta amb ADSL arrancant un programet (com si fes servir ppp), en canvi hi-ha gent que engega l'ordinador i ja está connectat. Aixó queda determinat per les possibilitats del mòdem? depén de la companyia? Qualsevol de les dues les hauria de poder fer amb Linux (la primera ja se qu si)? com?

Com  dic la qüestió es mes general: tinc un proveïdor d'ADSL i un módem amb manual per windos que ja puc entrar a configurar des de Linux. Qué fer ara?

A veure, una cosa que em sembla significativa es que al modem petit, a les págines de configuració diu tipus de connexió PPPoE y PPPoA (en un altre lloc: PPPoE 8.35) + nom usuari + contrasenya); en canvi al modem gran no trobo on ficar aquestes dades que deuen quedar al programet que es llança amb una icona a l'escriptori windos.

---

### Post by papapep on 2008-05-29
Pel que veig estar parlant d'un router ADSL, no d'un mòdem, tot i que encara no sé quin dispositiu és.
Si el que vols és saber con configurar els paràmetres del router ho hauries de consultar o al teu proveïdor o a un fòrum específic del tema.

---

### Post by tacubuntuforums on 2008-05-29
Bueno, es que es casi tots son modem/router/hub. 

[COLOR="Red"]NOTA: Perdó. M'he equivocat, el gran, es THOMSON SpeedTouch 510[/COLOR]

Els paràmetres per connectar-me amb el meu proveïdor els tinc i els puc consultar a la configuració del modem/router petit. El que dic es que les dades que demanen no son iguals en algo que sembla important: el petit te les dades de l'usuari, la contrasenya i que la connexió es PPPoE (no m'havia fixat bé fins ara, però les veig i les puc canviar desde l'accés web), en canvi el gran no: només demana contrasenya per l'accés a les págines de config.
Jo crec que el programa de configuració (per windos) del router gran les demana i les fica fora del router gran en la configuració del programa client ppp que instala amb una icona a l'escriptori del Windos per iniciar la connexió ADSL (però no ho sé, no tinc tanta familiaritat amb aquestes coses..no sé si es qüestió del modem, del Windos, de la companyia o una combinació però alguns sitemes no no requereixen que facis clic en cap icona per iniciar la connexió ADSL)

---

### Post by papapep on 2008-05-29
El petit és un mòdem ADSL, i el 510 és un router. I sí, tot i que "tots són" mòdems, pels routers només et cal la configuració TCP/IP per connectar de la banda de la xarxa interna. En canvi el mòdem demana una configuració com els antics mòdems RTB (el ppp que tu esmentes). Per això, com que el tractament és bastant diferent el primer que cal saber és quin tipus de dispositiu és.

Dit això, i sabent ara ja que és un del nostres arxiconeguts 510, si l'ubuntu accedeix bé al router, si tal i com dius pots entrar al servidor web de configuració, i la resta de paràmetres de la connexió TCP/IP les tens bé, o el router està espatllat, o no tens bé els paràmetres del proveïdor. No hi ha més volta de full.

Si la ip, màscara de subxarxa, pasarel·la i servidors de dns estan bé, que és tot el que et cal per connectar-te, el problema és de la banda d'internet del router (WLAN), no de la teva xarxa. I això, com ja t'he comentat abans, és fora l'àmbit d'aquest fòrum.

---

### Post by tacubuntuforums on 2008-05-29
Doncs el manual i el programa de configuració del "Kit Telefónica"  diu, a tot arreu, a cada página, "módem router".

Els parámetres del proveidor, com explico, els tinc bé però els tinc al cap només. Tal com explico no sé com ficar-los al router gran (al petit ja hi son). Jo crec que el programa de config. per Windos els demana i els fica fora del router, en la configuració del programa ppp que queda insta.lat al Windos.

Bueno, el problema no es de la WLAN. Amb el módem petit funciona perfecte. Es un problema de configuració amb Linux. No ho volia fer, però estic segur de que si faig servir el Kit ADSL de config i connexió funcionará. Per començar  perquè em demana les dades de usuari per accedir al proveidor i des-de Linux com homhe de fer per sustituir aixó?

---

### Post by climent on 2008-05-29
Jo també crec que el tema correspon a un altre fòrum. Tot sovint dono un cop d'ull a [http://www.adslzone.net](http://www.adslzone.net). Allà hi ha força explicacions de modems routers i demés, i pel que fa als Thompson, els reconeix com a fabricats per Alcatel.

---

### Post by tacubuntuforums on 2008-05-29
No sera questió de que a Linux no haig de fer servir un programa per configurar PPPoE?
Si el kit instala el programa WinPoET al windows, què fer amb Linux?

---

### Post by torracastanyes on 2008-05-30
Sembla que aquest router porta l'ISP predefinit al firmware del mateix aparell. Hauríes de mirar si a la pàgina del fabricant n'hi ha algun de neutre i carregar-lo.
He trobat aquest manualet que és per a windows, però que hauría de funcionar igual desde linux, ja que tot el procés es fa desde el mateix aparell, nomes cal indicar-li on es l'arxiu que ha de carregar:

[http://www.adslzone.net/tutorial-7.5.html](http://www.adslzone.net/tutorial-7.5.html)

Mira't això també, per si et pot ajudar:

[http://www.adslzone.net/tutorial-7.6.html](http://www.adslzone.net/tutorial-7.6.html)

---

