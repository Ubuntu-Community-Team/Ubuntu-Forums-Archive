---
title: "Nou SALT 4.0 només per a OpenOffice.org"
date: 2008-09-19
forum: Catalan Team
---

### Post by diafebus on 2008-09-19
[http://www.edu.gva.es/polin/val/salt/apolin_salt4.htm]("http://www.edu.gva.es/polin/val/salt/apolin_salt4.htm")

Instruccions Ubuntu (provat a Ubuntu 8.04 Hardy):
1.- Descarregar versió Linux: [http://www.edu.gva.es/polin/docs/salt4.tgz]("http://www.edu.gva.es/polin/docs/salt4.tgz")
2.- Descomprir l'arxiu (fer doble clic damunt i polsar el botó per a extreure).
3.- Fer doble click damunt dels arxius deb i instal·lar-los en el següent ordre (per a no tindre problemes de dependències):
          salt-common_4.0-1_all.deb
          salt-data_4.0-1_all.deb
          salt-help_4.0-1_all.deb
          salt-server_4.0-1_i386.deb
          salt-ooo-addons_4.0-1_i386.deb
          salt_4.0-1_all.deb
4.- Obrir una terminal des de Aplicacions > Accessoris > Terminal
5.- Fiqueu: sudo /etc/init.d/salt-server start
6.- Podeu tancar la terminal

Ja teniu instal·lat el Salt!!

Ara a la barra de l'OpenOffice teniu 2 menús més: Salt i Utilitats del Salt. Per a traduir un text, seleccioneu-ho i trieu en el menú Salt l'opció adient. També inclou corrector (encara que el del OpenOffice.org és també útil).

El salt-server s'instal·la com a servei. Cada vegada que inicieu l'Ubuntu, s'engegarà per defecte.

---

### Post by lo gambusí on 2008-09-19
Genial! :)

---

### Post by kukat on 2008-09-19
Gràcies! a Ubuntu Gutsy Gibbon també funciona!!

---

### Post by SiscoGarcia on 2008-09-19
Només espere que la llengua estiga d'acord amb les Normes de Castelló del 32 ;)

---

### Post by tanreb20 on 2008-09-19
I per AMD64 de on el trec?

---

### Post by jaume69 on 2008-09-21
Doncs funciona!!,llàstima que no sigui en Català Universal,però és igual, que tampoc hi ha moltes variacions.

**Sort** de gent com aquesta que encara treballa pels demés.

Gràcies.

Salut.

---

### Post by CORRALET on 2008-10-01
Algú sap si hi ha la versió per amd64, Gràcies

---

### Post by SiscoGarcia on 2008-10-02
> **jaume69 said:**
> Doncs funciona!!,llàstima que no sigui en Català Universal,però és igual, que tampoc hi ha moltes variacions.


Quin és el català universal? Crec que el valencià (entès com la variant del català parlada al País Valencià) mentre s'adapti a les [Normes de Castelló]("http://ca.wikipedia.org/wiki/Normes_de_Castell%C3%B3") ja és prou universal, ja que aquestes normes segueixen les que va "dictar" [Pompeu Fabra]("http://ca.wikipedia.org/wiki/Pompeu_Fabra") per tal de normativitzar el català.

---

### Post by jaume69 on 2008-10-02
No sé jo...,si sé que el Valencià és la variant que menys variants semàntiques te envers del Català "diguem" barceloní.

Crec que BCN,Girona,Tarragona,son les ciutats que més s'assemblen al Català Stardard,amb petites variacions.

Però també penso que tan el Mallorquí com Aranès,Lleidatà,Valencià,etc..,també es poden posar com a Llengües Standars.

Pot ser lo més normal fora que decidissin com a Català Standard o Universal,el que en més extenses regions s'hi parli.

No sé...
Vaia lio...

__________________________________
Visca Catalunya,els països Catalans i tots els Catalans.I els altres..!!
:D

---

### Post by CORRALET on 2008-10-03
Al Pais Valencià diem: "qui no té faena Déu li'n dóna"
I em sembla que això estem fent ací a tot l'ambit de la Llengua Catalana o Llengua catalana-valenciana tant se'n val.
El que passa i el que volen els qui volen  que la nostra llengua desaparegua, per exemple, del País Valencià és que ens maregem en històries del nom, de la tipologia (normativització més correcte) del que parlem al país.
Algú s'imagina una discussió de si l'andaluç és la llengua estandard o el murcià, o el castella-manxec, o perquè no el mexicà; ells ho tenen clar: TOT ÉS VALID. Ho van acceptant i fent la llengua gran al contrari que nosaltres: L'AVL discrimina aquelles paraules que no s'usen al País Valencià.
Per tant cal un Instituto Cervantes i una Real Academia Española de la lengua a la catalano-valenciano-mallorquina

---

### Post by jaume69 on 2008-10-03
Jo dic que cadascú parli en la seva Regió com li agradi o li plagui,és el nostre dret.

El que jo deia avans és que aplicant la reunificació de Llengües-Dialectes catalans seria més simplificador i alleugerit per per exemple;tràmits o processos administratius,etc..,crec...

---

### Post by jraulbc on 2008-10-04
:) Em sembla que us heu errat de forum! [www.valencianisme.com](www.valencianisme.com)

---

### Post by martimcfly on 2009-04-26
Problemes de compatibilitat entre el salt 4.0 i openoffice 3.0.

Després d'instal·lar els paquets de salt i obrir l'openoffice, apareixen els menús correctament, però no funcionen.
Al seleccionar el text i clicar en "traducció", no tradueix res. Al fer clic en diccionari tampoc pasa res.
Sembla un problema d'incompatibilitat amb openoffice 3.0. Encara no he sigut capaç d'instal·lar la 2.4 (el paquets .deb ja no estan disponibles en openoffice.org)

Ara mateix tinc el Jaunty 9.04.

Algú amb el mateix problema?

---

### Post by Jpedros2 on 2009-04-26
Hola martimcfly, amb Jaunty tampoc no em funciona el Salt.
No és (crec) un problema de la versió d'OO:
en Hardy jo feia servir la versió 3 i crec recordar que em funcionava.

En tot cas el que et puc confirmar és que sota Jaunty, al meu equip no corre.
Salutacions cordials.
--
Jesús

---

### Post by chaumo on 2010-02-02
Hola, 

Yo he tenido problemas al instalarlo en Ubuntu 9.10 por las dependencias (pide python 2.5 y no acepta la python 2.6 que viene con la Karmic), no sé si en la 9.04 también pasará.

También he visto que el servidor intenta arrancar usando python 2.5 y si no existe falla. 
En mi caso lo he solucionado parcheando el .deb para que acepte versiones superiores a la 2.5. al instalar y cambiando el server para que busque python2 (cualquier versión).

He colgado la solución y el .deb parcheado en [mi web]("http://www.ruizarjona.com/especiales/tips-tools/linux-ubuntu/instalar-salt-4-ubuntu-910-solucion-problemas") , y les he enviado un mail para que lo corrijan o lo tengan en cuenta en futuras versiones.

Espero sirva de ayuda.

---

### Post by ximoberna on 2010-02-05
Totalment d'acord amb Corralet!
:popcorn:

---

### Post by socderafel on 2010-02-06
No liem la marrana, que estes discursions al final se'n van de les mans...
PD: m'ha fet molta gràcia el post escrit en castellà ... amb un parell d'ous amic!!!! jajajajaj!!!

---

### Post by chaumo on 2010-02-11
qué he de fer? tanta discussió que si valencià que si català... doncs jo en castellà, que a més em trobe més cómode :p a qui no li agrade que no em llisca.

---

### Post by SiscoGarcia on 2010-02-11
> **chaumo said:**
> doncs jo en castellà, que a més em trobe més cómode :p a qui no li agrade que no em llisca.

chaumo, recorda que estàs escrivint al fòrum en català. Per tant no es tracta d'agradar o no, ni de comoditat. Simplement és així, hi ha altres llocs on pots escriure en castellà, però ací no.

---

### Post by datunie on 2010-02-13
He provat d'instal·lar Salt i no funciona en un amd64. Supose que està pensat per a lliurex, que només té versió i386.

---

### Post by chaumo on 2010-02-15
> **SiscoGarcia said:**
> chaumo, recorda que estàs escrivint al fòrum en català. Per tant no es tracta d'agradar o no, ni de comoditat. Simplement és així, hi ha altres llocs on pots escriure en castellà, però ací no.

No crec que un usuari de Madrid tinga problemes amb la instal·lació de Salt perquè dubte molt que l'utilitze, la meua intenció és ajudar. 

I veig més correcte escriure en castellà sense faltes que en català amb elles...qüestió de falta pràctica supose. Que la pràctica s'agafa escrivint ja ho sé, així que tampoc vull entrar en això perquè no cree que siga l'objecte d'aquest fòrum. 

Demane disculpes.

---

### Post by SiscoGarcia on 2010-02-15
> **chaumo said:**
> No crec que un usuari de Madrid tinga problemes amb la instal·lació de Salt perquè dubte molt que l'utilitze,

Això no ho pots saber. HI ha ubuntaires en català pels [llocs més inversemblants]("http://www.ubuntu.cat/mapa_ubuntaires") :o

> **chaumo said:**
>  la meua intenció és ajudar. 

Això és el que ens uneix.


> **chaumo said:**
> I veig més correcte escriure en castellà sense faltes que en català amb elles...qüestió de falta pràctica supose. Que la pràctica s'agafa escrivint ja ho sé, així que tampoc vull entrar en això perquè no cree que siga l'objecte d'aquest fòrum. 

En aquest punt discrepem, perquè es tracta del fòrum d'usuaris d'ubuntu **en català**, la resta no importa.

> **chaumo said:**
> Demane disculpes.

Disculpat! Tant de bo tothom que discrepa tingués aquesta actitud conciliadora ;)

---

### Post by tonisilves on 2010-05-13
Tot torna a començar. No puc instal·lar Salt 4 al Lucid Lynx. Ajuda!

---

