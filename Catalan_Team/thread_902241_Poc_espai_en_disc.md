---
title: "Poc espai en disc"
date: 2008-08-27
forum: Catalan Team
---

### Post by david.rivera on 2008-08-27
Hola a tots, 

Tinc una maquina virtual, vmware, amb ubuntu 7.10 i tinc problemes despai en disc. He intentant esventar aquest problema esborrant el contingun de la carpeta /var/log ja que e contingut d'aquesta era massa, fent això he alliberat molt espai pero m'he trobat que ha deixat de funcionar el mysql. 

Algu hem podria donar una solucio? o dirme algun programa per ampliar l'espai? 

M'ha agradaria a part de una solucio per el poc espai en disc, una altre per el mysql que al iniciar l'ubuntu dona un error ([fail]).

Moltes gracies.

---

### Post by LitusMayol on 2008-08-27
Quan d'espai té el teu disc dur?

Podries mirar-te [aquest tema]("http://ubuntuforums.org/showthread.php?t=896482"), parla de dsitribucions lleugeres de GNU/Linux.  Jo et recomano ***Flux*buntu** i **Damn Small Linux** (aquesta última només necessita 50mb!).

---

### Post by david.rivera on 2008-08-27
> **LitusMayol said:**
> Quan d'espai té el teu disc dur?

Podries mirar-te [aquest tema]("http://ubuntuforums.org/showthread.php?t=896482"), parla de dsitribucions lleugeres de GNU/Linux.  Jo et recomano ***Flux*buntu** i **Damn Small Linux** (aquesta última només necessita 50mb!).

Cambiar de distribucio hem suposaria molts canvis ja que tenim instalat zabbix i mes aplicatius necesaris en l'empresa.

L'espai del disc es de 15gb.

Ampliar el disc dur ens hem donat compte que no es pot perque qui va crear la maquina virtual nomes li va donar de disc dur 16gb y no podem ampliar aquest espai.

Coneixes alguna aplicacio d'ubuntu per alliberar l'espai en disc?

Gracies.

---

### Post by LitusMayol on 2008-08-27
Jo quan anava apurat d'espai vaig trobar [aquest "tutorial"]("http://www.ubuntu-eee.com/index.php5?title=How_to:_free_up_space"), que simplement et diu algunes aplicacions que normalment no s'usen i estan instal·lades. Sinó [aquí]("http://ubuntuforums.org/showthread.php?t=184435") tens uns post de UbuntuForums que parlen d'alliberar espai.

Sinó pots probar de comprar un disc dur (extern o intern) i muntar-lo.

---

### Post by oriolsbd on 2008-08-27
Hola.

Què vas esborrar exactament de /var/log? Només els fitxers o també els subdirectoris? A moltes distribucions, el mysql deixa els seus log a /var/log/mysql, de manera que si esborres aquest subdirectori, el mysql pot ser que no el sàpiga crear per escriure-hi els logs a sota. Crea'l i és possible que et torni a funcionar.

Quant al tema de l'espai en disc, et poden ajudar aquestes comandes:
```
sudo apt-get autoclean
```
Et borrarà els fitxers ".deb" del directori on se'ls desa l'"apt-get" quan els instal·la. Només borra els fitxers ".deb", no desinstal·la els programes, clar. Amb l'opció autoclean només t'esborrarà els .deb d'aquells paquets que ja no es puguin descarregar.

```
sudo apt-get clean
```
Aquest fa el mateix que l'opció anterior, però borrant els fitxers ".deb" de TOTS els paquets (no només dels que ja no es poden descarregar). És per si necessites fer més espai, però no la facis si veus que guanyes espai amb les altres accions.

```
sudo apt-get autoremove
```
Aquest et mira les llibreries que tens instal·lades, però que no utilitza cap programa que tinguis instal·lat. Normalment són llibreries que s'instal·len quan instal·les un programa, però que no es desinstal·len un cop tu el desinstal·les. Jo mai he tingut cap problema, però et recomanaria que si utilitzes aquesta opció t'apuntis els paquets que et desinstal·larà, per si et trobes algun problema.

Salutacions,

Oriol.

---

### Post by papapep on 2008-08-27
Buscant a Google, [m'han sortit moltes referències a com redimensionar el disc d'una MV d'Vmware]("http://www.google.es/search?q=vmware+resize+disk&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:ca:unofficial&client=firefox-a"). Una d'elles és aquesta: [http://www.leonmeijer.nl/archive/2007/05/07/25.aspx](http://www.leonmeijer.nl/archive/2007/05/07/25.aspx). Tot i això, que quedi clar que això queda fora de l'àmbit d'aquest fòrum. 

Per cert, això de carregar-te /var/log sense més NO és cap bona idea, com ja has pogut veure. Et quedes directament sense cap registre del que passa al teu sistema, i qualsevol problema et deixa, bàsicament, en pilotetes. A banda de que hi ha aplicacions que quan detecten que no hi ha fitxers de registre es tanquen en banda, amb bon criteri, i no arrenquen.

---

### Post by david.rivera on 2008-08-27
> **papapep said:**
> Buscant a Google, [m'han sortit moltes referències a com redimensionar el disc d'una MV d'Vmware]("http://www.google.es/search?q=vmware+resize+disk&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:ca:unofficial&client=firefox-a"). Una d'elles és aquesta: [http://www.leonmeijer.nl/archive/2007/05/07/25.aspx](http://www.leonmeijer.nl/archive/2007/05/07/25.aspx). Tot i això, que quedi clar que això queda fora de l'àmbit d'aquest fòrum. 

Per cert, això de carregar-te /var/log sense més NO és cap bona idea, com ja has pogut veure. Et quedes directament sense cap registre del que passa al teu sistema, i qualsevol problema et deixa, bàsicament, en pilotetes. A banda de que hi ha aplicacions que quan detecten que no hi ha fitxers de registre es tanquen en banda, amb bon criteri, i no arrenquen.


Hola de nou, 

Hem ampliat la particio del vmware, pero ara tenim aquesta ampliacio (9gb) sense format, he intentat amb els meu coneixements y utilitzant el gparted intentar extendre la particio /dev/sda1 per aixi aumentar el seu espai, y no hem deixa.
Ara mateix el gparted hem mostra que tinc 4 particions:
/dev/sda1 ext3         --> 15.28 gb
/dev/sda2 extended     --> 729.51 mb
/dev/sda5 linux-swap   --> 729.48 mb
sin asignar            --> 9 gb

Llavors la de sin asignar la vull donar a la ext3 per aixi tindre mes gigas, com es pot fer? 

Gracies

---

### Post by papapep on 2008-08-27
Estàs fent coses molt delicades, ja que pel que dius entenc que la vostra feina depèn en part d'aquesta màquina virtual, i, també pel que tu dius, se t'escapa una mica el tema. Ves amb MOLT de compte.

Si les particions no són consecutives (no són físicament una al costat de l'altre al disc) no les pots "juntar", redimensionar la original amb la de nova creació. Sempre pots fer servir la nova amb un punt de muntatge concret (si, per exemple, on teniu més dades és a /var/log) copiar tot el /var/log a la nova partició, un cop creat i formatat amb el sistema de fitxers que volgueu, i modificar l'fstab a fi de que apunti aquest punt de muntatge a la nova partició. Un cop fet això i ben assegurat que funciona correctament, podrieu esborrar el que hi havia a l'antic espai (molt de compte amb la coincidència de noms al fer la còpia i muntar les particions i demés, que us podeu carregar les dades noves i perdre les antigues si no ho feu bé).

Una altra opció, tal i com us han comentat abans, que segurament seria més profitosa a llarg termini i si teniu la possibilitat tècnica i econòmica, és afegir un disc dur extern i fer-lo servir per afegir-lo a la màquina virtual (molt semblant al tema de la nova partició).

---

### Post by david.rivera on 2008-08-27
Se que es una burrada i segurament es una cosa que no s'hauria de fer, pero... 
Es pot eliminar la particio extended i linux-swap? I despres tornarles a crear, aixi podria ampliar el disc dur primari.

Com ho veieu?

---

### Post by papapep on 2008-08-27
David, fer, es pot fer (gairebé) qualsevol cosa. Ara bé, la qüestió radica en com i de quins mitjans es disposa.
La partició de 9 Gb nova que heu creat, quan de temps us durarà abans d'omplenar-se una altre cop? si no teniu clar això i genereu moltes dades, igual d'aquí dos mesos torneu a estar igual. 

El que vull dir és que si no ens dónes una visió més de conjunt és complicat aconsellar-te.

Quins directoris teniu més carregats?  on se us generen les dades que fan que la MV us quedi petita?

Podeu esborrar aquestes particions que dius (fent un backup prèviament, clar, del que tingueu a l'estesa), i tornar a crear la nova al costat de la de 15 Gb, i un cop remuntat tot plegat tornar a posar les dades de la partició eliminada al punt de l'estructura de directoris que pertoqui. Però la qüestió, quan s'estan administrant sistemes que és del que parles, és que cal veure el conjunt i, aleshores, decidir quina és la millor opció dins les possibles per solucionar el problema i per més endavant. 

Ja sé que parlo molt de teoria, però és que per arreglar-ho com cal, i no tenir problemes en un futur, s'ha d'anar un pèl més enllà quan parlem de sistemes productius. :-)

---

### Post by david.rivera on 2008-08-27
Moltes gracies companys.

El problema del espai en disc ha sigut solucionat fent el que hem indicat abans, tot ha funcionat sense problemes. 

L'unic problema que ens falta per solucionar es el tema el mysql pero creiem que aixo també fallaba abans d'esborrar els fitxers del directori /var/log ja que ho hem restaurat i continua fallant. Mirarem de solucionarlo, si no ho aconseguim demanarem ajuda per aquí.

Gracies un altre cop, i agrair la rapideça.

---

