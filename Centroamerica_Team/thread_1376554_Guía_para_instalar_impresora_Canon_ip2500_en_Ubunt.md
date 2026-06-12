---
title: "Guía para instalar impresora Canon ip2500 en Ubuntu 9.10"
date: 2010-01-09
forum: Centroamerica Team
---

### Post by alexishevia on 2010-01-09
Hace poco le instalé Ubuntu 9.10 a una sobrina y todo corrió de maravilla, con la excepción de un printer Canon Pixma ip2500. Para no hacer el cuento largo, aquí está la solución de cómo logré que funcionara.

Primero hay que editar el archivo sources.list para añadir repositorios, usando este comando:
```
sudo gedit /etc/apt/sources.list
```Cuando se abre el archivo, añadir las siguientes lineas al final del mismo:
```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian ./
deb-src http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian ./
```Salvar y cerrar el archivo, y luego actualizar los repositorios con este comando:
```
sudo apt-get update
```Instalar los siguientes paquetes:
```
sudo apt-get install libcnbj-2.6
sudo apt-get install bjfilter-2.6
sudo apt-get install libpng3
```En este sitio: [http://www.sendspace.com/file/1ekvs5](http://www.sendspace.com/file/1ekvs5) se puede descargar un .zip que armé con los drivers de la impresora, hechos por Canon. Se darán cuenta que están en formato .rpm, por ende hay que convertirlos a .deb usando alien. Si no se tiene alien instalado, se puede instalar mediante este comando:
```
sudo apt-get install alien
```Navegar a la carpeta donde se extrajo el .zip, en mi caso estaba en el escritorio:
```
cd ~/Desktop/CanonIP2500
```Convertir a .deb:
```
sudo alien -d cnijfilter-common-2.70-2.src.rpm  --scripts
sudo alien -d cnijfilter-ip2500series-2.70-1.i386.rpm --scripts
```Los .deb generados deben estar en la misma carpeta de los .rpm originales. Instalar dándoles doble click, primero cnijfilter-common-2.70-2.src.deb y luego cnijfilter-ip2500series-2.70-1.i386.deb.

Ahora se debe mover manualmente el archivo pstocanonij al directorio /usr/lib/cups/filter/ :
```
sudo mv ./pstocanonij /usr/lib/cups/filter/pstocanonij
sudo chown root:root /usr/lib/cups/filter/pstocanonij
sudo chmod u+x /usr/lib/cups/filter/pstocanonij
```Para que el sistema lea los archivos correctamente, se deben crear algunos enlaces simbólicos:
```
cd /usr/lib
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libcnbpcmcm311.so.6.50.1 libcnbpcmcm311.so
sudo ln -s libcnbpess311.so.3.0.9 libcnbpess311.so
sudo ln -s libcnbpcnclapi311.so.3.3.0 libcnbpcnclapi311.so
sudo ln -s libcnbpcnclbjcmd311.so.3.3.0 libcnbpcnclbjcmd311.so
sudo ln -s libcnbpcnclui311.so.3.3.0 libcnbpcnclui311.so
```Para revisar que todo esté bien, ejecutar lo siguiente:
```
cd /usr/local/bin
ldd cifip2500
```Debe mostrar un resultado como el siguiente:
```
linux-gate.so.1 =>  (0xb8015000)
libcnbpcmcm311.so => /usr/lib/libcnbpcmcm311.so (0xb7ff6000)
libcnbpess311.so => /usr/lib/libcnbpess311.so (0xb7fae000)
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f87000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f83000)
libtiff.so.3 => /usr/lib/libtiff.so.3 (0xb7f2d000)
libpng.so.3 => /usr/lib/libpng.so.3 (0xb7f07000)
libcnbpcnclapi311.so => /usr/lib/libcnbpcnclapi311.so (0xb7f02000)
libcnbpcnclbjcmd311.so => /usr/lib/libcnbpcnclbjcmd311.so (0xb7efc000)
libcnbpcnclui311.so => /usr/lib/libcnbpcnclui311.so (0xb7ef6000)
libpopt.so.0 => /lib/libpopt.so.0 (0xb7eec000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d89000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7d70000)
/lib/ld-linux.so.2 (0xb8016000)
libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7d50000)
libz.so.1 => /lib/libz.so.1 (0xb7d39000)
```Reiniciar.
Abrir el browser y apuntar a la siguiente dirección: [http://localhost:631](http://localhost:631)
Hacer click en Añadir impresora y seguir las instrucciones.
Cuando el sistema pregunte por el driver, buscar la opción de "Seleccionar PPD".
Moverse a la carpeta /usr/share/cups/model/ y escoger el archivo canonip2500.ppd

Después de reiniciar nuevamente la impresora debe trabajar sin problemas.

---

### Post by Nugar on 2010-01-09
Aunque no uso esa impresoa en particular, gracias por la excelente guía!

Saludos,

---

