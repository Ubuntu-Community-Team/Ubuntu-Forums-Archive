---
title: "M'ha desaparegut la barra superior."
date: 2008-07-20
forum: Catalan Team
---

### Post by Fantito on 2008-07-20
Hola a tots.

Primer de tot em presento ja que és el meu primer missatge, em diuen Fantito y sóc de Barcelona. He acabat usant l'Ubuntu tip de tanta tonteria amb les finestres.

Anem al grá. Tinc instal·lat el Thunderbird com a gestor de correu però si clicaba una adreça de correu -a una web per exemple- no se m'obria el Thunderbird, si no que se m'obria l'Evolution i el correu no sortia. 

Amb un atac de "sóc-el-millor", arrecno el 'Gestor de paquets Synaptic' i em carrego tot, i dic tot el que tenia que veure amb l'Evulution.....

El que he perdut són totes les icones i les barres de la pantalla y no puc fer res.

Si us plau, em podeu dir on puc trobar un recuperador del sistema o similar? He probat amb el menú d'arrencada mirant de restituir el sistema, però no logro que es recuperi.

Un altre vegada que fiqui la pota, intentaré que no sigui tant endins.

Mercès per l'ajuda.

el Fantito, l'Alfred

---

### Post by LitusMayol on 2008-07-20
Fes click amb el botó dret damunt la barra de baix i clicka a "*Afegeix un quadre*".


(perquè el problema és que t'has carregat la barra intentant carregar-te l'**Evolution**, no?)

---

### Post by Fantito on 2008-07-20
tampoc tinc barra inferiror ni cap icona que sigui premible i que em permeti entrar al sistema de cualsevol manera.

La destrossa ha estat gran.

El fantito, l'Alfred

---

### Post by papapep on 2008-07-20
Et deus haver carregat tot el Gnome (el paquet ubuntu-desktop), que es desinstal·la si intentes treure l'Evolution...

A un terminal prova a fer:

```

sudo aptitude install ubuntu-desktop gdm
```

---

### Post by Fantito on 2008-08-15
Hola de nou.

He estat uns dies fora i no he pogut conectar-me.

Sembla que la cosa no avança. He posat el comandament que m'heu recomanat en un terminal i després d'un minut llarg de veure córrer text acaba amb aquestes dues frases:

>Ubyntu 8.04.1 Alf-laptop tty1
>alf-laptop loguin: (escric el meu loguin)
>[   97.659375] sr0: CDROM (ioctil) error, command: Test Unit >Ready 00 00 00 00 00 00 <

i cada vegada que l'arrenco acaba de la mateixa manera però no arribo a que se m'arrenqui a la versió visual o com es digui.

A veure si tenim més sort amb la propera proposta.

l'Alfred

---

### Post by Fantito on 2008-08-19
Per un altre costst em diuen que miri d'aconseguir un programa reparador ya que potser que al desinstal·lar l'Evolution es desinstal·len arxius importants en el funcionament de l'Ubuntu. He descartat l'opció de tornar a instal·lar tot l'Ubuntu ja que no enten la partcició que vaig fer en el seu moment i em queda oculta sense poder recuperar la feina que vaig fer.

A veure si algú em pot donar alguna altra solució, o com aconseguir un 'reparador'.

Mercès.

l'Alfred

---

### Post by patrickfromspain on 2008-08-19
el reparador com a tal, no existeix. El problema que tens es bastant gros. El que podries provar es, quan entres a ubuntu, pitjar Control + Alt + F1 i et quedaras en una especie d'MS-DOS, en un terminal. Alla escrius el teu nom d'usuari i la teva contrasenya (quan escriguis la contrasenya es normal que no es mogui res, escriu-la i prem enter).

Un cop alla: sudo nano /etc/apt/sources.list i borres la linea del cdrom i busques todos les linies que comencin per #deb i borres el #. Control + O (o de oviedo) per guardar, Control + X per sortir. A partir d'aqui:

sudo apt-get update
sudo apt-get install ubuntu-desktop gdm 

i reinicia, a veure que pasa.

salut

---

### Post by Tomàs M. on 2008-08-19
Tot i que ara és el més petit dels teus problemes, per canviar a TB com a aplicació de correu: Sistema - Preferències - Aplicacions preferides.
Per cert, si algú vol fer servir el gmail: [http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/) :-)

---

### Post by Fantito on 2008-08-23
Hola patrickfromspain i demés.

He fet tot el que m'has dit, evidentment amb el 'xino' conectat a la xarxa, i acaba amb auna frase semblant a aquesta:

< < No s'ha trobat el paquet GMD > > o similar.

Quan reinicio diu:

< < Starting up...
< < Loading, plase wait...
< < Kinit: name_to_dev_t(/dev/disk/by-uuid/ca9d231c-3371-486d-9bc2-eddd8686cce7) = sda6(8,6)
< < Kinit: trying to resume from /dev/disk/by-uuid/ca9d231c-3371-486d-9bc2-eddd8686cce7
< < Kinit: No resume image, doing normal boot... > >

em sap greu, però la cagada va ser gran.

l'Alfred

---

### Post by Fantito on 2008-10-09
Un "amic informàtic" de torn m'ha passat una sèrie de comandaments que s'assemblen molt al que em diu patrickfromspain, però em diu que s'ha de fer des de ROOT. El problema és que em cal saber un password vàlid per a root, ja que el meu no em serveix tot i que l'amic m'ha dit que podria ser el mateix.
Si us plau, algú em podria facilitar un password vàlid per a Root? merci.

l'Alfred

---

### Post by Ferri on 2008-10-09
A Ubuntu el "root" està inhabilitat per defecte. En el seu lloc es fa servir el comandament "sudo" davant dels comandaments que ho necessiten.
Quan fas servir "sudo" et demana una clau, que és la del teu usuari, si ets l'usuari principal (si no ho ets, depèn de si se li ha donat o no drets administratius al l'usuari en qüestió).
Pel que expliques, si fas les coses com diu el Patrick t'hauria de funcionar.

---

