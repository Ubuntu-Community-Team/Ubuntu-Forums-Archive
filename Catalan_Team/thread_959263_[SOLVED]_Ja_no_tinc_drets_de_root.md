---
title: "[SOLVED] Ja no tinc drets de root"
date: 2008-10-26
forum: Catalan Team
---

### Post by dmolner on 2008-10-26
Hola,

He estat instal.lant el VirtualBox i tenia aquest missatge:
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE)

Així que seguint instruccions de Internet vaig executar
sudo chmod 777 /dev/vboxdrv per al meu usuari pero ara hem diu que només soc del grup vboxusers

Com puc tornar a tenir drets de superusuri?

Ho he probat amb **Sistema-> Administracio-> Usuaris i grups** però no puc fer-ho ja que tinc un missatge d'error que crec que te que veure amb la falta de drets.(No s'ha pogut autenticar - S'ha produït un error inesperat.)

Gràcies per la vostra ajuda.

---

### Post by papapep on 2008-10-26
> ara hem diu que només soc del grup vboxusers

I d'on treus això?
Quin missatge exacte et dóna i en quin moment o executant quina ordre et surt?

---

### Post by dmolner on 2008-10-26
La veritat ara no recordo amb quina instrucció ho vaig veure a la consola.
A **Usuaris i grups** no puc fer res.
M'ha desaparegut la opcio de instal.lar o desinstal.lar coses.

Suposo que tindre de donar-me drets com a root com a usuari root, pero com es fa? Soc nou i no en se massa i no ho he trobat a Internet

---

### Post by Tomàs M. on 2008-10-26
Tinc aquesta xuleta d'un dia que vaig tocar alguna cosa que no havia de tocar; mira't el segon enllaç a veure si et serveix:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1150772](http://forum.ubuntu-fr.org/viewtopic.php?pid=1150772)
sudo: /etc/sudoers is owned by uid 1000, should be 0
Salut

Toujours en console de récupération (mode recovery) :
chown root:root /etc/sudoers 

@+

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
sudo: /etc/sudoers is mode 0777, should be 0440

---

### Post by dmolner on 2008-10-26
No acabo d'entendre el que diu, però he mirat l'arxiu /etc/groups i només surto com
root: x:0:
vboxusers: x:125:

M'haig de possar als altres que posa "firstuser"?

---

### Post by Tomàs M. on 2008-10-26
És que suposo que depèn de què et passi exactament. Fes cas a en papapep i et sabrà ajudar millor que jo...
Pots fer sudo? En cas contrari, quin és el missatge d'error?

---

### Post by SiscoGarcia on 2008-10-26
Perdoneu que m'hi posi pel mig, però crec que hauríem d'anar a pams. M'explico: d'entrada quina versió d'ubuntu fas anar? Una altra cosa, això et passa amb la màquina virtual o amb l'ubuntu? En qualsevol cas, quan dius que

> **dmolner said:**
> 
Ho he probat amb **Sistema-> Administracio-> Usuaris i grups** però no puc fer-ho ja que tinc un missatge d'error que crec que te que veure amb la falta de drets.(No s'ha pogut autenticar - S'ha produït un error inesperat.)


és des del teu usuari, no? I no ets administrador de l'equip? No acabo d'entendre que et continuï passant:confused:

---

### Post by papapep on 2008-10-26
Dmolner: enganxan's el teu fitxer /etc/group, si us plau.

---

### Post by dmolner on 2008-10-27
> **Tomàs M. said:**
> 
Pots fer sudo? En cas contrari, quin és el missatge d'error?
Des de la consola si que puc fer sudo.

> **SiscoGarcia said:**
> 
és des del teu usuari, no? I no ets administrador de l'equip? No acabo d'entendre que et continuï passant:confused:
Crec que el que pasa es això que he deixat de ser administrador

> **papapep said:**
> Dmolner: enganxan's el teu fitxer /etc/group, si us plau.
He canviat els noms dels usuaris el meu seria "jomateix"
He tingut de possar un " " entre ":" i la "x" ja que sino no m'ho accepta el forum.

root: x:0:jomateix
daemon: x:1:
bin: x:2:
sys: x:3:
adm: x:4:
tty: x:5:
disk: x:6:
lp: x:7:
mail: x:8:
news: x:9:
uucp: x:10:
man: x:12:
proxy: x:13:
kmem: x:15:
dialout: x:20:unaltre
fax: x:21:
voice: x:22:
cdrom: x:24:unaltre
floppy: x:25:unaltre
tape: x:26:
sudo: x:27:
audio: x:29: pulse,unaltre
dip: x:30:
www-data: x:33:
backup: x:34:
operator: x:37:
list: x:38:
irc: x:39:
src: x:40:
gnats: x:41:
shadow: x:42:
utmp: x:43:
video: x:44:
sasl: x:45:
plugdev: x:46:
staff: x:50:
games: x:60:
users: x:100:
nogroup: x:65534:
libuuid: x:101:
dhcp: x:102:
syslog: x:103:
klog: x:104:
scanner: x:105:hplip,unaltre
nvram: x:106:
fuse: x:107:
ssl-cert: x:108:
lpadmin: x:109:
crontab: x:110:
mlocate: x:111:
ssh: x:112:
avahi-autoipd: x:113:
gdm: x:114:
admin: x:115:
pulse: x:116:
pulse-access: x:117:
pulse-rt: x:118:
messagebus: x:119:
avahi: x:120:
netdev: x:121:
polkituser: x:122:
haldaemon: x:123:
david: x:1000:
dolors: x:1001:
sambashare: x:124:
vboxusers: x:125:jomateix


Gràcies a tots per ajudar-me.

---

### Post by papapep on 2008-10-27
Per enganxar aquest tipus de contingut tens l'etiqueta de codi, que pots posar clicant damunt l'icona amb un #. Tot el que fiquis entre les dues etiquetes CODE i /CODE que et posa, se li respecta el format.

Si dius que el sudo et funciona al terminal, abans de fer altres coses, hauries de provar a crear un nou usuari per veure si en aquest et funciona tot correctament, ja que flaira que t'hagis carregat alguna cosa del Gnome al teu usuari.

---

### Post by dmolner on 2008-10-27
> **papapep said:**
> 
Si dius que el sudo et funciona al terminal, abans de fer altres coses, hauries de provar a crear un nou usuari per veure si en aquest et funciona tot correctament, ja que flaira que t'hagis carregat alguna cosa del Gnome al teu usuari.

Pots dir-me com fer-ho, ho tindria de buscar i si m'ho dius vaig més segur.
Segons el que he possat sembla com si no estigues com a "admin", no?

---

### Post by papapep on 2008-10-27
Per afegir un usuari:

```
sudo useradd -m el_nom_que_vulguis
```

Per crear-li la contrasenya:

```
sudo passwd el_nom_que_vulguis (però el mateix que abans, clar)
```

També pots provar a afegir-te al grup **admin**, al /etc/group, reiniciar, i a veure si et funciona.

---

### Post by dmolner on 2008-10-27
Gràcies papapep.

Provare les dues coses.
Es pot des de la consola afegir un usuari al un grup determinat?

---

### Post by papapep on 2008-10-27
A Linux _absolutament tot_ es pot fer des del terminal. El que sí que és possible, és que coses que es poden fer al terminal no es puguin fer en mode gràfic si ningú n'ha creat la interfície bonica :-)

Per afegir un usuari a un grup determinat:

```
sudo useradd -G el_grup l'usuari
```

---

### Post by dmolner on 2008-10-27
Aconseguit!!!

He creat un usuari al que li he donat drets d'admin.
Amb aquest usuari he entrat a "Usuaris i grups" i he habilitat el meu usuari com a admin.

He tancat la sesió i l'he tornat a obrir i ja soc admin :lolflag:

Moltissimes gràcies a tots ara a seguir amb el VirtualBox que segueix no iniciant-se per manca de permisos, crec.

---

