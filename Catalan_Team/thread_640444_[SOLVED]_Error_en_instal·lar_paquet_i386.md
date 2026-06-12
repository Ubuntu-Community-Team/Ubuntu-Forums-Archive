---
title: "[SOLVED] Error en instal·lar paquet i386"
date: 2007-12-14
forum: Catalan Team
---

### Post by Joan Marc on 2007-12-14
Hola,
Em podríeu explicar què siguifica aquest número i386?
He buscat a la wikipèdia, i he entès que era un dels primers Intel que va sortir, o alguna cosa per l'estil.
El cas és que he intentat instal·lar aplicacions i jocs, i em diu el següent (captura adjunta), i no em deixa instal·lar-ho.

Salut!

---

### Post by eduardsola on 2007-12-14
La i386 és l'arquitectura per defecte dels processadors Intel, la que fan servir el Pentium 4, el core i algun més.

---

### Post by papapep on 2007-12-14
Més concretament, i386 significa que les instruccions dels processadors (Pentium, Pentium II, etc.. fins els actuals Centrino i Pentium IV) són compatibles amb els antics 386, successor del 286 i predecessor del 486.

L'error potser bé per què intentes instal·lar paquets per a màquines amb 
processador compatible amb 386 (de 32 bits) a una màquina amb processador de 64 bits?? Quin processador té el teu ordinador?

---

### Post by Joan Marc on 2007-12-14
Suposo que és Intel Centrino Duo (Core 2 Duo inside)

---

### Post by pespin on 2007-12-14
Jo et recomanaria instal·lar els jocs mitjançant aptitude o Synaptic, i no baixant-he els debs per separat com sembla que fas. Suposo que aquests programes sabran triar els paquets adients al teu processador :)

---

### Post by Joan Marc on 2007-12-14
> **pespin said:**
> Jo et recomanaria instal·lar els jocs mitjançant aptitude o Synaptic, i no baixant-he els debs per separat com sembla que fas...

La veritat és que no sé fer anar el Synaptic... A part d'això, quan obro el Gestor de paquets Synaptic em surt un problema (adjunt), faig el que em diu desde el terminal, i em diu que necessito permisso de superusuari... No sé per què però l'Ubuntu em dona molts errors...:(

---

### Post by papapep on 2007-12-14
Afegeix "sudo" al davant de la ordre et cal fer el següent:

```
sudo dpkg --configure -a
```

I no és que et dóni errors, és que ets molt novell ;-)

Una pregunta, no estaràs fent servir l'Automàtix per a instal·lar controladors i demés, oi???

---

### Post by Joan Marc on 2007-12-14
> **papapep said:**
> Afegeix "sudo" al davant de la ordre et cal fer el següent:

```
sudo dpkg --configure -a
```
He afegit sudo davant i el terminal no fa res:
```
gami@Gami:~$ sudo dpkg --configure -a
gami@Gami:~$ 
```


> **papapep said:**
> Una pregunta, no estaràs fent servir l'Automàtix per a instal·lar controladors i demés, oi???
Suposo que no... ja que no sé ni què és...

---

### Post by eduardsola on 2007-12-14
Quan posis sudo davant el comado que executis, automàticament després et demana la contrasenya d'administrador. Tu la poses, però no surt a la terminal.

---

### Post by Joan Marc on 2007-12-14
Tampoc, la posu i no fa res...
Ara ja ni em diu que necessito permissos de superusuari

---

### Post by Joan Marc on 2007-12-14
Bé, se m'acaben d'instal·lar uns actualitzacions de Java, no sé si és gràcies a elles, però el Synaptic ja torna a funcionar.
El que continua sense funcioanar es alhora d'instalar coses, continua sortinr el missatge d'error.
Algú sap s'algun manual facilet d'entendre del Synaptic¿?

Gràcies ;)

---

### Post by papapep on 2007-12-14
Joan Marc: Que no et mostri cap missatge al terminal no significa que la ordre no faci la seva feina.
I no, el java no té a veure amb que et funcioni el Synaptic.
Jo, fins que solucionis el tema dels paquets (l'error que et dóna) passaria del Synaptic.

Et dóna exactament el mateix missatge d'error??

Prova a fer a un terminal:

```
sudo apt-get update
```

---

### Post by Joan Marc on 2007-12-14
Sí, en dóna el mateix error...

He posat el que m'has dit al terminal, t'escric el que surt:
```
gami@Gami:~$ sudo apt-get update
[sudo] password for gami:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-ca
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-ca
Des:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/restricted Translation-ca        
Des:2 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-ca    
Ign http://archive.ubuntu.com gutsy-updates/main Translation-ca          
Ign http://security.ubuntu.com gutsy-security/main Translation-ca        
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-ca  
Obj http://security.ubuntu.com gutsy-security Release                    
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-ca    
Des:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                 
Obj http://archive.ubuntu.com gutsy/universe Translation-ca              
Ign http://archive.ubuntu.com gutsy/multiverse Translation-ca            
Obj http://archive.ubuntu.com gutsy/main Translation-ca                  
Ign http://archive.ubuntu.com gutsy/restricted Translation-ca            
Obj http://security.ubuntu.com gutsy-security/restricted Packages        
Obj http://archive.ubuntu.com gutsy-updates Release                      
Obj http://security.ubuntu.com gutsy-security/main Packages                    
Obj http://security.ubuntu.com gutsy-security/multiverse Packages        
Obj http://archive.ubuntu.com gutsy Release                              
Obj http://archive.ubuntu.com gutsy-updates/restricted Packages
Obj http://archive.ubuntu.com gutsy-updates/main Packages
Obj http://archive.ubuntu.com gutsy-updates/multiverse Packages
Obj http://archive.ubuntu.com gutsy/universe Packages
Obj http://archive.ubuntu.com gutsy/multiverse Packages
Obj http://archive.ubuntu.com gutsy/main Packages
Obj http://archive.ubuntu.com gutsy/restricted Packages
3B descarregats en 0s (4B/s)          
E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gami@Gami:~$ 

```

Merci.

---

### Post by papapep on 2007-12-14
> E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Aquí t'està donant la raó de l'error. Només pot accedir un programa simultàniament a la base de paquets. 
O sigui, que quan executis la ordre assegura't de no tenir el Synaptic obert.

---

### Post by Joan Marc on 2007-12-15
Es veritat, ara que l'he tancat el procés segueix bé, i s'acaba amb el seguent:
```
S'està llegint la llista de paquets... Fet
```

Però l'error de " Wrong architecture 'i386' " persisteix.

Salut.

---

### Post by papapep on 2007-12-15
```
sudo aptitude install wormux
```

Tal i com t'ha dit abans en RainCT, instal·lar paquets sense utilitzar el sistema "de sèrie" de Ubuntu té efectes col·laterals no desitjats quan no es controla el que es fa.

---

### Post by Joan Marc on 2007-12-15
papapep gràcies per dirme com isntal·lar el joc, però m'agradaria saber què he de fer quan em trobo amb un cas així, ja que tinc d'altres .deb que també em dónen aquest error.
A part de que si em baixo el .tar, no sé pas com l'he d'instal·lar.

Gràcies ;)

---

### Post by papapep on 2007-12-15
El problema que tens és en que no deus haver triat la versió de paquet correcte, símplement.
La pregunta seria més aviat si has d'instal·lar aquests .deb o tar.gz o si et sortirà més a compte mirar de trobar els paquets als repositoris oficials.
A partir d'aquí, la teva pregunta no té una única resposta, ni fàcil, ja que depèn del que hagi fet la gent que ha creat el paquet.

---

### Post by Joan Marc on 2007-12-15
Tens raó, per exemple m'he fixat que del wormux em puc baixar la versió de 64 bits, i aquesta em funciona correctament, però suposo que no tots els paquets tindran aquesta opció...

Els repositoris oficials et refereixes al Synaptic?

Gràcies:)

---

### Post by papapep on 2007-12-15
El Synaptic és un dels programes, de fet és una interfície que utilitza per sota d'altres programes, que consulta els repositoris oficials per obtenir el programari.

Si consultes el següent enllaç trobaràs una mica d'explicació del tema:

[https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/PMF_UbuntuCat#head-b7e5ceba616b6f421f25ba225501c05e20c46def](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/PMF_UbuntuCat#head-b7e5ceba616b6f421f25ba225501c05e20c46def)

---

### Post by Joan Marc on 2007-12-15
```
Què és un dipòsit (repositori) de programari?
És un servidor d'on es pot descarregar programari amb les eines habituals d'Ubuntu en el format de paquets .deb. N'hi ha d'oficials, en els quals es pot estar segur de que els paquets, la seva integritat i les seves dependències han estat verificats. També n'hi ha de no oficials, els quals no ofereixen cap garantia de que no portin problemes al vostre sistema

```

Diu que hi ha servidors oficials i no oficials, però no diu quins.

També he vist en altres posts, que deixeu l'aptitude bastant malament... És aconsellable baixar-me per exemple del dpkg (que es qualifica com "la mare dels ous") o millor fer-ho amb el synaptic?

Gràcies ;)

---

### Post by papapep on 2007-12-15
D'oficials n'hi ha uns quants (fes a un terminal "cat /etc/apt/sources.list" i en veuràs uns quants), i de no-oficials n'hi pot haver tants com la gent vulgui. Però clar, no ofereixen, de sortida, cap garantia de que no et fotin el sistema enlaire.
Respecte l'aptitude, doncs no sé d'on has tret aquesta mala sensació, però no és correcta.
Fes-ho amb el que vulguis instal·lar paquets: Synaptic, Adept, apt-get, aptitude...etc. Pensa que tots fan servir el dpkg per sota (no cal que el baixis, sinó el tinguessis ja instal·lat de sortida no podries fer gairebé res).

---

### Post by Joan Marc on 2007-12-15
Perdó, he confós l'aptitude amb l'Automàtix...

Bé, gràcies per tot, ara mateix marco el post com a Resolt :lolflag:

---

