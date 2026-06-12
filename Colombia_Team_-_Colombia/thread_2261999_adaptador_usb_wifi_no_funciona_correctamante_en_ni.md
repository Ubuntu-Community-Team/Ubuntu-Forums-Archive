---
title: "adaptador usb wifi no funciona correctamante en ninguna distro"
date: 2015-01-22
forum: Colombia Team - Colombia
---

### Post by karlitozebc on 2015-01-22
Hola, mi experiencia en linux es basica, tengo un pc de escritorio, en el cual le tengo conectado a un puerto usb un adaptador usb-wifi ENCORE ENWUI 1X45 ( [http://www.encore-usa.com/co/taxonomy/term/449/all](http://www.encore-usa.com/co/taxonomy/term/449/all) ) para poder recibir la señal wifi del modem en mi pc de escritorio, ya que el este está muy lejos del modem y no puedo regar cable desde el modem hasta el pc; pero resulta que con ninguna de las distros linux que he probado funciona correctamente, la señal siempre es intermitente, en un momento tengo internet, pero al rato se ha desconectado, quisiera saber si me pueden ayudar con eso, distros probadas, ubuntu, fedora, opensuse, debian, manjaro, aclaro que el adaptador viene con su cd de instalación con los drivers para windows, mac osx y linux, pero en linux no los he podido instalar, en el mismo pc tengo 2 discos duros, uno exclusivo para Mac OSX mavericks, y el otro particionado para windows y para linux.

la distro de turno es MANJARO 0.8.11, con la cual aparentemente habia resuelto el problema instalando el respectivo repositorio de drivers para REALTEK, pero al igual q con las anteriores distros funciono bien algunos minutos y despues se cae, y es peor con esta distro, porque ni siquiera puedo reconectar nuevamente la señal wi-fi.

en el cd de instalacion, viene la carpeta con los drivers para Linux, pero no he podido instalarlos, porque me declaro un ignorante en el tema.

Dentro de la carpeta de "Linux" (del CD), vienen las subcarpetas: "document", "driver" y "wpa_supplicant"; tambien un archivo "install.sh"; uno "readme.txt" y uno ReleaseNotes.doc"; dentro de la subcarpeta "driver", viene un archivo comprimido .tar.gz llamado: rtl8192CU_linux_v2.0.1126.20101020.tar.gz, al descomprimir el archivo .tar.gz encuentro una carpeta del mismo nombre (rtl8192CU_linux_v2.0.1126.20101020), la cual contiene mas subcarpetas y mas archivos, pero no he podido instalarla, a pesar de que he leido varios tutos sobre el manejo de archivos .tar.gz.

Quesiera que por favro alguien me ayude con este tema, gracias.


Gracias

---

### Post by Ricardo_Velasco on 2015-11-25
Saludos:

Intentare ayudarte con este tema:

Bueno aqui vi y te entendi que tu ya tienes el CD de instalacion del driver para tu USB Wireless?? Me doy a entender..

Entonces como ya tienes el driver te voy a decir lo que tienes que hacer..

Primero en la terminal copias todos esos archivos del CD y los pones en algun lugar de tu carpeta personal.. 

Entonces con esta carpeta de archivos entras por terminal un ejemplo:

> cd /Descargas/

> cd carpeta que creaste con los drivers/

Luego de eso como tu mismo dijiste existe un archivo install.sh..

Eso significa que ese es el script para que tu puedas ejecutar la instalacion..

Entonces lo que tu haces es lo siguiente:

Dentro de la carpeta en la terminal pones:

> ./install.sh

Pero antes de todo tienes que tener permitos de superusuario ejecutas en la terminal:

> sudo su

Tu password de Root

Y ahi sigues todos los pasos dichos..

Luego de ahi se te ejecutara un script y luego tendras la instalacion completada..

Porfavor me copias el texto que aparece en el archivo README.txt

PD: Si causo algun problema por revivir un post antiguo porfavor haganmelo llegar..

Muchas gracias

---

