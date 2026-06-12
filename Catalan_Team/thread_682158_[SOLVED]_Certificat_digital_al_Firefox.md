---
title: "[SOLVED] Certificat digital al Firefox"
date: 2008-01-29
forum: Catalan Team
---

### Post by lpargemi on 2008-01-29
Hola

Aquesta és la tercera entrega del serial...

Va del següent: Jo tinc un certificat digital de l'FNMT per identificar-me amb hisenda.

El certificat el tinc instal.lat al firefox, i reconegut per aquest com a tal.

El problema és que quan vull demanar o entregar documents a hisenda, no me l'admeten i em surt el pop-up que us adjunto, on hi diu que no ha colat.

El curiós és que el mateix certificat, en W$, només cola des de l'explorer. Amb firefox per W$ també passava el mateix.

Com puc saber si el problema és meu (del tàndem ubuntu-firefox) o és del servidor d'hisenda?

Sabeu d'alguna pàgina on em pugui identificar amb aquesta mena de certificat per descartar-ho?

Agraït

Lluís

---

### Post by Tomàs M. on 2008-01-30
> **lpargemi said:**
> Hola



El curiós és que el mateix certificat, en W$, només cola des de l'explorer. Amb firefox per W$ també passava el mateix.



En la meva vida anterior de zombi windosejat també em va passar, i algú em va comentar que perquè funcionés amb el Firefox se li havia de posar contrassenya mestra (edita-preferències-seguretat).
De tota manera, ho acabo de provar (sense aquesta opció activada) i estic veient el meu darrer model 100 sense problemes, o sigui que no sé pas quin pot ser el problema. Per si ho vols mirar, tinc marcat "Quan un lloc web necessiti un certificat: Selecciona'n un automàticament" a Avançat-Xifratge.

Sort!

---

### Post by papapep on 2008-01-30
Lluís, pot ser que no hagis descarregat, i instal·lat, el certificat arrel de la FNMT al firefox?

Per si no ho has fet, [aquí]("http://www.cert.fnmt.es/content/pages_std/certificados/FNMTClase2CA.cer") tens l'enllaç.
Quan l'instal·lis (Edita > Preferències > Avançat > Xifratge > Certificats > Visualitza els certificats > Importa) li has de donar autorització per a tot (les tres caselles que et surten al diàleg de importació.

Jo tornaria a importar el teu certificat personal i a veure si ara funciona.

---

### Post by bratac on 2008-01-31
Bones,

jo tinc un altre dubte relacionat. No sé si ho hauria de penjar aquí o no, en qualsevol cas, aquí el deixe i si convé ja faré una entrada nova.

Jo em vaig fer el certificat digital de la generalitat aquest estiu, en principi me'l vaig instal·lar bé (però no en vaig canviar la contrasenya) Posteriorment vaig haver de formatar el disc i vaig deixar el tema oblidat. 

Puc fer que el mateix certificat torni a funcionar o he de començar de nou? Vull dir baixar-me el certificat al firefox, anar a demanar un certificat nou, fer la instal·lació i tot això?

Com ho he de fer per a que funcioni?

Proposo fer un apartat del wiki només pel tema certificat digital, amb explicacions i tota la punyeta, crec que interessa i cada cop serà més necessari.

gràcies,

---

### Post by papapep on 2008-01-31
Doncs si tens una còpia de seguretat del certificat només l'has d'importar al nou navegador i punt. Si no la tens, has de revocar primer l'inicial i després tornar a començar el procés.

> Proposo fer un apartat del wiki només pel tema certificat digital, amb explicacions i tota la punyeta, crec que interessa i cada cop serà més necessari.


Tot teu el wiki. En tot cas, podriem mirar de quina altra pàgina hauria de penjar, però ets lliure per editar-lo (com tothom).

---

### Post by lpargemi on 2008-01-31
Hola

He seguit fent proves i m'he trobat amb el següent: El certificat que tinc instal.lat al firefox, davant d'hisenda, em permet identificar-me (i veure les meves dades fiscals disponibles, per exemple), però no em permet signar: És quan vull signar una petició o l'enviament de les dades quan m'apareix el pop-up que citava uns missatges abans.

Això em fa pensar que no sigui un parany dels javascript de la pàgina, que solen anar diferent per l'Explorer (que no compleix l'estandard) de la resta del mon mundial.

Una altra possibilitat és que al certificat, als camps que mostra a la taula del firefox, hi consta com a <desconegut> el camp "Finalitats" [Edita> Preferències >Avançat> Xifratge >Visualitza  els certificats]. A més d'un missatge críptic on diu que* els certificats no han estat validats amb OCSP* si he escollit aquesta opció a [Edita> Preferències >Avançat> Xifratge >verificació]. Potser no és normal aquest comportament amb els certificats FNMT i per això no acaba d'anar bé?

---

### Post by orestesmas on 2008-01-31
A mi també em surt això del OCSP i en canvi el certificat em va bé.

Tens més d'un certificat en el sistema? Si és així digues-li al navegador que no esculli el certificat automàticament (altrament pot ser que acabi escollint-ne un que no va bé),

---

### Post by CarlesOriol on 2008-02-01
Algú ha dit KDE en aquest fil??

:-D

---

### Post by lpargemi on 2008-09-29
Hola!

Ara que s'obre el plaç, fins al dia 20, per enviar les declaracions d'IVA, reprenc aquest tema: Segueixo sense poder enviar les declaracions des de Ubuntu. A final cada vegada he d'anar al costat fosc, i a més fer-hi servir el més tèrbol dels programes MSIE.

El cas és que des de la pàgina de la FNMT - l'emissor del certificat- em comproven el certificat i em diuen que és correcte, però a l'hora de signar gestions amb hisenda em segueix sortint la finestreta del primer text del post.

Algú pot fer gestions amb hisenda amb el certificat de la FNMT i firefox? Com teniu configurat el certificat?

Dades addicionals.

Jo el tinc donat d'alta a la pestanya "Your Certificates", i FNMT aparareix a la llista de Authorities.

Tinc triat a Preferències>avançat>xifratge les opcions SSL3.0, TLS1.0 (que no sé què volen dir) i que em demani cada vegada quin certificat vull fer servir

El resultat és el mateix independentment de l'opció que triï a PreferènciesAavançat>xifratge>Validació en relació al OCSP. 

Agraït de nou

Lluís

---

### Post by Tomàs M. on 2008-09-30
Mira't l'últim paràgraf de [http://www.tomi.cat/2008/05/com-fer-la-renda-amb-ubuntu.html](http://www.tomi.cat/2008/05/com-fer-la-renda-amb-ubuntu.html)

Sort!

---

### Post by lpargemi on 2008-10-01
Tomàs, gràcies, però malgrat tenir el certificat donat d'alta com a entitat, tampoc va. Em segueix donant la mateixa errada.

Salut

lluís

---

### Post by Tomàs M. on 2008-10-02
Doncs si el que et vas baixar és el que hi ha a [http://www.cert.fnmt.es/content/pages_std/certificados/FNMTClase2CA.cer](http://www.cert.fnmt.es/content/pages_std/certificados/FNMTClase2CA.cer) i en importar vas marcar les 3 finalitats, ja no en sé més :confused:

---

### Post by lpargemi on 2008-10-02
Hola Tomàs

Ara ja em funciona. 

Jo només havia importat el meu certificat d'usuari a la pestanya "Your Certificates". Després, fent proves també l'havia importat a la pestanya Servers 

No tenia el certificat d'arrel que es baixa de la pàgina de la FNMT que tu indiques al post anterior:

> Doncs si el que et vas baixar és el que hi ha a [http://www.cert.fnmt.es/content/page...MTClase2CA.cer](http://www.cert.fnmt.es/content/page...MTClase2CA.cer) i en importar vas marcar les 3 finalitats, ja no en sé més

Quan l'he descarregat no l'he pogut instal.lar a "Authorithies" perquè tenia els invents de proves anteriors a "Servers". Borrant els certificats de FNMT que havia importat a "Servers" i instal.lant el del teu enllaç a "authorities" ha funcionat bé

Molt Agraït

Lluís

---

