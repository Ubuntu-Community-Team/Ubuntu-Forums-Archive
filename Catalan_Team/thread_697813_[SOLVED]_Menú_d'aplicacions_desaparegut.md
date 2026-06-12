---
title: "[SOLVED] Menú d'aplicacions desaparegut"
date: 2008-02-15
forum: Catalan Team
---

### Post by Druiling on 2008-02-15
Hola tothom.
Vaig fer ahir l'actualització a 7.10 i tot correcte. L'únic és que del menú, allà on diu aplicacions, m'ha desaparegut tot el contingut. Clico amb el dret, li dic edita els menus i tinc l'espai d'aplicacions buit (no el puc ni desplegar, abans si però ara no sé què he tocat que no). Miro de passar una captura des de la consola a veure si m'ensurto i em podeu ajudar a recuperar això.
Gràcies.

---

### Post by patrickfromspain on 2008-02-15
has probat a pitjar el boto de Restaura?

salut!

---

### Post by Druiling on 2008-02-15
Bona nit. 
Si, ho he provat. No fa res.
;)

---

### Post by CarlesOriol on 2008-02-15
Prova d'obrir un terminal i fer 

sudo apt-get install ubuntu-desktop

---

### Post by Druiling on 2008-02-16
Hola, aquesta comanda em diu:

maria@maria-laptop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for maria:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
ubuntu-desktop ja es troba en la versió més recent.
The following packages were automatically installed and are no longer required:
  libswfdec0.3 python2.4-minimal libcommons-fileupload-java
  libdirac0c2a hermes1
Use 'apt-get autoremove' to remove them.
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 1 no actualitzats.
maria@maria-laptop:~$

No sé...

---

### Post by Druiling on 2008-02-16
A l'ajut he trobat això:

gnome-app-install

i m'ha donat això:

/usr/lib/python2.5/site-packages/gst-0.10/gst/__init__.py:144
: Warning: cannot register existing type `GstRTPJitterBuffer'
  from _gst import *

(gnome-app-install:14211): GStreamer-CRITICAL **: gst_element
_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' f
ailed
/usr/lib/python2.5/site-packages/gst-0.10/gst/__init__.py:144      : Warning: cannot register existing type `GstRTPBin'
  from _gst import *

(gnome-app-install:14211): GStreamer-CRITICAL **: gst_element      _register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' f      ailed
warning: could not initiate dbus

** (gnome-app-install:14210): WARNING **: return value of cus      tom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:126      1: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_mode      l_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)

crec que hi ha alguna cosa que no està bé.

---

### Post by CarlesOriol on 2008-02-18
Eps... 

Com està el tema. Segueixes igual? 
Has provat si això et succeeix a tots els usuaris de l'ordinador o sols al teu? (si cal crear-ne d'altres fes-ho per provar)

---

### Post by Druiling on 2008-02-18
Hola Carles,
Segueixo igual. 
No tinc més usuaris, però miraré de crear-ne un altre.
Per cert, també tinc instal.lat el KDE i allí tot correcte, però a risc que se m'enfadi algú, de moment, prefereixo Gnome, el trobo més senzill i tothom sap que estic començant...
Provo això que dius i us ho comento.
Gràcies.

---

### Post by Druiling on 2008-02-18
Bé, he creat un altre usuari i seguim igual.
Ara, per acabar-ho d'adobar, em reconeix la xarxa inhalàmbrica, però no es connecta, així que haig d'anar amb KDE.
No sé, potser si això no pita m'ho pensi, però no m'agrada gens donar-me per vençuda...
Salut!

---

### Post by Druiling on 2008-02-24
Ja pita la xarxa, encara que no demana que desbloquis l'anell de claus però això crec que és la versió que ho fa tot sol. Va un pèl més lenta la detecció però, però va.
Em dona la impressió que la pregunta que us faré tot seguit, podria ser per un fil diferent, però estic gairebé segura que té a veure amb el rollo aquest de la desaparició del menú d'aplicacions, i és que si vull posar un fons de pantalla o moure alguna de les configuracions de finestres, colors, fonts, etc, em queden les finestres de l'aplicatiu penjades.
Miro de posar una captura.
Agrairé suggeriments.

---

### Post by dar22442 on 2008-03-15
Hola!
Sóc molt nou amb el tema, i a mi m'ha passat el mateix, al actualitzar a la 7.10 m'ha desaparegut el menú d'aplicacions, ja ho heu pogut solucionar? Alguna idea?

Sóc tan nou que no se ni executar el terminal sense accedir al menú d'aplicacions......:(

Moltes gràcies,

Salutacions,

---

### Post by lluisanunez on 2008-03-15
El menú d'aplicacions potser el pots recuperar simplement clicant al panell amb el botó contrari del ratolí, Afegir > Menú
(és a l'apartat utilitats)

---

### Post by dar22442 on 2008-03-15
Moltes gràcies, però no hi ha cap aplicació per afegir, a part tampoc puc editar els menús, quan ho intento no fa res, surt el rellotge, fa que pensa una mica i després res de res.

A part ara al intentar afegir com tu m'has dit, he tret la barra de a dalt de tot i ja no le se tornar a posar...... que malament que vaig amb això!!!!

---

### Post by lluisanunez on 2008-03-15
Per obrir un terminal, fes Alt+F2 i al camp comanda escriu gnome-terminal  (em sembla que ja et surt allà mateix la icona del terminal)

Un cop al terminal, fes 
```
killal gnome-panel
gnome-panel
``` i recuperaràs el panel

---

### Post by Druiling on 2008-03-28
Hola tothom,

No sé com m'ho he fet, que aquest migdia remenant, he tocat una configuració de la pantalla i tres o quatre coses més i m'he posat al damunt d'Aplicacions i quan m'ha sortit la caixa buida que us ensenyava al principi dels posts, li he dit restaurar (per provar alguna cosa més altre cop) i m'ha tornat a aparèixer, de manera que ja el torno a tenir.
Dar, no sé si això pot servir-te o com està el teu tema.
Em sap molt greu no poder concretar més.
Salutacions.

---

### Post by Druiling on 2008-04-19
No he tancat ja aquest fil per si en Dar havia de fer alguna pregunta més, però ara ja fa molts dies de l'última intervenció.
Podeu comentar-me què és el que soleu fer en un cas així?
Ho dic perquè si cas el podríem tancar, o és millor que no?
Fins ara! :biggrin:

---

### Post by SiscoGarcia on 2008-04-19
Pots tancar-lo (suposo que vols dir marcar-lo com a resolt) i si hi ha algú interessat a reobrir-lo ho pot fer sense cap problema (jo mateix ho he fet algun cop).

---

### Post by Druiling on 2008-04-19
Gràcies company.
Bona nit.

---

### Post by SiscoGarcia on 2008-04-19
De res, companya.

Veus com és possible ;)

Fins l'[HolaHardy]("https://wiki.ubuntu.com/CatalanTeam/HolaHardy?action=show&redirect=CatalanTeam%2FFestaHardy")

---

