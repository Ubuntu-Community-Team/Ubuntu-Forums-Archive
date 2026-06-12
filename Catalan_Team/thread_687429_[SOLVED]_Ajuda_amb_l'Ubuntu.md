---
title: "[SOLVED] Ajuda amb l'Ubuntu"
date: 2008-02-04
forum: Catalan Team
---

### Post by autista on 2008-02-04
Hola a tothom,
em dic autista i vos expose la meua situació a veure si algú em pot ajudar.
NO TINC NI IDEA DE COM FUNCIONA L'UBUNTUUUU!!!!
Tinc a casa un pc amb el windows xp, amb connexió a internet per Wi-Fi, i un altre pc amb l'ubuntu instal·lat nou de trinca (tot just el vaig instal·lar ahir).
El que voldria és poder compartir arxius i connexió a internet  entre els dos pcs. He llegit per internet que cal un cable cross-over per connectar dos pcs directament, així que me n'he fet amb un. Ara el problema és que no sé seguir... :-(

ALGÚ EM POT AJUDAR???

gràcies anticipades

---

### Post by papapep on 2008-02-04
Benvingut/da al fòrum (estaria bé que passesis pel fil de presentació a fer-nos cinc cèntims de qui ets),

Primer: Crec que t'aniria bé llegir el fil que hi ha a la capçalera del fòrum que es diu "Llegir abans de continuar".

També crec que seria bo "diseccionar" el teu problema en problemes petits, per que si no, no ens ho menjarem.

Segon: si vols connectar els dos pc's t'aconsello fervorosament comprar-te un switch que et costarà poca cosa i menys i connectar els pc's amb cable convencional. Després ja veurem com fer-ho a nivell de programari.

Tercer: Quina connexió tens a internet? Em refereixo a si tens un router ethernet o usb o un módem, etc...tens el router lluny i els dos pc's aprop l'un de l'altre? o tens opció a connectar-te directament al router però només té un port ethernet???

---

### Post by CarlesOriol on 2008-02-04
Jo també m'hi apunto.

Primer: Crec que t'aniria bé llegir el fil que hi ha a la capçalera del fòrum que es diu "Llegir abans de continuar". :-P

Segon: Amb un cable cross-over ja vas bé.

Tercer: La configuració del pc en windows per compartir la connexió d'internet... es tema per un altre fòrum.  Però si vols t'ajudem a exorcitzar el dimoni de l'altre ordinador. En linux és molt fàcil. :-)

També és important que et presentis com diu en Josep per què la forma com algú et pot explicar com compartir arxius entre els ordinadors és molt diferent depenent dels coneixements que tinguis.

---

### Post by autista on 2008-02-04
heheheeh gràcies, ara ja em vaig enterant una mica com funciona. 
ara he canviat la connexió a internet del xp a l'ubuntu i m'he baixat una nova versió del samba, perquè la que em venia ja en la distribució no em deixava compartir (em deia que no estava instal·lat).

Ara m'agradaria saber com faig per treure la contrasenya que em demana quan intente entrar des de l'xp i com fer per tindre internet compartit. Ah, tinc un trasto USB WiFi que es connecta a un router ADSL (per si serveix d'alguna cosa)

quina alegria, estic escrivint açò amb l'ubuntu!!!

gràcies.

---

### Post by lluisalguero on 2008-02-04
Pot ser vaig errat en el plantejament pero t'explico com ho tinc jo.

Tinc 2 pc's, un amb XP i l'altre amb l'ubuntu. L'XP el tinc connectat mitjançant cable al router i l'Ubuntu via WIFI al router també.

Fes servir un cable tal i com ho dius tu per fer anar l'ubuntu connectat a l'XP per a que et faci de pasarel·la, no crec que sigui la forma més cómoda i eficaç, però això t'ho diràn els companys papapep i Carles Oriol...ells ho toquen tot bé (ja us pasaré l'adreça per a que m'envieu els pernils :lolflag:)

---

### Post by CarlesOriol on 2008-02-04
Collonut... has fet el PITJOR que es pot fer. Sobreescriure un paquet dels repositoris per un d'extern, encara que sigui de l'upstream.

Explica exactament que has fet.

---

### Post by autista on 2008-02-04
ui ui ui
el que he fet ha estat seguir les instruccions del company que em va recomanar l'ubuntu, hem escrit uns comandos o no sé què i llavors ha tret el samba que no funcionava, hem posat una cosa que es connectava a internet per buscar packages i ha trobat un de samba 3.0.26a i l'he posat, tot seguit s'ha obert una finestreta que deia Samba i he posat a compartir una carpeta que he fet amb un arxiu a dins, per veure si es podia vore amb l'XP, i si, anava bé, no m'ha tornat a sortir la finestreta que em deia que instal·lés SMB o una altra cosa...
crec que no he fet res malament, oi mestre?

---

### Post by papapep on 2008-02-04
Ostres autista, cal que siguis un pèl més explícit, sinó no podem saber què has fet i a quin punt ets.

A banda de que et funcioni bé o no, cal saber què has fet realment, per valorar si el que has fet feia falta o no. T'ho dic a efectes de que no només et funcioni sinó que sàpigues el perquè, pel proper cop que et passi alguna cosa semblant. ;-)
Posan's aquí quines ordres has fet servir, si us plau.

---

### Post by autista on 2008-02-04
hehehehehe, OK intentaré reproduir tot allò que he fet.
Primer de tot he buscat al ggole informació sobre connectar un pc windows amb un ubuntu, llavors he entrat en un tutorial, i el que deia era molt fàcil, anar a sistema > administració > carpetes compartides i allà anar afegint les carpetes per compartir. El primer problema, quan entrava en Carpetes compartides em sortia una pantalleta que deia que havia d'instal·lar uns paquets de SMB (xarxes windows) o una altra cosa que era per unix, bé, jo he deseleccionat la de l'unix, com deia el tutorial i llavors li he donat a OK, aquesta pantalla ha desparegut durant uns segons i ha tornat a apareixer. Per molt que donava a OK o seleccionés una o altra opció el resultat era el mateix, despareixia i apareixia als pocs segons.
Llavors he buscat al google la frase que em deia aquesta finestreta (sharing services not installed) i m'ha sortit que a la gent també li passava. Llavors he dit: descarregue el Samba aquest i solucionat. He entrat a la web oficial i m'he baixat l'ultima versió que hi havia, la 3.0.28 crec, i com no sé instal·lar ni res no m'ha servit de res. Tot seguit m'he posat a inspeccionar els directoris, i en un he trobat un How to i m'he possat a llegir-lo. He vist que posava Obtaining and installing samba, però deia que busquesis al manual del teu SO. 
He tornat a internet a la recerca de com instal·lar el samba aquest,
He trobat un lloc on deia que havies d'escriure:

sudo aptitude install samba samba-client smbfs

pero no anava, em deia que (açò ja ho estava copiant tot per ensenyar-li al company)

S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
Reading extended state information      
Initializing package states... Fet
Building tag database... Fet      
No candidate version found for samba
No candidate version found for smbfs
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Fet
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet           
Reading extended state information      
Initializing package states... Fet
Building tag database... Fet

i no feia res, seguia igual
després m'ha dit que provés a desintal·lar-lo i tornar-lo a posar, això és el que he posat:


~$ sudo apt-get remove samba samba-client smbfs
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
El paquet samba no està instal·lat, així que no s'eliminarà
Nota: s'està seleccionant smbclient en comptes de samba-client
El paquet smbfs no està instal·lat, així que no s'eliminarà
S'ELIMINARAN els següents paquets:
  smbclient ubuntu-desktop
0 actualitzats, 0 nous a instal·lar, 2 a eliminar i 0 no actualitzats.
Es necessita obtenir 0B d'arxius.
Després de desempaquetar s'alliberaran 12,6MB d'espai en disc.
Voleu continuar [S/n]? s
(S'està llegint la base de dades ... hi ha 88931 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant ubuntu-desktop ...
S'està desinstal·lant smbclient ...

i amb aixo crec que s'ha tret. A continuació m'he passat una bona estona per intentar posar el samba 3.0.28 aquest però no hi havia manera.

Al final m'he fartat i me n'he anat a sopar, i quan he tornat he agafat i he connectat el pc amb ubuntu a internet directament, llavors he anat a Add/Remove applications i m'ha dit d'ctualitzar la llista, un cop fet, he buscat el samba dels ous i l'he trobat (el 3.0.26a crec), li he dit d'instal·lar i al poc temps ja ho tenia, s'ha obert una finestreta que es deia samba i he afegit una carpeta amb un arxiu per veure si es veia des del pc windows, i voilà. 
Ara tinc la connexió a internet amb l'ubuntu i està en xarxa local amb el XP, però el que voldria és tindre internet als dos (sense gastar diners xDDD) i que quan intente entrar alñs compartits des de l'XP no em demani contrasenya (que per cert no sé quina és).

Bé, espere que açò us sigui d'ajuda per intentar esbrinar què dimonis he fet.

Moltes gràcies per intentar ajudar-me...
està molt bé l'ubuntu... però hauria de ser una mica més senzill perquè tothom pugui adaptar-se i oblidar les pantalles blaves.

un salut

---

### Post by CarlesOriol on 2008-02-05
La contrasenya la generes fent

**smbpasswd  **

i l'escrius pel teu usuari.

El samba 3.0.26a és correcte. L'altre si saps programar i et vols dedicar a aplicar tots els pedaços d'ubuntu abans de la sortida del Hardy també.

---

### Post by autista on 2008-02-05
llavors tot està correcte? mare meua quin esglai

moltes gràcies per tot!!!!

---

