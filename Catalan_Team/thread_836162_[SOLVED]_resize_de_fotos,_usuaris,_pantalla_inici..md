---
title: "[SOLVED] resize de fotos, usuaris, pantalla inici."
date: 2008-06-21
forum: Catalan Team
---

### Post by grundt on 2008-06-21
Bé tinc tres dubtes,

1.-Sabeu d'algun programa per agafar moltes fotos i canviar-ne el pes?

2.-Una vegada vaig haver de crear dos usuaris i ara els vull borrar,
    però la carpeta d'aquests usuaris porta un candau, com ho faig?

3.-Quan inicio l'ordinador em dona la possibilitat d'entrar en windows xp
   o en ubuntu, el problema  és que cada cop la llista d'ubuntu es més llarga, i jo només necessito l'ultima versió. Com puc esborrar les altres?

---

### Post by CarlesOriol on 2008-06-21
Al fòrum tenim un lema:

Una pregunta = un fil.

Et responc la primera i et prego separis les altres en fils diferents.

Per tal de treballar amb imatges des de la linea de comandes hi ha eines collonudes com imagemagick.

Una de les funcions que proveeix és convert. Aquesta ens permet fer un munt de conversions i filtres a imatges.

El que ara ens interesa és:

convert -scale 400 imatge_entrada.png imatge_sortida.jpg

Aquest exemple ens escala la imatge proporcionalment a un ample de 400 pixels i ens canvia el format de png a jpg.

Ara sols ens cal un iterador d’arxius d’un directori. Per això utilitzarem find.

La sintaxis serà: find *quecerco* -exec comandaaexecutar {} (l’arxiu trobat es substitueix per {}) \; (impotant no deixar-se \; al final de la linea)

find *.png -exec convert -scale 400 {} surt{} \;

---

### Post by grundt on 2008-06-21
Ok,
he mirat al synaptic, i em diu que el tinc instalat
però no el se trobar al menu d'aplicacions.

---

### Post by RainCT on 2008-06-21
He contestat la segona pregunta (directoris amb cadenat) [aquí](http://ubuntuforums.org/showthread.php?p=5232188) i la tercera (treure els nuclis antics de la pantalla d'inici) [aquí](http://ubuntuforums.org/showthread.php?t=836259).

---

### Post by pespin on 2008-06-21
No el trobaràs ja que no és una aplicació gràfica.

Has d'executar-lo des de la terminal com diu en CarlesOriol.

---

### Post by RainCT on 2008-06-21
> **grundt said:**
> Ok,
he mirat al synaptic, i em diu que el tinc instalat
però no el se trobar al menu d'aplicacions.

El que t'ha explicat el Carles no és un programa gràfic sinó l'ús conjunt de dos programes en mode text que es poden utilitzar a la terminal.

Per a fer la conversió que ha posat com a exemple, ves a Sistema -> Accessoris -> Terminal i allà escriu «cd "directori/on/estiguin/les/imatges/"», prem enter, i tot seguit escriu el que t'ha indicat («find *.png -exec convert -scale 400 {} surt{} \;»). Si vols conèixer més opcions que pots utilitzar amb la comanda (així és com s'anomenen els programes a la terminal) convert escriu «man convert» i t'apareixerà la documentació (per sortir-ne prem «q»).

Per a entendre millor tot això et recomano la lectura d'[aquest gran document](https://wiki.ubuntu.com/JosepS%C3%A0nchez/documentaci%C3%B3/interpret_comandes) que ha traduït en papapep.

---

### Post by RainCT on 2008-06-21
Si només vols canviar les imatges de mida (sense canviar el format ni res més) pots fer-ho d'una manera gràfica que et serà més fàcil. Per a això, insta&#320;la el paquet «nautilus-image-converter» des del Synaptic (Sistema -> Aplicacions -> Gestor de paquets Synaptic), torna a iniciar el navegador de fitxers (per a això prem Alt+F2, escriu «killall nautilus» a la finestra que surt i prem «executa», o bé simplement tanca la sessió i torna-hi a entrar) i llavors si se&#320;leciones les imatges que vols i fas clic amb el dret del ratolí t'apareixerà l'opció «Resize Images...».

**Nota:** Acabo de traduir el nautilus-image-converter (la traducció estarà disponible a l'Intrepid d'aquí a poc). Aviso per si a algú altre se li acudeix fer el mateix.

---

### Post by orestesmas on 2008-06-21
> **RainCT said:**
> Si només vols canviar les imatges de mida (sense canviar el format ni res més) pots fer-ho d'una manera gràfica que et serà més fàcil.

I si a més de canviar-ne la mida vols fer un munt de coses més amb les imatges, com afegir-hi marcs, canviar-ne el format, aplicar-hi diversos filtres i efectes, reanomenar-les, etc, etc,, tot això per lots i de forma gràfica, aleshores el teu programa és el Digikam amb els endollables "Kipi".

---

### Post by grundt on 2008-06-21
He fet lo del nautilus image converter, era això el que volia, sobretot perque és fàcil.

Jo , la veritat, em fa molt pal haver d'anar escrivint coses a la terminal.

Espero, que en el futur s'hagi d'escriure lo mínim.

He dit una tonteria?

---

### Post by orestesmas on 2008-06-21
> **grundt said:**
> 

Espero, que en el futur s'hagi d'escriure lo mínim.

He dit una tonteria?

Més aviat si :)

---

### Post by CarlesOriol on 2008-06-21
> **grundt said:**
> Jo , la veritat, em fa molt pal haver d'anar escrivint coses a la terminal.

Espero, que en el futur s'hagi d'escriure lo mínim.

Normalment moltes feines es fan més ràpidament escrivint, tot i que requereix una feina adicional d'aprenentatge.

Imagina't un directori amb mil fotos i vols canviar-ne la mida. Tu tens feina de clics per una tarda, jo escric la comanda en segons.

Llavors pots pensar: "algú pot fer un programa per canviar de mida les imatges d'un directori"... però veuràs que a mida que augmentes la complexitat el sistema gràfic per eficiència per la quantitat de menú i opcions que apareixen i al final no saps del cert que va a fer, mentre que la comanda sempre tens el control des del moment que l'has aprés.

---

### Post by grundt on 2008-06-21
Ah.

Bona explicació.

Aviam, jo en aquest cas concret he seleccionat mil fotos li he dit resize amb el click dret,i ja està. El que passa es que triga una miqueta, vols dir que això mateix amb un parell d'ordres t'ho fa a l'instant? perquè ,llavors és un altre tema.

---

### Post by RainCT on 2008-06-21
> **grundt said:**
> El que passa es que triga una miqueta, vols dir que això mateix amb un parell d'ordres t'ho fa a l'instant?

En aquest cas, no, triga el mateix (ja que de fet el que està fent és cridar la mateixa ordre que escriuries a la terminal però embolcallant-ho amb la interfície gràfica).

Per cert, si vols tenir el nautilus-image-converter en català prem Alt+F2 i executa «gksudo "wget [http://utils.eurion.net/hosted/nautilus-image-converter.mo](http://utils.eurion.net/hosted/nautilus-image-converter.mo) -o /tmp/nautilus-image-converter.mo"». Després, reinicia el Nautilus (el gestor de fitxers, com ja he dit abans fent Alt+F2 i «killall nautilus») i et sortirà traduït.

---

