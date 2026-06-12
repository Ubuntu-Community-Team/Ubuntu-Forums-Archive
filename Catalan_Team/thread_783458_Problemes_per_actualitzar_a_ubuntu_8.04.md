---
title: "Problemes per actualitzar a ubuntu 8.04"
date: 2008-05-05
forum: Catalan Team
---

### Post by lFossil on 2008-05-05
Hola a tots, ja fa des de que va sortir l'última versió de l'ubuntu, que provo d'instalar-la però sempre em sortia un error.
Vaig esperar-me un teuns fmps seguint recomanació en alguns posts 
(saturació del servidor) però en continuo igual i no sé què pot ser.
Sé que molts heu tingut problemes, algú li ha passat el mateix?
[http://imageshack.us/img/butansn.png](http://imageshack.us/img/butansn.png)
[http://imageshack.us/img/butansn.png](http://imageshack.us/img/butansn.png)

---

### Post by kukat on 2008-05-06
Jo vaig baixar la imatge des d'un server de Portugal el mateix dia que el van traure, i hem va baixar en menys d'un hora.....i la meua connexió no es res de l'altre món...Que et passa exactament? No funciona be el CD? primer comprova si el CD té defectes abans de començar l'insta&#322;lació (tens una opció al menú principal...)

---

### Post by lFossil on 2008-05-06
No no, intento descarregar-m'ho des del gestor d'actualitzacions.

---

### Post by lo gambusí on 2008-05-06
les captures d'imatge que has enllaçat no són les que volies posar (mira-ho tu mateix: entra als enllaços que has posat). digues quin missatge d'error te dóna, o sinó fes una altra captura.:P

---

### Post by pserra on 2008-05-07
Hola   companys,
un parell de dubtes....no tinc ganes d'actualitzar  a la 8.04 perque el meu portàtil te 4 anyets  i penso que ja esta una mica desfassadet, i també després de l'ultima actualització (Gutsy),sembla que va mes lent d'arrancar....bé... però una cosa...si vull que no em surti mes el gestor d'actualitzacions com ho faig? avui tinc 13 actualitzacions que no s'instal·len segurament perque no estic amb la 8.04.
Si penseu que m'equivoco al no actualitzar feu-m'ho saber....

---

### Post by papapep on 2008-05-07
Un nou tema necessita un fil nou.

---

### Post by lFossil on 2008-05-08
Tens raó gambusí, aquí torno a ficar les que eren.
[http://img139.imageshack.us/my.php?image=capturadi2.png](http://img139.imageshack.us/my.php?image=capturadi2.png)
[http://img395.imageshack.us/my.php?image=capturahardyus7.png](http://img395.imageshack.us/my.php?image=capturahardyus7.png)

---

### Post by lFossil on 2008-05-09
> **lFossil said:**
> Tens raó gambusí, aquí torno a ficar les que eren.
[http://img139.imageshack.us/my.php?image=capturadi2.png](http://img139.imageshack.us/my.php?image=capturadi2.png)
[http://img395.imageshack.us/my.php?image=capturahardyus7.png](http://img395.imageshack.us/my.php?image=capturahardyus7.png)

A veure si algú em pot ajudar plis!

---

### Post by lFossil on 2008-05-12
Algú em pot ajudar a actualitzar l'ubuntu???

---

### Post by papapep on 2008-05-12
Enganxa aquí el contingut del fitxer /etc/apt/sources.list, si us plau.

---

### Post by lFossil on 2008-05-13
No em deixa obrir la source list, em surt això:

jasiel@jasiel-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
jasiel@jasiel-laptop:~$

---

### Post by RainCT on 2008-05-13
Escrivint el nom del fitxer i ja està el que estas fent és provar d'executar-lo (cosa que no pots perquè, evidentment, no és executable).

Per veure el fitxer escriu:
```
cat /etc/apt/sources.list
```

O bé ves a /etc/apt des del navegador i fes doble clic al fitxer sources.list perquè se't obri amb el gedit.

---

### Post by lFossil on 2008-05-13
Ara sí:)

jasiel@jasiel-laptop:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted multiverse universe main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted multiverse universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

---

### Post by papapep on 2008-05-13
Fes a un terminal:

```
sudo aptitude update
```

a veure quins missatges et mostra.

---

### Post by lFossil on 2008-05-13
Em surt tota aquesta parrafada en el terminal:


jasiel@jasiel-laptop:~$ sudo aptitude update
[sudo] password for jasiel:
Obté:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-ca  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-ca  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-ca    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-ca        
Obté:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-ca            
Obté:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [51,2kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-ca   
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-ca    
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-ca
Obté:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-ca 
Obté:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-ca
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                      
Obté:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release [58,5kB]   
Obté:7 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [14B]      
Obté:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release [44,0kB]
Obté:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2880B]    
Obté:10 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [64,3kB]    
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                 
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages           
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages               
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                   
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources              
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources              
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Obté:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]
Obté:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages [9936B]     
Obté:13 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [94,7kB]        
Obté:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages [88,1kB]      
Obté:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages [264kB]           
Obté:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources [937B]       
Obté:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources [1881B]
Obté:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources [14,1kB]
Obté:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources [72,6kB]
Obté:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages [30,2kB]
Obté:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages [14B]
Obté:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages [106kB]
Obté:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages [16,7kB]
S'han recollit 924kB en 3s (238kB/s)               
S'està llegint la llista de paquets... Fet

---

### Post by papapep on 2008-05-13
Bé, doncs fins aquí tot bé. Ara fes això:

```
sudo aptitude safe-upgrade
```

Però digues-li que no al que et proposi, és només per veure què et proposa (espero que sigui decent...:-D)

---

### Post by lFossil on 2008-05-13
He he, a veure em fa una proposta...
Aqui tens:

jasiel@jasiel-laptop:~$ sudo aptitude safe-upgrade
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 
Els paquets següents no s'utilitzen i se suprimiran:
  bridge-utils kdebase-bin kdebase-kio-plugins kdesktop libdbus-qt-1-1c2 
  libkonq4 libntfs-3g12 python-qt3 python-sip4 uml-utilities 
Els paquets següents s'actualitzaran:
  libssl0.9.8 openssh-client openssl ssh-askpass-gnome 
4 paquets actualitzats, 0 instal·lats, 10 a suprimir i 0 a no actualitzar.
Es necessita obtenir 4492kB d'arxius. Després del desempaquetat s'alliberaran 33,0MB.
Esteu segur de voler continuar? [Y/n/?] n
Abandona.

---

### Post by papapep on 2008-05-13
Bé, doncs ara ja queda a la teva opció.

Si tornes a fer el:

```
sudo aptitude safe-upgrade
```

tindràs el sistema a punt de caramel per actualitzar versió de Gutsy a Hardy.

Per a fer-ho, fes al terminal:

```
sudo do-release-upgrade

```

Si ho fas, estarà una bona estona calculant, descarregant i actualitzant, o sigui que busca un espai de temps que t'ho permeti. En principi tot ha d'anar igual, o millor, que amb el synaptic que, de fet, és una simple interfície gràfica de les eines de gestió de paquets de l'intèrpret d'ordres.

Ja explicaràs què fas i com t'ha anat!

---

### Post by lFossil on 2008-05-13
D'acord, gràcies, ja et diré.
:)

---

### Post by lFossil on 2008-05-13
Ei, s'ha baixat correctament tot, però després de que s'instalés, l'he reiniciat com em deia, però quan fico el nom d'usuari i la contrasenya, després es queda la pantalla de color negre i  no passa res. No m'entra.

He provat en al principi quan et diu fer ESC i tornar a un moment avans que surten uns quants tipus diferents de ubuntu 7,10 però no e aconseguit res.

Ai mare què he fet :icon_frown: :confused:

---

### Post by papapep on 2008-05-13
Res de l'altre món, segur. Segurament problema del controlador de la placa gràfica. Quina tens? Si no ho saps, fes:

```
lspci |grep Display
```

i enganxa el resultat.

---

### Post by lFossil on 2008-05-14
On u fico aixo? No m'entra a l'escritori!

---

### Post by papapep on 2008-05-14
Fes Ctrl+Alt+F1 i aniràs a un terminal.

---

### Post by lFossil on 2008-05-14
sí, ja em surt però no sé com posar aquesta barra entre mig perquè ho estic llegint des d'un altre ordinador.
em diu login incorrect

---

### Post by papapep on 2008-05-14
El símbol canonada ("pipe" | ) es fa amb AltGr+1

---

### Post by lFossil on 2008-05-14
Usento es que estic una mica nerviòs perqué necessito lordinador.
A veure ho he fet però m'ha sortit "Login incorrect".

A veure és "lcpi+1 espai+ |+ grep Display". No?

---

### Post by papapep on 2008-05-14
No, has de prèmer la tecla AltGr (a la dreta de la barra espaiadora) i, mentre la mantens apretada, prèmer el número 1. aleshores et farà el |.

I la ordre en concret és:

```
lspci | grep Display
```

Per cert, abans de ficar-la T'HAS D'IDENTIFICAR COM A USUARI. Cal que posis el teu nom d'usuari "normal" i la contrassenya.

---

### Post by lFossil on 2008-05-14
em surt:
Login incorrect

---

### Post by pespin on 2008-05-14
> 
Login incorrect
No estàs posant bé el tenu nom d'usuari i contrasenya

---

### Post by lFossil on 2008-05-14
nomes em demana la contrassenya.
surt:

jasiel-laptop login: lspci | grep Display
Password: aquí poso la contrassenya d'usuari

Login incorrect

---

### Post by lFossil on 2008-05-14
Val d'acord, ja ho he vist.
Primerr fico l'usuari
després la contrassenya i una volta em surt:
jasiel@jasiel-laptop:&#12316;$
llavors fico lspci | grep Display

No?

Però ho fico i no passa res!

---

### Post by papapep on 2008-05-14
Si, senyor.

---

### Post by lFossil on 2008-05-14
Però no passa res!!

---

### Post by papapep on 2008-05-14
Bé, doncs fes:

```
lspci
```

sense res més

---

### Post by lFossil on 2008-05-14
Em surt una llista de coses i es queda igual

---

### Post by papapep on 2008-05-14
Clar, és que aquesta llista de coses és la que hem de veure per saber quina gràfica tens. Si no la saps veure, enganxa-ho aquí.

---

### Post by lFossil on 2008-05-14
00:00.0 Host bridge: ATI Tachnologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bbridge: ATI Technologies Inc RS480 PCI Bridge

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA

00:14.0 SMBus: ATI technologies Inc SBx00 SMBus Controller (rev 13)


Hi ha més coses però mes o menys he ficat les que creia més importants per què em toca escriureu tot jeje, si et serveix i si no ho ficare tot.

---

### Post by papapep on 2008-05-14
Enlloc posa res de "Display controller" o "graphic card" o similar??
Al que has posat no hi sé veure quina és...

Potser si dius quina marca i model concret de l'ordinador que tens...(busca una etiqueta on hauria de posar s/n i un nombre i p/n i un altre nombre i digues els dos).

---

### Post by lFossil on 2008-05-14
Tinc aquesta placa:
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

Ho sé perquè he mirat un fil que vaig penja fa temps en el qual em preguntaves això.

---

### Post by papapep on 2008-05-14
I ara no et surt això quan fas lspci???

Prova a fer:

```
lspci | grep VGA
```

---

### Post by lFossil on 2008-05-14
Sí, sí que em surt :)

---

### Post by lFossil on 2008-05-15
I ara què faig Papapep?

---

### Post by papapep on 2008-05-15
Doncs jo provaria què tal amb una aplicació que prova de configurar aquestes plaques, més o menys, automàticament. Fes a un terminal:

```
sudo aptitude install envyng-core
```

un cop acabi, si acaba bé, clar, fes:

```
sudo envyng -t
```

aquí li hauràs de dir que t'instal·li el driver per les Ati. 
Si acabes el procés sense cap missatge d'error, hauries de reiniciar el sistema a veure si has tingut èxit.

---

### Post by lFossil on 2008-05-15
En diu que s'estan inician els estats dels paquets i després que sçestan generant la base de dades de marcadors, però al final de la llista diu:
E: dpkg was interrumped, you must manually run 'dpkg --configure -a' to cprrect the problem
:confused:
Ha sortit malament?

---

### Post by papapep on 2008-05-15
Bé, cal que facis la ordre que et diu. Fes al terminal:

```
sudo dpkg --configure -a
```

i si acaba bé, torna a fer el que t'he dit abans.

---

### Post by lFossil on 2008-05-15
Una pregunta, tal com ha acavat, a aparegut la pantalla d'inici i e ficat el nom d'usuari i contrassenya i m'ha entrat i funciona perfectament. M'ha demanat de reiniciar per acavar de estar enllesit.
Igualment he de fer el que m'has dit avans¿?

---

### Post by papapep on 2008-05-15
Si us plau, no editis els posts per canviar totalment el que hi posava, sinó l'altra gent que ho pot llegir perdrà part del sentit del fil. 
Això no és una conversa entre tu i jo.

Doncs no, _si ja funciona no ho toquis_ (màxima de la informàtica).

---

### Post by lFossil on 2008-05-15
Usento, perdó.

Però ja el tinc actulitzat?

---

### Post by papapep on 2008-05-15
Sistema > Quan a l'Ubuntu

---

### Post by papapep on 2008-05-15
Sistema > Quant a l'Ubuntu

---

### Post by lFossil on 2008-05-15
Diu que tinc el Gutsy

---

### Post by papapep on 2008-05-15
Bé, doncs està clar que en algun moment de l'actualització de Gutsy a Hardy que vas intentar et va petar tot plegat. Vas tenir algun tall de corrent o de connexió a internet?? Sigui com sigui, per actualitzar tornem al principi de tot plegat, quan et vaig dir que actualitzessis i després fessis la pujada de versió, les ordres dels posts 14 i 18

---

### Post by lFossil on 2008-05-15
No no vaig tenir cap tall de corrent ni res que jo sàpiga. Bé ara intentaré a fer el que em vas dir.

---

### Post by lFossil on 2008-05-15
Bé he fet al terminal:
sudo aptitude update
i m'ha sortit:

jasiel@jasiel-laptop:~$ sudo aptitude update
[sudo] password for jasiel: 
Obté:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-ca
Obté:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [191B]
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-ca     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-ca
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-ca
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-ca
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-ca
Obté:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-ca
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Obté:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-ca        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-ca  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-ca    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-ca
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages         
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages             
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release                   
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages   
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
S'han recollit 4B en 0s (4B/s)        
S'està llegint la llista de paquets... Fet 
jasiel@jasiel-laptop:~$ 

Com u veus?

---

### Post by RainCT on 2008-05-15
Fes:

```
sudo aptitude safe-upgrade
```

I un cop hagi acabat:

```
sudo aptitude full-upgrade
```

---

### Post by papapep on 2008-05-15
Bé, lFossil, ho veig bé.

Ara fes el que t'he dit al principi. El que et diu en RainCT és una altra manera, però farem la "pura" d'Ubuntu:

```
sudo aptitude safe-upgrade
```

i després:

```
sudo do-release-upgrade
```

---

### Post by papapep on 2008-05-15
Per cert, abans de fer això, fes a un terminal:

```
uname -a
```

i passa'ns el que et posi.

---

### Post by lFossil on 2008-05-17
Ok papapep, una cosa, tan pronte pugui fer-ho ho faré, quan tingui una mica de temps d'acord?
Gràcies de totes formes, aviat us diré què tal!!
:):):)

---

### Post by lFossil on 2008-05-26
Bones, una pregunta, encara no he pogut dedicar un moment a fer això últim que em vas dir, però ara fa uns dies vaig obrir el gestor d'actualitzacions i crec que se'm va instal·lar el Hardy, perquè m'han canviat algunes coses com el tema de la finestra d'entrada...
Vaig a  sistema> quant a l'ubuntu i em diu que tinc el Hardy heron, llavors aquí va la meva pregunta, és necessari que faci els últims passos que em vas dir?

(També he de comentar que des de llavors he tingut un problema que explico [aquí]("http://ubuntuforums.org/showthread.php?t=799068"))

---

### Post by RainCT on 2008-05-26
Sí. Pot ser que falti insta&#320;lar/actualitzar algun programa.

---

### Post by calbasi on 2008-05-28
> **pserra said:**
> Hola   companys,
un parell de dubtes....no tinc ganes d'actualitzar  a la 8.04 perque el meu portàtil te 4 anyets  i penso que ja esta una mica desfassadet, i també després de l'ultima actualització (Gutsy),sembla que va mes lent d'arrancar....bé... però una cosa...si vull que no em surti mes el gestor d'actualitzacions com ho faig? avui tinc 13 actualitzacions que no s'instal·len segurament perque no estic amb la 8.04.
Si penseu que m'equivoco al no actualitzar feu-m'ho saber....

Em penso que les actualitzacions fan referència a la versió que tens instal·lada, no a la més nova... Jo tinc una 7.10 i les actualitzacions que em surten son de la meva versió i s'instal·len bé...

---

### Post by lFossil on 2008-05-30
Bones, he fet el que em restava de l'actualització que deia avans en papapep i m'he quedad igual amb el problema del usb i no puc instal·lar actualitzacions del gestor. :confused:

---

### Post by RainCT on 2008-06-01
Fes això:

```

sudo dpkg --configure -a

```

I llavors prova a fer:
```

sudo aptitude update && sudo aptitude safe-upgrade

```

I si et surt algun error copia'l aquí.

---

### Post by lFossil on 2008-06-01
D'acord he fet això que m'has dit i crec que no ha sorgit cap problema, aquí t'ho poso per a que ho vegis:

jasiel@jasiel-laptop:~$ sudo aptitude update && sudo aptitude safe-upgrade
Obté:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-ca     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-ca
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages  
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Prem [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Obté:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [191B]                       
Obté:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-ca [237B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-ca    
Obté:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-ca [1839B]
Obté:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-ca [6914B]
Obté:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-ca
Obté:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-ca
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-ca
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release       
Obté:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release [44,0kB]
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                         
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                           
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages                
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                  
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources                 
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources                 
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources                   
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources                       
Obté:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages [48,6kB]         
Obté:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages [14B]     
Obté:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages [10,9kB]    
Obté:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages [14B]     
S'han recollit 113kB en 7s (15,6kB/s)                                           
S'està llegint la llista de paquets... Fet
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 
Els paquets següents s'han apartat automàticament:
  amarok-xine amule-common apt apt-utils bogofilter-bdb g++ 
  gnome-cards-data gnome-mount libmono-sqlite2.0-cil libquicktime1 
  librarian0 libvcdinfo0 libxerces27 libxine1 libxine1-bin libxine1-console 
  libxine1-misc-plugins libxine1-plugins libxine1-x linux-image-generic 
  linux-restricted-modules-generic mixxx-data 
  openoffice.org-style-andromeda openoffice.org-style-human python-soya 
  sun-java6-bin sun-java6-jre vlc-nox xserver-xorg-dev 
  xserver-xorg-video-amd xserver-xorg-video-intel 
Els paquets següents s'han apartat:
  amarok amule aptitude bluez-gnome bluez-utils f-spot firefox 
  firefox-gnome-support gcc gettext gnome-app-install gnome-games 
  gnome-games-data gnome-pilot gnome-pilot-conduits gpsdrive 
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly hal-cups-utils hpijs 
  hplip hplip-data language-support-ca language-support-en libfaad2-0 
  libhsqldb-java libmono-sqlite1.0-cil libxine1-ffmpeg linux-generic 
  linux-headers-generic mixxx mozilla-mplayer netcat ntfs-3g openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb 
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-l10n-ca 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math 
  openoffice.org-style-industrial openoffice.org-writer python-apt 
  python-uno rss-glx scim scim-gtk2-immodule scim-modules-socket ssl-cert 
  sun-java6-plugin synaptic tomboy totem totem-gstreamer totem-mozilla 
  ttf-gentium ubuntu-artwork ubuntu-standard update-manager 
  update-manager-core vlc wvdial xserver-xorg xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-input-elographics 
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse 
  xserver-xorg-input-synaptics xserver-xorg-input-wacom 
  xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark 
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus 
  xserver-xorg-video-cyrix xserver-xorg-video-dummy 
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128 
  xserver-xorg-video-i740 xserver-xorg-video-imstt xserver-xorg-video-mga 
  xserver-xorg-video-neomagic xserver-xorg-video-newport 
  xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-rendition 
  xserver-xorg-video-s3 xserver-xorg-video-s3virge 
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion 
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx 
  xserver-xorg-video-tga xserver-xorg-video-trident 
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa 
  xserver-xorg-video-vga xserver-xorg-video-via xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo yelp 
Els paquets següents s'actualitzaran:
  cpp evolution-data-server evolution-data-server-common gdb gij 
  libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 
  libegroupwise1.2-13 libgcj-bc libgcj-common libgdata-google1.2-1 
  libgdata1.2-1 libmysqlclient15off mysql-common 
19 paquets actualitzats, 0 instal·lats, 0 a suprimir i 148 a no actualitzar.
Es necessita obtenir 6334kB d'arxius. Després del desempaquetat s'utilitzaran 8192B.
Esteu segur de voler continuar? [Y/n/?] y
S'està escrivint la informació d'estat estesa... Fet
Obté:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main cpp 4:4.2.3-1ubuntu5 [34,5kB]
Obté:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main evolution-data-server 2.22.1.1-0ubuntu3 [418kB]
Obté:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main evolution-data-server-common 2.22.1.1-0ubuntu3 [73,4kB]
Obté:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libedataserver1.2-9 2.22.1.1-0ubuntu3 [113kB]
Obté:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libcamel1.2-11 2.22.1.1-0ubuntu3 [304kB]
Obté:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libebook1.2-9 2.22.1.1-0ubuntu3 [79,6kB]
Obté:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libecal1.2-7 2.22.1.1-0ubuntu3 [242kB]
Obté:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libedata-book1.2-2 2.22.1.1-0ubuntu3 [47,6kB]
Obté:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libedata-cal1.2-6 2.22.1.1-0ubuntu3 [57,1kB]
Obté:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libegroupwise1.2-13 2.22.1.1-0ubuntu3 [107kB]
Obté:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libgdata1.2-1 2.22.1.1-0ubuntu3 [59,2kB]
Obté:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libgdata-google1.2-1 2.22.1.1-0ubuntu3 [12,7kB]
Obté:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main gdb 6.8-1ubuntu2 [2798kB]
Obté:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libgcj-common 1:4.2.3-1ubuntu5 [13,2kB]
Obté:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libgcj-bc 4.2.3-1ubuntu5 [1172B]
Obté:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main gij 4:4.2.3-1ubuntu5 [1526B]
Obté:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libedataserverui1.2-8 2.22.1.1-0ubuntu3 [77,2kB]
Obté:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main mysql-common 5.0.51a-3ubuntu5.1 [59,7kB]
Obté:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libmysqlclient15off 5.0.51a-3ubuntu5.1 [1836kB]
S'han recollit 6334kB en 20s (312kB/s)                                          
(S'està llegint la base de dades ... hi ha 140372 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar cpp 4:4.2.3-1ubuntu3 (fent servir .../cpp_4%3a4.2.3-1ubuntu5_i386.deb) ...
S'està desempaquetant el reemplaçament de cpp ...
S'està preparant per a reemplaçar evolution-data-server 2.22.1-0ubuntu2.1 (fent servir .../evolution-data-server_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de evolution-data-server ...
S'està preparant per a reemplaçar evolution-data-server-common 2.22.1-0ubuntu2.1 (fent servir .../evolution-data-server-common_2.22.1.1-0ubuntu3_all.deb) ...
S'està desempaquetant el reemplaçament de evolution-data-server-common ...
S'està preparant per a reemplaçar libedataserver1.2-9 2.22.1-0ubuntu2.1 (fent servir .../libedataserver1.2-9_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libedataserver1.2-9 ...
S'està preparant per a reemplaçar libcamel1.2-11 2.22.1-0ubuntu2.1 (fent servir .../libcamel1.2-11_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libcamel1.2-11 ...
S'està preparant per a reemplaçar libebook1.2-9 2.22.1-0ubuntu2.1 (fent servir .../libebook1.2-9_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libebook1.2-9 ...
S'està preparant per a reemplaçar libecal1.2-7 2.22.1-0ubuntu2.1 (fent servir .../libecal1.2-7_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libecal1.2-7 ...
S'està preparant per a reemplaçar libedata-book1.2-2 2.22.1-0ubuntu2.1 (fent servir .../libedata-book1.2-2_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libedata-book1.2-2 ...
S'està preparant per a reemplaçar libedata-cal1.2-6 2.22.1-0ubuntu2.1 (fent servir .../libedata-cal1.2-6_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libedata-cal1.2-6 ...
S'està preparant per a reemplaçar libegroupwise1.2-13 2.22.1-0ubuntu2.1 (fent servir .../libegroupwise1.2-13_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libegroupwise1.2-13 ...
S'està preparant per a reemplaçar libgdata1.2-1 2.22.1-0ubuntu2.1 (fent servir .../libgdata1.2-1_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libgdata1.2-1 ...
S'està preparant per a reemplaçar libgdata-google1.2-1 2.22.1-0ubuntu2.1 (fent servir .../libgdata-google1.2-1_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libgdata-google1.2-1 ...
S'està preparant per a reemplaçar gdb 6.8-1ubuntu1 (fent servir .../gdb_6.8-1ubuntu2_i386.deb) ...
S'està desempaquetant el reemplaçament de gdb ...
S'està preparant per a reemplaçar libgcj-common 1:4.2.3-1ubuntu3 (fent servir .../libgcj-common_1%3a4.2.3-1ubuntu5_i386.deb) ...
S'està desempaquetant el reemplaçament de libgcj-common ...
S'està preparant per a reemplaçar libgcj-bc 4.2.3-1ubuntu3 (fent servir .../libgcj-bc_4.2.3-1ubuntu5_i386.deb) ...
S'està desempaquetant el reemplaçament de libgcj-bc ...
S'està preparant per a reemplaçar gij 4:4.2.3-1ubuntu3 (fent servir .../gij_4%3a4.2.3-1ubuntu5_i386.deb) ...
S'està desempaquetant el reemplaçament de gij ...
S'està preparant per a reemplaçar libedataserverui1.2-8 2.22.1-0ubuntu2.1 (fent servir .../libedataserverui1.2-8_2.22.1.1-0ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libedataserverui1.2-8 ...
S'està preparant per a reemplaçar mysql-common 5.0.51a-3ubuntu5 (fent servir .../mysql-common_5.0.51a-3ubuntu5.1_all.deb) ...
S'està desempaquetant el reemplaçament de mysql-common ...
S'està preparant per a reemplaçar libmysqlclient15off 5.0.51a-3ubuntu5 (fent servir .../libmysqlclient15off_5.0.51a-3ubuntu5.1_i386.deb) ...
S'està desempaquetant el reemplaçament de libmysqlclient15off ...
S'està configurant cpp (4:4.2.3-1ubuntu5) ...

S'està configurant evolution-data-server-common (2.22.1.1-0ubuntu3) ...
S'està configurant libedataserver1.2-9 (2.22.1.1-0ubuntu3) ...

S'està configurant libcamel1.2-11 (2.22.1.1-0ubuntu3) ...

S'està configurant libebook1.2-9 (2.22.1.1-0ubuntu3) ...

S'està configurant libecal1.2-7 (2.22.1.1-0ubuntu3) ...

S'està configurant libedata-book1.2-2 (2.22.1.1-0ubuntu3) ...

S'està configurant libedata-cal1.2-6 (2.22.1.1-0ubuntu3) ...

S'està configurant libegroupwise1.2-13 (2.22.1.1-0ubuntu3) ...

S'està configurant libgdata1.2-1 (2.22.1.1-0ubuntu3) ...

S'està configurant libgdata-google1.2-1 (2.22.1.1-0ubuntu3) ...

S'està configurant evolution-data-server (2.22.1.1-0ubuntu3) ...
S'està configurant gdb (6.8-1ubuntu2) ...

S'està configurant libgcj-common (1:4.2.3-1ubuntu5) ...

S'està configurant libgcj-bc (4.2.3-1ubuntu5) ...
S'està configurant gij (4:4.2.3-1ubuntu5) ...
S'està configurant libedataserverui1.2-8 (2.22.1.1-0ubuntu3) ...

S'està configurant mysql-common (5.0.51a-3ubuntu5.1) ...
S'està configurant libmysqlclient15off (5.0.51a-3ubuntu5.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
S'està llegint la llista de paquets... Fet           
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
jasiel@jasiel-laptop:~$

---

### Post by lFossil on 2008-06-01
Per cert, he provat d'iniciar el gestor d'actualitzacions i em passa el mateix.
Això:
[[IMG]http://img174.imageshack.us/img174/9728/capturaupdatemanageruy8.th.png[/IMG]](http://img174.imageshack.us/my.php?image=capturaupdatemanageruy8.png)

[[IMG]http://img110.imageshack.us/img110/9295/capturaupdatemanager1uj0.th.png[/IMG]](http://img110.imageshack.us/my.php?image=capturaupdatemanager1uj0.png)

I amb el tema de l'usb em passa el mateix:

[[IMG]http://img148.imageshack.us/img148/7070/capturagnomemountjf8.th.png[/IMG]](http://img148.imageshack.us/my.php?image=capturagnomemountjf8.png)

---

### Post by lFossil on 2008-06-03
> **lFossil said:**
> Per cert, he provat d'iniciar el gestor d'actualitzacions i em passa el mateix.
Això:
[[IMG]http://img174.imageshack.us/img174/9728/capturaupdatemanageruy8.th.png[/IMG]](http://img174.imageshack.us/my.php?image=capturaupdatemanageruy8.png)

[[IMG]http://img110.imageshack.us/img110/9295/capturaupdatemanager1uj0.th.png[/IMG]](http://img110.imageshack.us/my.php?image=capturaupdatemanager1uj0.png)

I amb el tema de l'usb em passa el mateix:

[[IMG]http://img148.imageshack.us/img148/7070/capturagnomemountjf8.th.png[/IMG]](http://img148.imageshack.us/my.php?image=capturagnomemountjf8.png)

I si instal·lo l'ubuntu de cap i de nou?

---

### Post by lFossil on 2008-06-05
Algú em pot ajudar si us plau? :sad:

---

### Post by CarlesOriol on 2008-06-08
Puff

Esta xungo el tema.

IFossil pots comprovar que a la carpeta /etc/apt/sourceslist.d no tinguis cap arxiu que faci referencia a la gutsy.

Si no hi ha res podem fer 2 coses (per solucionar el problema rapidament):

 1. Fer una copia de la carpeta home i reinsta&#320;lar el sistema (millor obrir un altre fil si tens dubtes de com fer i restaurar la copia)

 2. Esperar a veure si properament fem alguna install-party on poder veure in-situ la teva màquina.

---

### Post by lFossil on 2008-06-08
Ei, finalment he pogut actualitzar-lo al complet.
Vaig provar d'actualitzar pel gestor de paquets synaptic i se m'ha actualitzat!! La veritat, va ser una d'aquestes de l'informàtica...
Ja es sap jajaja
Tots els problemes que hi tenia ja s'han solucionat.
Moltes mercès de totes formes!

---

### Post by CarlesOriol on 2008-06-09
AU... doncs ja saps.

Xapa el fil i afegeix-te al mes dels barrets.

[http://ubuntuforums.org/showthread.php?t=814956](http://ubuntuforums.org/showthread.php?t=814956)

---

