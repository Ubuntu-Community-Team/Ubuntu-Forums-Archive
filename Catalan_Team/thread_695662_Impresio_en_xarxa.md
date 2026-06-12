---
title: "Impresio en xarxa"
date: 2008-02-13
forum: Catalan Team
---

### Post by almogabber on 2008-02-13
Tinc una xarxa muntada amb dos portatils amb XP conectats via wifi, i un altre amb Ubuntu 7.10 on hi tinc la impresora, una HP DeskJect 710c.

Imprimeix tant en local com en xarxa perfecte, però (i aquest és el problema): si vull enviar un arxiu a la impressora des dels portàtils abans he d'entrar dins la xarxa i connectar la impressora (botó dret -> connectar..)

Si no fos pel nivell dels usuaris dels portàtils això no és cap problema, però no em puc permetre en confiar que sempre se'n recordin del que han de fer per imprimir.

Suposo que això serà perquè aquest dos usuaris (que ja tinc a la taula de usuaris de unix i de samba, és així oi?) han d'entrar el seu nom i contrasenya cada primera vegada que accedeixen als meus compartits (tant arxius com la impressora). És això, oi??

Hi ha alguna manera per donar 'via lliure' perquè aquest dos usuaris entrin al meu pc sempre que vulguin, i no hagin d'entrar ni el nom ni la contrasenya ni tan sols el primer cop?, i així poder accedir als arxius i a la impressora compartides??

Sempre cap a la simplificació màxima. :D

gràcies nanos!!! ;)

---

### Post by guillemsola on 2008-02-13
El linux és una virgüeria per les xarxes però com tot s'ha de configurar.

Respecte a la impressió prova a connectar amb el sevei CUPS que si no recordo malament està activat per defecte.

La cosa va aixì, t'has de connectarper HTTP a la IP de la màquina on hi ha la impressora al port 631.

Per exemple si la IP de l'ubuntu és 192.168.1.2 la cosa quedaria aixì

> [http://192.168.1.2:631/](http://192.168.1.2:631/)

Si et carrega això tindràs accés a l'administració de la impressora i la seva cua.

Després per imprimir tan des del finestre o linux agregues una impresora del tipus impresora en xarxa amb la direcció HTTP de la tava impresora. Per exemple

> [http://192.168.1.2:631/printers/HP_DESKJET_710C_USB_1](http://192.168.1.2:631/printers/HP_DESKJET_710C_USB_1)

Resptecte a que no pregunti la paraula de pas cada vegada que accedeixes a un recurs creu que hauries de modificar el fitxer /etc/samba/smb.conf. (Recorda de fer-ne una copia abans de res)

Localitza on diu AUTHENTIFICATION i fixa't que hi digui

security = SHARE

crec que per defecte està a USER

Això permet determinar per a cada servei si ha de demanar paraula de pas o no.

al final de l'arxiu tindràs una referència a cada recurs compartit a la màquina. Mira que hi hagi com a mínim aquests valors. 

> [public]
   comment = Carpeta compartida
   path = /home/usuari
   available = yes
   public = yes
   browseable = yes
   writable = yes

Normalment el recurs és diu [public] si no hi haurà el nom que tu hi haguis possat.

SaluT!

---

### Post by almogabber on 2008-02-15
Hola Angrychai! Gràcies per la resposta.

Sobre la primera part, dir-te que la impressora connectada al meu pc (amb ubuntu: 192.168.1.2) ja està agregada als dos ordinadors amb windows. Fins aquí no he tingut masses problemes.

Suposo que la solució és la que esmentes: a l'arxiu smb.conf l'apartat Authentification està posar en 'security = USER', com bé deies. Si el poso a SHARE, els altres membres de la xarxa podran entrar sense introduir cap password no? Ok, perfecte!

Però, una altra pregunta abans: més avall hi ha el següent apartat, que suposo que fa referència la impressora:
```
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
**   public = no - No hauria de ser YES??**
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
**   guest ok = no - Aquest hauria de ser YES també, oi?**
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin
```

No s'haurien de canviar les dues variables que he marcat??

Ah, i si, al final de l'arxiu  hi han els detalls de les carpetes compartides, com dius.

Gràcies per l'ajuda!! :)

---

### Post by guillemsola on 2008-02-15
Respecte a la impresora no ho tinc clar, crec que si comparteixes per CUPS ja no té massa utilitat el recurs samba.

Em refereixo a que potser elimines l'opció de l'impresora del smb.conf i la pots continuar fent servir a través de CUPS. La veritat no ho he probat.

Jo sempre ho he deixat per defecte i sense problemes.

Salut!

---

### Post by rroca1 on 2008-02-21
Jo en tinc 2 xp i un ubuntu. L'1 xp la té compartida i no he fet res més que a ubuntu posar-hi sistema/administració/carpetes compartides/ m'ha instal·lat el suport per a samba i he anat a afegir la impressora. FINAL! Tot va bé (cal posar el mateix grup de treball als XPS i a l'UBUNTU.

---

