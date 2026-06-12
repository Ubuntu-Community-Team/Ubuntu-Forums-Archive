---
title: "[SOLVED] MLDonkey: fer-lo funcionar i/o reinstalar-lo"
date: 2008-02-18
forum: Catalan Team
---

### Post by almogabber on 2008-02-18
Tenia el programa en qüestió instal·lat, i anava bé, però ara, després d'actualitzar, em demana el nom d'usuari i la contrasenya, i tot i que la poso bé, no en vol.

Una de dos: voldria saber com accedir per canviar la contrassenya (em diu que entri a Settings -> GUI -> GUI server) o bé per desinstal·lar-lo.
He provat de fer-ho tant per la terminal, com pel synaptic. Amb la terminal em donava error, i amb el synaptic no: tornava a reinstalar-lo (un cop desinstal·lat) i res..

Per això he pensat en no complicar-me amb les contrasenyes, eliminar-lo de cap i de nou i tornar-lo a carregar, que tampoc vaig tenir masses problemes el primer cop..

Gràcies! Visca la Terra!!

---

### Post by papapep on 2008-02-18
Per carregar-te un programa amb els fitxers de configuració inclosos:

```
sudo aptitude purge nom_del_programa
```

---

### Post by almogabber on 2008-02-19
Me l'he carregat, com dius, i ha quedat tot ben net. Però extranyament, el torno a instal·lar de nou, i em torna a dir que el password està malament.. (i encara no he tingut temps de canviar el que hi ha per defecte! :confused: )

Alguna idea de perquè pot ser?? (tinc el mateix problema tant amb la interfície gràfica com entrant pel localhost)

---

### Post by papapep on 2008-02-19
Quina ha estat la ordre exacta que has executat i els missatges que has rebut?

---

### Post by almogabber on 2008-02-19
Doncs, **sudo aptitude purge mldonkey-sever**, id esprés el mateix, però amb el **mldonkey-gui**.
Efectivament, estava desinstal·lat, ja que no apareixia no a la llista d'aplicacions i al synaptic estava marcat com a  no instal·lat.

I llavors, ja que era al synaptic, l'he torant a instal·lar: baixar els paquets... tot autompatic.

És un xic llarg, però enganxaré els processos del terminal:
> almogaver@almogaver-linux:~$ sudo aptitude purge mldonkey-server
[sudo] password for almogaver:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 
Els paquets següents no s'utilitzen i se suprimiran:
  ecj ecj-gcj libecj-java libecj-java-gcj 
Els paquets següents se suprimiran:
  mldonkey-server{p} 
0 paquets actualitzats, 0 instal·lats, 5 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'alliberaran 16,0MB.
Esteu segur de voler continuar? [Y/n/?] y
S'està escrivint la informació d'estat estesa... Fet
(S'està llegint la base de dades ... hi ha 126439 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant ecj-gcj ...
S'està desinstal·lant ecj ...
S'està desinstal·lant libecj-java-gcj ...
S'està desinstal·lant libecj-java ...
(S'està llegint la base de dades ... hi ha 126418 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant mldonkey-server ...
Stopping MLDonkey: mlnet.
S'estan purgant els fitxers de configuració de mldonkey-server ...
Not removing MLDonkey directory (/var/lib/mldonkey, /var/run/mldonkey), user and group.
Remove it manually if needed.
Not removing MLDonkey directory (/var/lib/mldonkey, /var/run/mldonkey), user and group.
Remove it manually if needed.
dpkg - avís: al desinstal·lar mldonkey-server, el directori «/var/log/mldonkey» no està buit, no s'esborra.
S'està llegint la llista de paquets... Fet           
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 


tot seguit he fet el mateix però amb el mldonkey-gui, com he dit; però no cal pas que ho enganxi oi??

Gràcies per l'ajuda!

---

### Post by papapep on 2008-02-19
Doncs el resultat de la ordre si que cal que l'enganxis.

---

### Post by almogabber on 2008-02-19
Ho deia perquè no hi ha res 'sospitós':
```
almogaver@almogaver-linux:~$ sudo aptitude purge mldonkey-gui
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents se suprimiran:
  mldonkey-gui{p} 
0 paquets actualitzats, 0 instal·lats, 1 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'alliberaran 8212kB.
Esteu segur de voler continuar? [Y/n/?] y
S'està escrivint la informació d'estat estesa... Fet
(S'està llegint la base de dades ... hi ha 126301 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant mldonkey-gui ...
S'estan purgant els fitxers de configuració de mldonkey-gui ...
S'està llegint la llista de paquets... Fet           
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet
```

Un cop fet això, men vaig al synaptic, torno a instal·lar i estem a les mateixes... :)

---

### Post by patrickfromspain on 2008-02-19
proba a fer mv ~/.mldonkey ~/.mldonkey-copia y reinicia el programa. Aixo si, perdras tota la configuracio.

salut!

---

### Post by papapep on 2008-02-19
> Ho deia perquè no hi ha res 'sospitós':

Clar, però tu ho suposes i jo no ho sé, i com que el que t'estic aconsellant sóc jo, necessito tenir la mateixa, o més,  informació que tu per no fer-te fer cap desgràcia sense voler :)

Aleshores, **després** de fer el ja repetit:

```
sudo aptitude purge mldonkey-server mldonkey-gui 
```

fes:

```
sudo rm -r /var/lib/mldonkey
```
```
sudo rm -r /var/run/mldonkey
```
```
sudo rm -r /var/log/mldonkey
```

un cop fet això, fes:

```
sudo aptitude install mldonkey-server mldonkey-gui
```

---

### Post by almogabber on 2008-02-20
Crack!!! Perfecte!

Tot i que comanda ```
sudo rm -r /var/run/mldonkey
``` m'ha donat error diguent que no ha trobat el direcotri... però ho he seguit reinstalant i cap problema. :)

Gràcies de nou!

---

