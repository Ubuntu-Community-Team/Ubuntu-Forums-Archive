---
title: "Ubuntu 8,10 una mica estrany"
date: 2008-11-20
forum: Catalan Team
---

### Post by lFossil on 2008-11-20
Hola, acavo d'instal·lar el nou ubuntu des de zero però no hi porta el compiz i els temes que venen són una mica arcaics i per exemple trobo a faltar "l'ubuntu studio", estic segur que deu faltar alguna cosa per instal·lar, he estat buscant, però no hr trobat res, a algú li ha passat alguna cosa semblant?

---

### Post by Daerun on 2008-11-20
El compiz mai ha vingut de sèrie amb l'Ubuntu, que jo sàpiga... De la resta, com que m'he quedat amb el 8.04, no sabria dir-te, però de sempre que els temes predetermintas de l'Ubuntu han sigut lletjos :roll:

---

### Post by PatrickVogeli on 2008-11-20
estas segur de que la versio que has instal·lat es la final???

Respecte a l'ubuntu studio, que vols dir que el trobes a faltar? Si no m'equivoco, te repositoris propis amb algunes coses especifiques.

EDITO: estas segur de que no porta el compiz? Posa en terminal compiz --replace, que et surt?

---

### Post by oriolsbd on 2008-11-21
Jo diria que el Compiz, sí que ve de sèrie, però no ve activat, perquè s'ha d'activar l'acceleració gràfica de la targeta de vídeo.

Si dius que no et ve instal·lat, i que els temes són arcaics (no sé ben bé a què et refereixes amb això) pot ser que hagis instal·lat una versió antiga de Ubuntu en comptes de la 8.10? O el que diu el Patrick, que no sigui una versió alfa.

---

### Post by lFossil on 2008-11-21
Doncs no ho sé, l'unic que vaig fer va ser descarregar desde la pàgina oficial l'ubuntu 8.10 i instal·lar-lo, com puc saber si és una versió alfa?

Quan dic que trobo a falta l'ubuntu studio i que els temes són arcaics, em refereixo a temes més moderns i atractius com ara l'ubuntu studio que crec que hauria de venir per defecte (almenys amb el 8.04 manava).

El que em diu quan poso compiz--replace és:

 jasiel@jasiel-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048 ): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by climent on 2008-11-21
Que jo sàpiga, l'Ubuntu Studio és una variació de l'Ubuntu stàndard en la que s'hi han afegit diferents programes específics de l'àrea multimèdia, i que no ve "de sèrie" sinó que cal descarregar-lo a banda. De fet, quan parlem de "Intrepid Ibex" només ens podem referir a Ubuntu a seques. L'Ubuntu Studio no diu "intrepid" i sí 8.10
Quant al compiz, sí que ve de sèrie, el que cal instal·lar és el compizconfig-settings-manager, amb el terminal o el synaptic, que permet obrir les opcions d'efectes d'escriptori.
Si més no, és el que jo faig quan instal·lo una nova versió.

---

### Post by SiscoGarcia on 2008-11-21
Si vols els extres que aporta l'ubuntu studio només cal que el busquis a Synaptic (o adept, si fas anar kubuntu) o per terminal. Si ho fas pel synaptic podràs triar quins components concrets vols instal·lar-te, jo ho vaig fer no fa gaire i va força bé.

---

### Post by PatrickVogeli on 2008-11-22
Tens el compiz instal·lat, el que passa es que no tens activada l'acceleració gràfica. Quina tarjeta tens?

Temes arcaics.. ens pots enganxar una captura de pantalla del tema que et va deixar la instal·lació per a que ho veiem?

T'ho tornem a dir: de l'Ubuntustudio, mai ha vingut res de serie. Pots instal·lar el tema de l'ubuntustudio fent sudo apt-get install ubuntustudio-look

---

### Post by lFossil on 2008-11-22
Bé ja he fet tot el que m'haveu dit, moltes gràcies a tots!!

---

