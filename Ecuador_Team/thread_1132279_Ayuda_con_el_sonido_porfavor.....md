---
title: "Ayuda con el sonido porfavor...."
date: 2009-04-21
forum: Ecuador Team
---

### Post by xxxpoexxx on 2009-04-21
Hola a todos.... soy nuevo utilizando ubuntu. decidi migrar a ubuntu. he instalado la version 8.04 en una laptop HP tx2532la. todo me funciona de maravilla solo q no tengo sonido :(  porfavor si alguien me puede ayudar con este problema.......

---

### Post by Favux on 2009-04-21
Hi xxxpoexxx,

If you have the same sound chip as other TX2500's.

To the bottom of the file "/etc/modprobe.d/alsa-base" you add the following line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
To edit the file you would use:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Since you have to be root when you edit it gksudo will do that. It will ask for your password. Gedit is gnome-edit.

To determine your soundchip:
```
aplay -l
```

I hope this helps.

---

### Post by xxxpoexxx on 2009-04-22
> **Favux said:**
> Hi xxxpoexxx,

If you have the same sound chip as other TX2500's.

To the bottom of the file "/etc/modprobe.d/alsa-base" you add the following line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
To edit the file you would use:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Since you have to be root when you edit it gksudo will do that. It will ask for your password. Gedit is gnome-edit.

To determine your soundchip:
```
aplay -l
```

I hope this helps.

Hey man...!!! you save me...!!!
thats works...!!!
Thx....
pdt: sorry for my english..!! is not perfect.
:guitar::lolflag:

---

### Post by Favux on 2009-04-22
Hi again xxxpoexxx,

Great!  I'm glad you got sound working.  You are welcome.

---

### Post by estebandid0 on 2009-04-22
Saludos

Mira en unos pocos días más va a salir la version 9.04, la versión que tienes es la de exactamente hace un año, por lo cual te sugeriría o que mejor te instales la versión 8.10 que es la de octubre del año pasado o te instalas la nueva que sale en 4 días más.

Por cierto te sugiero que si estas migrando a Ubuntu siempre pero siempre crees tres particiones cuando instalas

root /
home
swap

ya que por defaul ubuntu te crea solo dos particiones, al tener el home separado del root puedes cambiarte y formatear tu máquina las veces que quieras en caso de cambiarte de distro y sin perder tus archivos y configuraciones

Saludos

---

### Post by xxxpoexxx on 2009-04-22
> **estebandid0 said:**
> Saludos

Mira en unos pocos días más va a salir la version 9.04, la versión que tienes es la de exactamente hace un año, por lo cual te sugeriría o que mejor te instales la versión 8.10 que es la de octubre del año pasado o te instalas la nueva que sale en 4 días más.

Por cierto te sugiero que si estas migrando a Ubuntu siempre pero siempre crees tres particiones cuando instalas

root /
home
swap

ya que por defaul ubuntu te crea solo dos particiones, al tener el home separado del root puedes cambiarte y formatear tu máquina las veces que quieras en caso de cambiarte de distro y sin perder tus archivos y configuraciones

Saludos

me parece interesante lo q me dices.... y voy a estar a la expectativa cuando salga la nueva versión de ubuntu... y lo de las particiones he estado leyendo y eso pero aun no tngo claro sobre las cuotas q debo dar a cada partición. por ejemplo si no me equivoco al swap toca dar el doble de la memoria ram q posee el equipo. realmente aun no estoy al tanto de eso. si puedes ayudam con una breve explicación de todo eso. te lo agradecería un monton. o a su vez si esque ya existe algun hilo sobre eso dame el link.... gracias.

---

### Post by estebandid0 on 2009-04-23
> **xxxpoexxx said:**
> me parece interesante lo q me dices.... y voy a estar a la expectativa cuando salga la nueva versión de ubuntu... y lo de las particiones he estado leyendo y eso pero aun no tngo claro sobre las cuotas q debo dar a cada partición. por ejemplo si no me equivoco al swap toca dar el doble de la memoria ram q posee el equipo. realmente aun no estoy al tanto de eso. si puedes ayudam con una breve explicación de todo eso. te lo agradecería un monton. o a su vez si esque ya existe algun hilo sobre eso dame el link.... gracias.

Encontré tu máquina y bueno dice que tiene 250 GB como la mía, yo tengo la tx1420us

Cuando se tiene un gran disco duro puedes crear la opcion del doble de la ram, pero si no te ajustas a lo que tienes.

Mira acabo de revisar cuanto del root he usado, y tengo disponible en el root 16GB, y tengo bastantes programas instalados, asi que con eso estas bien.

Si crees que vas a necesitar mas espacio para el root, dale mas espacio.

Tienes 3 gigas de ram asi que 6 gb de swap van bien, y lo que sobra para el home.

Ojo ten en cuenta que la nueva version que sale en los proximos dias vas a poder instalarla en ext4, no como en las previas que la instalabas en ext3.

Yo lo tengo así

root 20GB
swap 6 gb
home el resto

Con eso te queda super bien la máquina

Si necesitas mas ayuda solo escribime

---

