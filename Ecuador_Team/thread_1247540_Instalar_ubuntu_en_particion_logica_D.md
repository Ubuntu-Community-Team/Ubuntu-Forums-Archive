---
title: "Instalar ubuntu en particion logica D"
date: 2009-08-23
forum: Ecuador Team
---

### Post by orlyyan on 2009-08-23
Hola necesito una ayuda de ustedes los versados, quiero instalar ubuntu en la particion D: pero tengo dudas si arrancara sin problemas, ademas que tengo la D como mi respaldo no se como realizar la particion sin que se borren mis datos .ya que me confundo al realizarlo por  especificar particiones manualmente acontinuacion tratare de responderme y ustedes me corregiran.

1.- voy a **especificar particiones manualmente**

solo para ejemplo

/dev/sda1 ntfs    48800 MB
/dev/sda2 ntfs  184000 MB

2.-**EDITAR UNA PARTICION** ....suponiendo que tengo 142 gb de espacio libre y yo quiero darle 10 gb a Ubuntu pondria lo siguiente en
**TAMAÑO NUEVO DE LA PARTICION** EN MB -----> AQUI LA duda pongo 132000 o pongo los 10000 que serian los 10 gb destinados para ubuntu.

De ahy hacer las demas particiones eso si se. porque ya lo hice pero con un disco entero, no en una particion en este caso la D, de un solo disco duro.

Saludos

---

### Post by estebandid0 on 2009-08-23
te sugiero hacer 3 particiones

root
swap 
home

ahora si quieres 10GB tienes que multiplicar 10 x 1024 y esa valor es en megas 10240 MB que equivale a 10 gigas

tanto el root como el swap puedes formatearlos en ext3 o ext4 mas no en ntfs

la swap tiene su propio formato que se llama swap

el swap tiene que ser el doble de lo que es tu memoria ram, osea si tienes 2 gigas en ram tu swap debe ser de 4 gigas

---

### Post by orlyyan on 2009-08-24
estebandid0

> te sugiero hacer 3 particiones

root
swap
home

ahora si quieres 10GB tienes que multiplicar 10 x 1024 y esa valor es en megas 10240 MB que equivale a 10 gigas

tanto el root como el swap puedes formatearlos en ext3 o ext4 mas no en ntfs

la swap tiene su propio formato que se llama swap

el swap tiene que ser el doble de lo que es tu memoria ram, osea si tienes 2 gigas en ram tu swap debe ser de 4 gigas 

Entiendo todo esto mi problema es de como particiono sin perder mis datos en el D

> 2.-EDITAR UNA PARTICION ....suponiendo que tengo 142 gb de espacio libre y yo quiero darle 10 gb a Ubuntu pondria lo siguiente en
TAMAÑO NUEVO DE LA PARTICION EN MB -----> **AQUI LA duda pongo 132000 o pongo los 10000 que serian los 10 gb destinados para ubuntu.**

basado a este manual 

[http://sliceoflinux.com/2009/04/23/instalar-ubuntu-904-paso-a-paso/](http://sliceoflinux.com/2009/04/23/instalar-ubuntu-904-paso-a-paso/)

 y de acuerdo a este procedimiento haciendo en forma manual escogiendo la Particion D

[http://sliceoflinux.files.wordpress.com/2009/04/ma-ubuntu904-6f-paso4-manualmente.png](http://sliceoflinux.files.wordpress.com/2009/04/ma-ubuntu904-6f-paso4-manualmente.png)

luego redimensiona a 10000 (10gb)el disco 30.2 gb

[http://sliceoflinux.files.wordpress.com/2009/04/ma-ubuntu904-6g-paso4-manualmente.png](http://sliceoflinux.files.wordpress.com/2009/04/ma-ubuntu904-6g-paso4-manualmente.png) 



entonces la particion sda2 o paticion D "como yo lo entiendo) de 30.2 gb queda en 9.3gb

Ademas quedan como 22 gb de espacio libre.
[http://sliceoflinux.files.wordpress.com/2009/04/ma-ubuntu904-6i-paso4-manualmente.png](http://sliceoflinux.files.wordpress.com/2009/04/ma-ubuntu904-6i-paso4-manualmente.png)

[COLOR="Blue"]
por logica si mi particion D tiene 142 gb y yo quiero diez para ubuntu seria 132 gb para que queden 10 gb libres?[/COLOR]


[COLOR="SeaGreen"]De ahy hacer las demas particiones eso si se. porque ya lo hice pero con un disco entero, no en una particion en este caso la D, de un solo disco duro.[/COLOR]

me olvidaba mi particion d es donde guardo todos mis archivos

---

### Post by naitsirch on 2009-09-05
Hola a ver si te entiendo...

Tu tienes un disco de 250 GB

una C:\ de 50GB
y una D:\ de 200GB


en la C: tienes win2 y en la D: tienes archivos tuyos...

entonces si quieres modificar la particion al momento que estas haciendo la instalacion, perderas los archivos de la particion D:\

mira


es muy sencillo:


insertas tu disco de ubuntu y le dejas que te corra en liveCD, cuando ya has entrado al sistema ejecutas

$ sudo su

y luego 

# gparted

entonces se te abre un programa que te sirve para hacer particiones (algo asi como en winXP el partition magic--> nunca pude usarlo con exito :))

dentro del gparted, vas a ver tu disco duro 

[[IMG]http://img216.imageshack.us/img216/618/gparted.jpg[/IMG]](http://img216.imageshack.us/i/gparted.jpg/)

aqui escoges la particion 2

que seria en tu caso la de 200GB

y le das click en REDIMENSIONAR

y le haces no solo 10GB, sino unos 20GB

Para Ubuntu

y mueves con la flecha desde la parte derecha le recorres hacia la izquierda


Entonces esto hara que no pierdas los archivos de tu disco d:\

ademas al terminar este proceso, reinicias en windows porque ahi te va a reconocer como cuando apagas de mala manera el computador y le pasa un CHECKDISK

la proxima vez que realices la instalacion de ubuntu

ya tendras una particion especifica de espacio no utilizado para poder usarla con UBUNTU o cualquier distro que prefieras.


Saludos!

---

