---
title: "Hola a tothom! ... i primers dubtes"
date: 2008-05-12
forum: Catalan Team
---

### Post by kilian_cuerda on 2008-05-12
Bona nit a tots i totes, sóc Kilian Cuerda, de València, i acabe de començar, pràcticament literalment, amb això d'Ubuntu i Linux. Ja tinc alguns dubtes, i si bé podrien semblar coses extremadament senzilles, necessitaria preguntar. Al começament tenia instal·lada la versió ubuntu 7.10, però fa un parell de dies, em va eixir que es podia actualitzar a 8.04. Des d'aleshores, porte temps intentant instal·lar un .bin, i al fer-li doble click, m'apareix: No s'ha pogut mostrar «/home/toshiba/Escriptori/gvSIG-1_1_1-linux-i586.bin».No hi ha cap aplicació instal·lada per a aquest tipus de fitxer. Tampoc funciona activant la possibilitat de que s'execute com un programa en permisos, ni afegint obre amb pregunta d'execució automàtica. A banda del terminal, ¿què podria fer per a que s'execute amb normalitat qual li faig doble click, com abans d'actualitzar a 8.04? Per altre costat venia a dir el mateix al tractar d'obrir l'accés directe per al programa una vegada instal·lat amb el terminal, fins que un conegut que sap del tema m'ha fet un apanyo amb una llançadora d'aplicacions o alguna cosa així, però em pareix una moguda per a cada vegada que vullga instal·lar alguna cosa semblant. Ah per cert, no puc escriure el signe d'arrova pulsant ctrl+alt i la tecla del 2 a on està l'arrova, sabríeu com solventar-lo? Perdoneu si poden parèixer ximpleries, però estic encara fent els primers passos. Moltes gràcies per la vostra atenció i espere poder contribuir en la mesura del possible. Saluts a tothom.

Kilian.

---

### Post by papapep on 2008-05-12
Benvingut al fòrum, al programari lliure i a la comunitat d'ubuntaires, Kilian!
He llegit els dos posts que has posat, el d'aquest fil i el del de presentació, i crec que has de utilitzar una miqueta més els punts i apart!!!:-) Sinó podem morir ofegats si algun dia et llegim en veu alta ;-)

Respecte els teus problemes, fes a un terminal, si us plau:

```
ls -la /home/toshiba/Escriptori/
```

i enganxa aquí el que et mostri.

---

### Post by kilian_cuerda on 2008-05-12
Jajajjaja, sí, és veritat, crec que m'he habituat massa a escriure parrafades. Això canviarà ipso facto.
Bé, gràcies per la informació, però això seria per a després escriure al terminal (una regió arcana i desconeguda encara per a mi) allò de ./ i el nom del arxiu a executar, no? Crec que bàsicament seria cóm m'ha ajudat a instal·lar el programa un professor de la Universitat, o potser m'estic confonent.  

Per cert, el programa en qüestió és el gvSIG, un sistema d'informació geogràfica prou bó, desenvolupat per la Conselleria d'Infraestructures del País Valencià, i és software lliure, la veritat és que en aquest camp estan portant endavant un interesantíssim projecte: [www.gvsig.gva.es](www.gvsig.gva.es) 

Gràcies, un salut.

Kilian.

---

### Post by kilian_cuerda on 2008-05-12
ok, estic un poc espés ja a aquestes hores, un momentet

---

### Post by kilian_cuerda on 2008-05-12
ok papapep, m'apareix això:

total 44485
drwxr-xr-x  2 toshiba toshiba      128 2008-05-12 20:26 .
drwxr-xr-x 45 toshiba toshiba     1784 2008-05-12 23:11 ..
-rwxrwxrwx  1 toshiba toshiba 45498936 2008-05-11 21:39 gvSIG-1_1_1-linux-i586.bin
-rw-r--r--  1 toshiba toshiba      280 2008-05-12 20:26 gvSIG.sh.desktop

---

### Post by papapep on 2008-05-12
> Bé, gràcies per la informació, però això seria per a després escriure al terminal (una regió arcana i desconeguda encara per a mi) allò de ./ i el nom del arxiu a executar, no? Crec que bàsicament seria cóm m'ha ajudat a instal·lar el programa un professor de la Universitat, o potser m'estic confonent.

Bé, les ordres de terminal ho són TOT en els Unix/Linux. Són com realment funciona el sistema. La resta (tota la parafernàlia gràfica) símplement no funcionaria sense això.
El que et demano és que llistis els permisos dels fitxers que tens a l'escriptori per poder veure quins possibles problemes hi tens que no te'l deixa executar.

Per cert, si no ho has fet ja, sempre és interessant que els nouvinguts feu un acurat cop d'ull al fil creat just per a vosaltres ;-)

[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

---

### Post by papapep on 2008-05-13
Doncs, ara fes a un terminal:

```
chmod +x /home/toshiba/Escriptori/gvSIG.sh.desktop
```

i torna a provar a executar la icona del gvSIG amb el doble clic del ratolí.

---

### Post by orestesmas on 2008-05-13
Amb ànim de ser didàctic (tot i que el Pep ja ho és prou), l'ordre que et fa posar, "ls -la /home/toshiba/Escriptori" fa el següent:

"ls" significa "list", i serveix per obtenir un llistat de tots els fitxers d'un directori, en aquest cas el /home/toshiba/Escriptori

"-la" són unes opcions que se li passen a l'ordre "ls" i que modifiquen una mica el seu comportament. En aquest cas la "l" és per fer un llistat "llarg", que inclogui permisos, i la "a" per tal que llisti "tots" els fitxers, àdhuc els ocults (que comencen per un punt).

I finalment comentar que tota la informació dels diferents usuaris es posa sota el directori /home. Cada usuari té un directori i, ves per on, tu has escollit dir-te "toshiba". Dins d'aquest /home/toshiba hi ha diverses subcarpetes, i "Escriptori" és allí on hi guarda els fitxers que apareixen a l'escriptori.

Finalment el que et proposa el Pep és canviar els permisos d'un accés directe (el fitxer gvSIG.sh.desktop) per tal que es pugui executar.

Tot això s'hagués pogut fer també des de l'entorn gràfic. El que passa és que en GNU/Linux hi ha més d'un entorn gràfic: Gnome, Xfce, KDE, Enlightenment, WindowMaker... i aquesta riquesa és un inconvenient a l'hora d'ajudar a algú, perquè potser està fent servir un entorn gràfic que no correspon al teu i aleshores les coses no són al mateix lloc.

Per això el terminal és l'element unificador de tots els Linuxaires.

Ens veiem per aquí.

---

### Post by kilian_cuerda on 2008-05-13
Gràcies a tots dos, i saluts. Pel que fa a l'accés directe, sí que funciona a soles, doncs aquest que apareix és el que va crear el professor amb una llançadora d'aplicacions a través de terminal (crec que era així): li done doble click i apareix el terminal amb una bona pluja de lletres i s'executa el programa, l'accés directe que no anava era altre que ja no està. 

El problema és per a executar el .bin, i el mateix passa si em descarregue la nova versió del programa o l'actualització. Imagine que canviant el nom de l'element en qüestió de l'ordre del terminal hauria de funcionar, no?

Ah, per cert... em dic toshiba perquè és el nom que posaren els tècnics al instal·lar-me l'ubuntu... jejeje a veure si el canvie, continua per inèrcia, són aquestes les primeres vegades que estic emprant linux.

---

### Post by SiscoGarcia on 2008-05-14
Estava seguint amb interès aquest fil, i just quan he trobat la següent resposta del papapep:
> El que et demano és que llistis els permisos dels fitxers que tens a l'escriptori per poder veure quins possibles problemes hi tens que no te'l deixa executar.
he pensat que seria molt més didàctic si s'expliqués què vol dir cada ordre que ens demaneu que fem, tot i que sóc conscient que ja feu més que suficient (i prou didàctic també) amb el que feu (gràcies a tots).

Quan m'he trobat la següent resposta de l'Orestes que és just el que estava pensant:

> **orestesmas said:**
> Amb ànim de ser didàctic (tot i que el Pep ja ho és prou), l'ordre que et fa posar, "ls -la /home/toshiba/Escriptori" fa el següent:

"ls" significa "list", i serveix per obtenir un llistat de tots els fitxers d'un directori, en aquest cas el /home/toshiba/Escriptori

"-la" són unes opcions que se li passen a l'ordre "ls" i que modifiquen una mica el seu comportament. En aquest cas la "l" és per fer un llistat "llarg", que inclogui permisos, i la "a" per tal que llisti "tots" els fitxers, àdhuc els ocults (que comencen per un punt).

I finalment comentar que tota la informació dels diferents usuaris es posa sota el directori /home. Cada usuari té un directori i, ves per on, tu has escollit dir-te "toshiba". Dins d'aquest /home/toshiba hi ha diverses subcarpetes, i "Escriptori" és allí on hi guarda els fitxers que apareixen a l'escriptori.

Finalment el que et proposa el Pep és canviar els permisos d'un accés directe (el fitxer gvSIG.sh.desktop) per tal que es pugui executar.

Tot això s'hagués pogut fer també des de l'entorn gràfic. El que passa és que en GNU/Linux hi ha més d'un entorn gràfic: Gnome, Xfce, KDE, Enlightenment, WindowMaker... i aquesta riquesa és un inconvenient a l'hora d'ajudar a algú, perquè potser està fent servir un entorn gràfic que no correspon al teu i aleshores les coses no són al mateix lloc.

Per això el terminal és l'element unificador de tots els Linuxaires.

Ens veiem per aquí.

BRAVO!!!!!!!

---

### Post by papapep on 2008-05-14
> he pensat que seria molt més didàctic si s'expliqués què vol dir cada ordre que ens demaneu que fem,

Sí, seria molt més didàctic, però cal una mica d'esforç per part de l'"ajudat/da". No pretendreu que només treballi una banda, oi? ;-)

Per això mateix, sempre donem referències dels recursos del wiki, poso a la signatura el tutorial de l'intérpret d'ordres, etc...cal una mica d'implicació per part de tots els intervinents.

---

### Post by SiscoGarcia on 2008-05-14
> **papapep said:**
> Sí, seria molt més didàctic, però cal una mica d'esforç per part de l'"ajudat/da". No pretendreu que només treballi una banda, oi? ;-)

Per això mateix, sempre donem referències dels recursos del wiki, poso a la signatura el tutorial de l'intérpret d'ordres, etc...cal una mica d'implicació per part de tots els intervinents.

Evidentment, un no pot ensenyar a qui no ajuda. No demano que ho feu, ja entenc que és una feinada. Només ho dic perquè n'aprendríem més ja que entendríem què és el que estem fent.

Diria que el problema és que fem anar els ordinadors sense coneixements suficients per traginar al nivell que ho fem. A partir d'aquí depèn de les ganes que tinguis per aprendre'n que pots fer-ho millor o no. L'ajuda que ens doneu és molt valuosa.

---

### Post by CarlesOriol on 2008-05-14
Sisco:

sempre pots fer 

**man ordrequeetdiem**

per exemple si fas :

**man ls**

veuras que surt un munt de bona informació.

---

### Post by SiscoGarcia on 2008-05-15
> **CarlesOriol said:**
> Sisco:

sempre pots fer 

**man ordrequeetdiem**

per exemple si fas :

**man ls**

veuras que surt un munt de bona informació.


Diguem que ... "touché".

Merci, això és part del que deia.

---

