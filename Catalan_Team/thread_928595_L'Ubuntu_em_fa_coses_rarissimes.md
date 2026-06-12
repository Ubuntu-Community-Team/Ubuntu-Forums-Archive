---
title: "L'Ubuntu em fa coses rarissimes"
date: 2008-09-24
forum: Catalan Team
---

### Post by MiquelBLL on 2008-09-24
Des que vaig instal.lar el 8.04 que tinc problemes, de sobte i en cualsevol aplicacio pero sobretot miran videos en cualsevol dels programa, amarok vlc totem smplayer que el sistema s'em queda congelat, de vegades son uns pocs segons, altres algun minut i d'altres el tinc que apagar cansat d'esperar. I lo d'ahir ja va ser rarissim. resulta que a la carpeta on tenia alguna pel.licula i algun video cuan l'obria no em sortia res i al cap de poc s'em tornava en blanc i negre, despres vaig poder accedir-hi cambian a las preferencies a la finestra de gestio de fitxers i fen que el comportamenr fos que no -obris sempre en finestres del navegador-, pero si tornava a posar-ho en tornava a fer el mateix.Ho he solucionat esborran aquesta carpeta i restauran.la d'una copia que tinc en un disc extern, pero m'ha fotut molt aixo. I lo altre tambe molt extrany que no m'habia passat mai es que de sobte vaig a buscar una cosa a google i poso la paraula al lloc per buscarla  i en lloc de les lletres corresponent en surten altres coses, per exemple escribia la "p" i em sortia "-", tambe em feia el mateix escribin al terminal. Al reiniciar de moment no ho a fet mes
Estic molt confus, no he fet res extrany que jo sapiga, l´unic es posar uns altres repositoris que he trobat per veurer si s´em solucionava lo de les penjades, i si s´hem van actualitzar algunes  coses que no se m´actualitzaben pero res mes.
Estic desitjan que surti ja la 8.10 i veurer si s´arregla, ja dic amb la 7.04 i 7.10 no es penjaba mai, tan sols el firefox 2 de vegades miran videos pero el sistema anaba be. No se si algu li ha passat alguna cosa similar i ho ha pogut sol.lucionar. Gracies

---

### Post by CarlesOriol on 2008-09-28
No sembla un problema que se't vagi a solucionar amb un canvi de versió.

Sembla un error en algun dels suports d'emmagatzenament que tens muntats.

Comprova els hdd, cds (dvds) , pendrives i connexions de xarxa.

També pots fer:

**sudo dmesg -c**

per netejar l'històric de missatges del sistema

i un cop t'hagi succeit una aturada curta un:

**dmesg**

per veure si t'està avisant d'algun error

---

### Post by MiquelBLL on 2008-09-28
Vols dir que tinc un error al disc dur? Una vegada em va donar un error pero ell mateix em va dir que executes un comando, ara no recordo quin per solucionar-ho i es va solucionar. Tinc tambe una SD de 4 gigas posada sempre i el cd-dvd es nou doncs cuan lo del disc dur s´em va espatllar i m´en va posar un de nou. No tinc cap xarxa. Pero ja et dic no em diu que tingui cap error al disc dur. Tinc tambe instal.lat a una particio el vista i cap error.

---

### Post by MiquelBLL on 2008-09-29
El comando en qüestió es el ´fsck´, si ho faig en un terminal en diu lo següent: 

miquel@miquel-laptop:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=55cc47d9-8cd8-455e-ac03-c0ba3f009eac'
miquel@miquel-laptop:~$ 

em sembla que alguna cosa no deu estar be....
lo de les lletres que em sortien era degut a que habia pulsat lo de num LK i amb lo dels nervis per lo del error a la carpeta de video no m´en vaig donar conte.

---

### Post by papapep on 2008-09-29
No intentis fer un fsck d'un sistema de fitxers muntat (o sigui, amb l'ordinador funcionant i el sistema de fitxers accessible), que t'ho pots carregar tot. Fes-ho o des d'un live-cd o entrant en mode single i desmuntant els disc o partició que et dóna problemes (per la segona cal més experiència).
També estaria bé veure el contingut del teu /etc/fstab, ja que sembla que no acabi d'estar bé. Has afegit o modificat la configuració dels discs durs últimament? o insta&#322;lat algun programa per a fer-ho?

---

### Post by MiquelBLL on 2008-09-29
Hola gracies. Aixo del fsck ho vaig tenir que fer una vegada, al arrencar l´ordinador em va sortir aquesta opcio, em deia que tenia que fer-ho per que hi habia un error i es va arreglar, pero va ser en el moment d´engegar. Crec quew va ser d´una pujada de corrent, ara tinc un protector de pujades de corrent suposo alguna cosa fara. 
No he modificat res dels disc durs, no tinc prous coneixements encara que mi esforço i ja no vaig tan peix com cuan vaig començar am el 7.04.
On dius em surt aixó:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=55cc47d9-8cd8-455e-ac03-c0ba3f009eac /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=847b1869-16b2-48b4-9999-865473bc1105 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Mirare de fer lo del live-cd que en tinc un amb el 8.04.

---

### Post by papapep on 2008-09-29
> Aixo del fsck ho vaig tenir que fer una vegada, al arrencar l´ordinador em va sortir aquesta opcio, em deia que tenia que fer-ho per que hi habia un error i es va arreglar, pero va ser en el moment d´engegar

Efectivament, en arrencar, Gnu/Linux fa unes verificacions del sistema de fitxers que, si detecten algun error, et proposen arreglar-ho abans de patir mals majors.

> fsck.ext3: **Unable to resolve** 'UUID=55cc47d9-8cd8-455e-ac03-c0ba3f009eac'

Hauries de verificar que l'UUID que tens al /etc/fstab per la partició /dev/sda2 és correcte. Fes a un terminal:

```
vol_id /dev/sda2
```

busques la línia **ID_FS_UUID=** i comproves caràcter a caràcter que és idèntic al que posa al fstab per a la partició /dev/sda2.

---

### Post by MiquelBLL on 2008-09-30
Hola. Veig que si que son els mateixos caracters, aqui ho enganxo. Lo de la carpeta de videos que no podia obrir no m´habia passat mai, lo de que es queda congelat em passa des de la 8.04 com he comentat sobre tot fen anar el Firefox o cualsevol reproductor de video.
Aqui t´ho enganxo:


miquel@miquel-laptop:~$ sudo vol_id /dev/sda2
[sudo] password for miquel: 
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=55cc47d9-8cd8-455e-ac03-c0ba3f009eac
ID_FS_UUID_ENC=55cc47d9-8cd8-455e-ac03-c0ba3f009eac
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
miquel@miquel-laptop:~$

---

### Post by jaume69 on 2008-09-30
A mi també em passa amb **Firefox**,quan veig un video o entro a una plana que hi ha videos,s'em tanca directament,algunes vegades,no sempre.

No l'he iniciat al Terminal però segur que em diu "**Fallo de Fragmentación**".

Que hi farem...,ja no m'hi emprenyo pas,"per no tenir dues feines".....

Amb videos meus,al reproduir-los,no tinc cap problema.
_____________________________

Ves que sigui algun problema amb la gràfica o el controlador,**lo teu**.

:o

---

### Post by MiquelBLL on 2008-10-01
Hola. Es el que penso que podia ser, alguna cosa de la grafica, els ajustaments o el driver de la Nvidia.

---

### Post by catximba on 2008-10-02
a mi també se'm penja, sobretot quan acabe d'iniciar el sistema per primer cop en diverses hores.

i en qüestió del Firefox, si tinc carregant més d'una pestanya, o si restaure sessió se'm tanca sol, sense arribar a carregar la pàgina o a mig-carregar.

no sé què em pot passar, ja que just abans d'iniciar la meva aventura amb Ubuntu vaig formatar bé i completament el disc dur amb el mateix cd d'Ubuntu.

resulta que des que he fet unes quantes actualitzacions al sistema cada cop m'ha anat pitjor amb certs programes, com el Firefox 3, o amb l'Amarok.

---

### Post by jaume69 on 2008-10-02
[QUOTE="catximba"]i en qüestió del Firefox, si tinc carregant més d'una pestanya, o si restaure sessió se'm tanca sol, sense arribar a carregar la pàgina o a mig-carregar.
[/QUOTE]

A mi em passa el mateix quan les planes web que veig son de vídeos.
Em sembla que amb els de YouTube,i algun altre no em passa.En cara que si en la plana que vull veure hi ha 3 o 4 videos de YouTube i algun altre,llavors si.

No he provat instal.lar **Adove Flash Player** de la web,perquè m'imagino els resultats..
(Si algun dia em "pica",ho faré.:))

Salut.

---

### Post by MiquelBLL on 2008-10-05
Hola. Lo de que algun programa es tanqui sol em passa com per exemple trian una resol.lucio de pantalla molt gran, no ho accepta i es tanca, pero no es penja el sistema. El Firefox3 no s´em penja gaire be mai, alguna vegada tinc que forçar a tancar pero poques vegades, lo extrany es que en el meu cas passi que es queda el ratoli congelat i no es pot fer res, ja dic sobre tot miran videos pero de vegades sense forçar la maquina gens.Esepro que la nova versio funcioni be del tot.

---

### Post by orestesmas on 2008-10-06
A banda d'això que et diuen del disc dur, mira de desactivar els efectes d'escriptori en cas que els tinguéssis, tot i que segons el que dius la gràfica és vellota i segurament no els suportarà.

---

### Post by MiquelBLL on 2008-10-06
Hola. Hui, sense els efectes d´escritori deixo l´informatica, pero no es aixo, ja els vaig desactivar i feia el mateix, cuan li donava la gana es quedava congelat, a mes, ja te dic que amb el 7.04 i 7.10 m´anava be el Beryl. Tinc una GeForce 6100 i els efectes funcionen perfectament, va ser una de les coses de triar Linux i Ubuntu, si no ara tindria segurament un iMac, tenia i tinc encara un Amiga, fins l´any passat el vaig fer servir i encara el toco de tant en tant. Per cert es una pregunta que tinc que fer el con configurar el e-uae.

---

