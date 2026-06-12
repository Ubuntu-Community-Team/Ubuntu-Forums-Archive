---
title: "permisos a dispositius"
date: 2008-04-16
forum: Catalan Team
---

### Post by abosch on 2008-04-16
Uola, 

tinc un problema-dubte q ha arribat al punt q em molesta més no entedre-ho q solucionar-ho... tinc entés q els dispositius són tractats com a fitxers de manera que se'ls hi otorgen/retiren permisos (rwx). Utilitzo un llapis q com a usuari els tinc tots (rwx) , però quan vulll gravar-hi me'n denega el permís (sempre treballo com a usuari-propietari). Magradaria entendre què passa.

Ui ui ui  ,  ara veig que ... per

'llocs->ordinador->usb_drive'    permios només de lectura 





La pràctica és:  he  llegit q amb l'ordre 'chmod' podria eliminar restriccions  ' chmod 777 nom_del_fitxer'  ;   disculperu una pregunta tant bàsica, pro la ruta del dispositiu és '/media/

La preguntal

---

### Post by abosch on 2008-04-16
ups ! l'he enviat sense completar #-o 

el q estava escrivint acabo de veure que entrant per  'llocs->ordinador->usb_drive' permisos només de lectura  ... ???   no entenc q per un costat tingui permisos i per l'altre no. Una cosa son permisos d'un dispositiu i l'altre del port USB ?  

Gràcies, disculpeu el 2x1
Alex

---

### Post by crazyserver on 2008-04-16
Jo estic pensant que es molt extrany que pq sí et munti l'usb sense permisos d'escriptura...
Vejam... potser amb la sortida de:
```
cat /etc/fstab
```pots mirar els permisos de la carpeta a /media? segurament siguin els permisos que et surten a (llocs-->ordinador) o a l'escriptori. Com ho fas per muntar-ho? ho munta ubuntu? ho muntes tu a ma? dona'ns detalls!

Potser pots canviar els permisos des de llocs->ubuntu, prova-ho també.

---

### Post by papapep on 2008-04-16
> Utilitzo un llapis q com a usuari els tinc tots (rwx)

Mostra a veure què et surt fent a un terminal, amb el llapis connectat::

```
ls -la /media/
```

---

### Post by RainCT on 2008-04-16
No crec que aquest sigui el problema, però per estar segurs ves a  Sistema -> Administració -> Usuaris i grups i comprova que a la pestanya "Privilegis d'usuari" del teu usuari l'opció "Accés automàtic a dispositius d'emmagatzematge externs" estigui marcada.

---

### Post by abosch on 2008-04-16
He comprova't el que dius RainCT,

 ves a Sistema -> Administració -> Usuaris i grups i comprova que a la pestanya "Privilegis d'usuari" del teu usuari l'opció "Accés automàtic a dispositius d'emmagatzematge externs" estigui marcada.

Efectivament la tinc marcada. 

Si faig l'ordre que dius Papapep
abosch@abb-portatil:~$ ls -la /media
total 24
drwxr-xr-x  5 root   root 4096 2008-04-16 22:00 .
drwxr-xr-x 22 root   root 4096 2008-04-12 20:56 ..
lrwxrwxrwx  1 root   root    6 2008-03-09 21:06 cdrom -> cdrom0
drwxr-xr-x  2 root   root 4096 2008-03-09 21:06 cdrom0
drwxr-xr-x  3 root   root 4096 2008-03-09 21:06 deb
-rw-r--r--  1 root   root  105 2008-04-16 22:00 .hal-mtab
-rw-------  1 root   root    0 2008-04-16 22:00 .hal-mtab-lock
drwx------ 12 abosch root 4096 1970-01-01 01:00 USB Drive


I pel que fa al que preguntes Crazyserver
Com ho fas per muntar-ho? ho munta ubuntu? ho muntes tu a ma? dona'ns detalls!

jo no munto res, sempre l'ha dectat/muntat sol.

---

### Post by crazyserver on 2008-04-16
:| però si té els permisos bé!, no?XD ets el propietari, pots llegir, escriure i executar.. no ho entenc, pots fer:
```
sudo chmod 777 /media/USB\ Drive
```però no crec que serveixi...

---

### Post by papapep on 2008-04-16
El curiós és la data en que et munta el dispositiu:

```
drwx------ 12 abosch root 4096 [COLOR="Red"]**1970-01-01**[/COLOR] 01:00 USB Drive
```

A mi em munta el pendrive amb els mateixos permisos (però amb data del moment que ho faig) i bé que puc desar-hi coses:

```
drwx------  3 papapep root    4096 2008-04-17 00:28 disk-4
```

Prova a fer:

```
touch /media/USB Drive/prova.txt
```

a veure si et crea el fitxer prova.txt al pendrive.

EDITO: Per cert, quin format de sistema de fitxers hi tens al llapis USB? I quina versió d'Ubuntu fas servir?

---

### Post by crazyserver on 2008-04-17
Segons posa el profile usa la gutsy, no?XD
si no et funciona el touch d'aquesta manera,fes:[FONT=monospace]
```
touch /media/USB\ Drive/prova.txt
```

Que s'assembla pero no es el mateix!XD
[/FONT]

---

### Post by abosch on 2008-04-18
iepala  :)

 ...Ostres amb això de l'any no m'hi havia fixa't.  Acabo de provar les ordres els resultats són,

abosch@abb-portatil:~$ touch /media/USB\ Drive/prova.txt
touch: no s'han pogut canviar les dates de «/media/USB Drive/prova.txt»: Read-only file system

abosch@abb-portatil:~$ sudo chmod 777 /media/USB\ Drive
[sudo] password for abosch:
Sorry, try again.
[sudo] password for abosch:
chmod: en canviar els permissos de «/media/USB Drive»: Read-only file system

abosch@abb-portatil:~$ touch /media/USB\ Drive/prova.txt
touch: no s'han pogut canviar les dates de «/media/USB Drive/prova.txt»: Read-only file system
abosch@abb-portatil:~$

 per si pot ajudar, el format de fitxers del pendrive és 'vfat' . Potser més que ajudar complica les coses  ¿?  ( he llegit per alguna banda que el format 'fat' no suporta permisos? )  

 
salut

---

### Post by papapep on 2008-04-18
> **crazyserver said:**
> Segons posa el profile usa la gutsy, no?XD
No te'n refiis gens ni mica dels usuaris :-D Sempre t'enganyen! (he vist massa capítols de House??)

> **crazyserver said:**
> si no et funciona el touch d'aquesta manera,fes:
```
touch /media/USB\ Drive/prova.txt
```

Aquí sí, se m'ha oblidat el cony de backslash...

**Abosch**, vàries coses:
 - Entenc que el teu pendrive no tindrà un switch físic per a ficar-lo en mode protegit oi?
 - Tens molts fitxers al directori arrel del pendrive (més de 512)?
 - Prova a re-formatejar-lo des de Windows, a veure si t'arregla el problema.

---

### Post by abosch on 2008-04-18
Carai rellegint el fil, he vist que tinc tendència a independitzar les 't' del participi.  :confused:


>  No te'n refiis gens ni mica dels usuaris  Sempre t'enganyen! (he vist massa capítols de House??)
 
 sobretot si no tenen permisos ...  :D   

conyes a part, és d'agrair la paciència que teniu aquells/es veterans/es amb els qui no rasquem bola. Per altra banda no és per falta d'interés , tot al contrari, moltes vegades entro per cercar alguna cosa en particular i al final acabo tancant la màquina havent aprés vàries coses ... però sense haver resolt el que m'hi havia portat ](*,) 


Tornant al tema del fil (que ia me'n vai! ), 
> - Entenc que el teu pendrive no tindrà un switch físic per a ficar-lo en mode protegit oi? No estic segur,diria q et refereixes a un interruptor tipus ON-OFF, si és això la resposta és no.
>   - Tens molts fitxers al directori arrel del pendrive (més de 512)? No

> - Prova a re-formatejar-lo des de Windows, a veure si t'arregla el problema.    'Val, en els propers dies ho provo. De fet aquesta és una de les meves preferides, un "reset" i a tornar-hi. Ja vos explico. Posats em sembla que li faré particions guardan-ne una de petita per les visites a màquines amb windows. 


Tornant al tema, 
[Llegeixo]("http://www.ubuntu-es.org/index.php?q=node/54527") que també es poden modificar permisos USB amb el canvi

```
/etc/udev/rules.d/40-permissions.rules , donde cambie los permisos de


SUBSYSTEM==”usb_device”, MODE=”0664?

a

SUBSYSTEM==”usb_device”, MODE=”0666?


```

Això fa referència al que preguntava de principi del fil. Són coses diferents els permisos d'un dispositiu que els te la màquina per entrada d'un port en particular? uff... espero que m'entengueu perquè no sé com dir-ho millor

gràcies, 
Alex

---

### Post by papapep on 2008-04-18
No sé si hauràs revisat ja el que tens al gconf-editor.

Ves a Aplicacions > Eines del sistema > Editor de la configuració > System > Storage > Default options > Vfat i enganxa el que hi tens, si us plau.

---

### Post by abosch on 2008-04-19
el que m'hi apareix és,

mount_options [short name=mixed,uid=,utf8,umask=077,exec,usefree]

envio captura

---

### Post by crazyserver on 2008-04-19
Jo ho tinc igual!;)

---

