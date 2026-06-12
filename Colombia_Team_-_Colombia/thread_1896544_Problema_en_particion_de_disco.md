---
title: "Problema en particion de disco"
date: 2011-12-17
forum: Colombia Team - Colombia
---

### Post by SHAKAIM on 2011-12-17
Saludos a todos
He instalado Ubuntu 11.10 desde hace un mes más o menos. El proceso de instalación lo seguí paso a paso y muy minuciosamente, en lo que respecta a las particiones
Para raíz asigné 20 GB, pero al pasar Bleachbit aparecio un mensaje casi al final donde decía que tenía 0 bits de espacio, me llamó mucho la atención pues no he instalado casi nada. Luego al con Nautilus encontré que carpeta home está dentro de la partición "/"...he leído que puede darse por cierres imprevistos de sistema, cortes de energía etc etc.
Domino apenas nada la informática y me da miedo embarrarla, a pesar de leer mucho en internet. Pero nooo.
Por cierto tengo capturas de pantalla tanto de las particiones como de Bleachbit y un reporte de Nautilus que quisiera me ayuden a ver si hay algo malo, pues vi por ahí algo de error...
Alguien puede orientarme los pasos a seguir? repito no domino informática la ayuda debe ser paso a paso....
Gracias

---

### Post by SHAKAIM on 2011-12-17
Saludos a todos
He instalado Ubuntu 11.10 desde hace un mes más o menos. El proceso de  instalación lo seguí paso a paso y muy minuciosamente, en lo que  respecta a las particiones
Para raíz asigné 20 GB, pero al pasar Bleachbit aparecio un mensaje casi  al final donde decía que tenía 0 bits de espacio, me llamó mucho la  atención pues no he instalado casi nada. Luego al con Nautilus encontré  que carpeta home está dentro de la partición "/"...he leído que puede  darse por cierres imprevistos de sistema, cortes de energía etc etc.
Domino apenas nada la informática y me da miedo embarrarla, a pesar de leer mucho en internet. Pero nooo.
Por cierto tengo capturas de pantalla tanto de las particiones como de  Bleachbit y un reporte de Nautilus que quisiera me ayuden a ver si hay  algo malo, pues vi por ahí algo de error...
Alguien puede orientarme los pasos a seguir? repito no domino informática la ayuda debe ser paso a paso....
Gracias

---

### Post by BC59 on 2011-12-17
Abre un terminal con CTRL+ALT+T y pega esto con click derecho-pegar:

```
sudo parted /dev/sda print 
```

Intro y contraseña.

Después esto:

```
sudo fdisk -l
```

Copia los resultados del terminal y pega les en un post nuevo.

---

### Post by howefield on 2011-12-17
Duplicate threads merged.

---

### Post by SHAKAIM on 2011-12-17
Buenos días, aquí esta la primera parte

kintia@kintia-K53E:~$ sudo parted /dev/sda print
[sudo] password for kintia: 
Modelo: ATA WDC WD6400BPVT-8 (scsi)
Disco /dev/sda: 640GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Typo      Sistema de ficheros  Banderas
 1      32,3kB  20,0GB  20,0GB  primary   ext4                 oculta, lba
 2      20,0GB  180GB   160GB   primary   ntfs                 arranque
 3      180GB   451GB   271GB   extended
 5      180GB   200GB   20,0GB  logical   ext4
 6      200GB   450GB   250GB   logical   ext4
 7      450GB   451GB   1023MB  logical   linux-swap(v1)

kintia@kintia-K53E:~$ 

la segunda ejecución....

kintia@kintia-K53E:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros, 1250263728 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador del disco: 0x98b324f9

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1              63    39062562    19531250   1c  Hidden W95 FAT32 (LBA)
La partición 1 no se inició en el limite físico del sector
/dev/sda2   *    39062568   351628327   156282880    7  HPFS/NTFS/exFAT
/dev/sda3       351629310   880973823   264672257    5  Extendida
La partición 3 no se inició en el limite físico del sector
/dev/sda5       351629312   390690815    19530752   83  Linux
/dev/sda6       390692864   878972927   244140032   83  Linux
/dev/sda7       878974976   880973823      999424   82  Linux swap / Solaris
kintia@kintia-K53E:~$ 

Gracias

---

### Post by BC59 on 2011-12-17
Pues como ves, las particiones 1 y 3 no están ubicadas en el limite físico del sector.
No se como lo has hecho pero las particiones están mal mezcladas. ¿Tienes instalado Windows Vista o 7?

---

### Post by SHAKAIM on 2011-12-17
Ya lo veo, como escribia arriba segui paso a paso, antes revisé por horas diferentes tutoriales y leí mucho, me daba como miedo hacer algo mal.
Inicialmente probé con WUBI, luego ya me sentí más seguro del manejo e inicie la instalación manual, por cierto llegó un momento en que no podía entrar a Windows con WUBI entonces reseteé todo, tal vez ahí estuvo la falla. Tengo Windows 7.
Ahora cómo puedo arreglar esto?

---

### Post by BC59 on 2011-12-17
No es el Wubi pero da igual. 

En primer lugar haz un backup de todos tus archivos que no quieres perder. 

No se puede salvar la instalación de Ubuntu. Lo re-instalarás después. Por eso salva todo que tienes ahí dentro.

Luego empieza en Windows. Desde el sistema de discos duros y particiones, carga la primera particion por izquierda de Windows.

[IMG]http://ubuntuforums.org/picture.php?albumid=2453&pictureid=8309[/IMG]

Mucho cuidado no cargar las particiones de Windows como aparecen en la foto, system reserved y Windows NTFS.
Debes borrar la particion que aparecerá como desconocida y por la izquierda.

Después de eso, en el espacio creado intenta a reposicionar Windows de manera que ocupe todo el espacio libre.

Haz lo así y luego te explico como instalarás el Ubuntu.

---

### Post by SHAKAIM on 2011-12-17
Saludos
Eliminé la partición que indicaste, la que en la imagen esta en el extremo. En la siguiente, donde está Windows, es decir OS, no me permite extender el disco, está inhabilitada esa opción, será porque la que borré no esta en formato NTFS o aquellos que Windows permite? quiero decir si tratase de poner en esos formatos podría añadirla a OS?

[http://img6.imageshack.us/img6/9408/capturazs.png](http://img6.imageshack.us/img6/9408/capturazs.png)

---

### Post by BC59 on 2011-12-17
Esto es muy importante porque te vas a desplazar el windows hacia la izquierda, significa que desplazaras el sector boot. ¿No acepta con click derecho extender el volumen?

---

### Post by SHAKAIM on 2011-12-17
Exacto no me acepta o mejor dicho la opción no está habilitada haciendo click derecho

---

### Post by SHAKAIM on 2011-12-19
kintia@kintia-laptop:~$ sudo fdisk -l
[sudo] password for kintia: 

Disco /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador de disco: 0x98b324f9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2              13       36486   292968750    7  HPFS/NTFS
/dev/sda3           36486       63358   215843841    5  Extendida
La partición 3 no se inició en el limite físico del sector
/dev/sda5           36486       38918    19530752   83  Linux
/dev/sda6           38918       39042      999424   82  Linux swap / Solaris
/dev/sda7           39043       63358   195311616   83  Linux
kintia@kintia-laptop:~

Al final reinstalé UBUNTU, pero ahora sale este informe....

---

### Post by BC59 on 2011-12-19
El tema es muy complicado.
Aquí hay un problema parecido:
[http://ubuntuforums.org/showthread.php?t=1718074](http://ubuntuforums.org/showthread.php?t=1718074)
pero como lo veo lo han solucionado, formateando el Disco duro.
Espera si hay alguien en el forum con alguna solución mejor. 
Sino yo veo que hagas una imagen del Windows con Norton o con el sistema que tiene integrado y que formatees el disco. Después puedes instalar la imagen de Windows y por encima el Ubuntu.

---

### Post by SHAKAIM on 2011-12-19
OK Gracias!
Leìa que esto puede darse por usar programas gráficos y no aquellos como f disk que lo hacen de otra manera. Creo este problema es muy frecuente.
Ojalà pueda recibir màs comentarios y/o orientaciones.
Saludos

---

