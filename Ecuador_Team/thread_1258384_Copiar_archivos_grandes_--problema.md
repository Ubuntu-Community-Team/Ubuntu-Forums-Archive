---
title: "Copiar archivos grandes --problema"
date: 2009-09-04
forum: Ecuador Team
---

### Post by naitsirch on 2009-09-04
Hola, comento, ando estudiando por propios medios linux, me ha gustado mas ubuntu por su versatilidad...

Nota 1. Tengo Ubuntu instalado bajo Windows

corre excelente y ademas, puedo copiar el archivo y llevar la configuracion a donde quiera.

Nota 2. Tengo virtualizado por medio de VBox una maquina (VM) con Windows XP para poder utilizar corel draw y otros "benjurjes" que aun no hay en linux :) 

Tengo un disco duro externo MyBook de 500GB Western Digital para sacar respaldos y etc etc.

Mi computador tiene 2 Discos Duros:

1.- 80GB IDE con una particion de 55 GB para windows y es el host de ubuntu. y Otra de 25GB originalmente para linux, pero no la utilice, ahora ahi esta montado el disco virtual de windows.

2.- Un disco Sata de 500GB particion de 100GB y Otra de 400GB para FILES (todo=instaladores, musica, videos, fotos, doc.. etc etc)



---

En la primera particion del disco de 55gb c:\ se encuentra la instalacion de 17GB de ubuntu.

es una carpeta de 17GB la cual es mi sistema operativo, pero al momento de querer copiarla para sacar un respaldo al disco externo USB de 500 me sale un problema que el archivo es demaciado grande.

y entonces entro a windows para copiarlo desde ahi y me dice que no hay espacio en el disco duro de 500GB cuando aun tengo 300GB libres.


---


Pregunto:

Hay algun comando especial para copiar la carpeta UBUNTU del disco c:\ al disco USB de 500GB?


NOTA: He utilizado el comando

cp /host/ubuntu /media/My\ Book/ -R --force

y a los 5 minutos sale el error:

christian@ubuntu:/host$ cp ubuntu /media/My\ Book/ -R --force
cp: escribiendo «/media/My Book/ubuntu/disks/root.disk»: Archivo demasiado grande
christian@ubuntu:/host$ 

entonces ha copiado solo una cantidad de 4,7 GB pero la carpeta total es de 17GB.


Gracias cualquier consejo para copiarlo desde Ubuntu o desde Windows (winbugs) :)

---

### Post by estebandid0 on 2009-09-05
lo que pasa es que tu disco duro externo debe estar formateado para fat 32 por lo cual no te deja copiar archivos grandes

ahora para solucionar eso puedes formatear un espacio de tu disco externo en ext3 o ext4 y peudes copiar los archivos sin problema, pero ojo para poder verlos en windows necestas de otro programa ya quewindows por defecto no reconoce las particiones ext

y para hacer un backup nada mejor que grsync es lo mejor

---

