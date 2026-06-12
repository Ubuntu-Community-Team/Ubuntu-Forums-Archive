---
title: "Ubuntu 10.04LTS + intel gma500"
date: 2010-05-04
forum: Comunidad
---

### Post by adriano_seth on 2010-05-04
Hola gente, el pasado 24 de abril asisti a FLISOL y los muchachos me instalaron el ubuntu 10.04 en mi netbook asus 1201HA, que posee un chipset intel GMA500 el cual no tiene drivers para linux, asi que no puedo mejorar la resolucion de video de la compu, ni hablar de activar los efectos del compiz. La cuestion es que esta es mi primera experiencia con linux y necesito algo de instruccion para realizar las actualizaciones manualmente o si tengo que montar algo por consola. Desde ya muchas gracias a todos.

---

### Post by guillermolisi on 2010-05-04
> **adriano_seth said:**
> Hola gente, el pasado 24 de abril asisti a FLISOL y los muchachos me instalaron el ubuntu 10.04 en mi netbook asus 1201HA, que posee un chipset intel GMA500 el cual no tiene drivers para linux, asi que no puedo mejorar la resolucion de video de la compu, ni hablar de activar los efectos del compiz. La cuestion es que esta es mi primera experiencia con linux y necesito algo de instruccion para realizar las actualizaciones manualmente o si tengo que montar algo por consola. Desde ya muchas gracias a todos.
Hola Adriano, Bienvenido !

Te recomiendo que leas estos enlaces que de a poco te van a ayudar en lo que quieras encarar:

[http://ubuntuforums.org/showthread.php?t=1007750](http://ubuntuforums.org/showthread.php?t=1007750)

[http://ubuntuforums.org/showthread.php?t=821950](http://ubuntuforums.org/showthread.php?t=821950)

[http://ubuntuforums.org/showthread.php?t=1283492](http://ubuntuforums.org/showthread.php?t=1283492)

Esto sin perjuicio que en cualquier momento alguien nos avise de una solucion para tu caso.

Sentite comodo y pregunta lo que necesites.

---

### Post by fedeavila on 2010-05-06
Hola, tengo el mismo equipo y el mismo problema. He googleado hasta cansarme y, por lo que vi, no hay solución de momento. Existen alternativas a Ubuntu, pero como ya lo dijeron por acá, no convence.. Está en 1024x768 así que no es TAAN desastrozo.. El problema es que no sólo afecta la resolución en sí, sino la performance en gral.

En fin, si hay alguna noticia (buena) avisenme!

---

### Post by guillermolisi on 2010-05-12
Gente

Les paso [este link a un blog]("http://www.internetling.com/2010/05/12/howto-intel-gma-500-poulsbo-on-ubuntu-10-04-lucid-lynx/") donde esta explicado que hay que hacer para que funcione razonablemente bien, con algunas mejoras pendientes, esta placa de video.

Si tienen inconvenientes con el idioma, avisan e intentamos una traduccion.

Hay casos de exito reportados asi que a animarse !

---

### Post by fedeavila on 2010-05-12
Funcionó!

No sé por qué pero copiando toda la línea me tiraba un error (creo que está de más el "./" al final

Bajé el archivito y "bash poulsbo_lucid.sh" y fue todo automático..

Lo único que cuando enciendo la máquina tengo que elegir el kernel viejo porque si elijo el nuevo me parpadea la pantalla un par de veces y queda como muerta.. Pero bueno, en fin.. No entendí qué es lo que hice pero anda de 10! Muchas gracias!

---

### Post by gonzar12 on 2010-05-20
Hola muchachos
les hago una pregunta
yo tambien tengo el mismo problema con esta netbook
cuando pongo la linea

*sudo apt-get remove --purge poulsbo-* psb-firmware psb-kernel-* xpsb-glx* xserver-xorg-video-psb* libdrm-poulsbo1* libva1 libva1-**

me responde esto

[I]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Nota, seleccionando libdrm-poulsbo1 para la expresión regular 'poulsbo-*'
Nota, seleccionando libdrm-poulsbo-dev para la expresión regular 'poulsbo-*'
Nota, seleccionando libdrm-poulsbo1-dbg para la expresión regular 'poulsbo-*'
Nota, seleccionando poulsbo-driver-2d para la expresión regular 'poulsbo-*'
Nota, seleccionando poulsbo-driver-3d para la expresión regular 'poulsbo-*'
Nota, seleccionando poulsbo-config para la expresión regular 'poulsbo-*'
El paquete psb-firmware no esta instalado, no se eliminará
Nota, seleccionando psb-kernel-source para la expresión regular 'psb-kernel-*'
Nota, seleccionando psb-kernel-headers para la expresión regular 'psb-kernel-*'
Nota, seleccionando xpsb-glx para la expresión regular 'xpsb-glx*'
E: No se pudo encontrar el paquete xpsb-glx*[/I]

la ultima linea me dice q no encuentra el paquete xpsb-glx*
instale el paquete xpsb-glx con

*sudo aptitude -y install psb-kernel-headers psb-kernel-source psb-modules xpsb-glx libdrm-poulsbo1 poulsbo-config psb-firmware*

y volvi a tirar el comando

*sudo apt-get remove --purge poulsbo-* psb-firmware psb-kernel-* xpsb-glx* xserver-xorg-video-psb* libdrm-poulsbo1* libva1 libva1-**

y ahora me dice 

[I]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Nota, seleccionando libdrm-poulsbo1 para la expresión regular 'poulsbo-*'
Nota, seleccionando libdrm-poulsbo-dev para la expresión regular 'poulsbo-*'
Nota, seleccionando libdrm-poulsbo1-dbg para la expresión regular 'poulsbo-*'
Nota, seleccionando poulsbo-driver-2d para la expresión regular 'poulsbo-*'
Nota, seleccionando poulsbo-driver-3d para la expresión regular 'poulsbo-*'
Nota, seleccionando poulsbo-config para la expresión regular 'poulsbo-*'
Nota, seleccionando psb-kernel-source para la expresión regular 'psb-kernel-*'
Nota, seleccionando psb-kernel-headers para la expresión regular 'psb-kernel-*'
Nota, seleccionando xpsb-glx para la expresión regular 'xpsb-glx*'
Nota, seleccionando xserver-xorg-video-psb para la expresión regular 'xserver-xorg-video-psb*'
E: No se pudo encontrar el paquete xserver-xorg-video-psb*
[/I]

intente instalar el paquete xserver-xorg-video-psb* pero no puedo
si alguien me da una mano se los voy a agradecer

---

### Post by gonzar12 on 2010-05-20
Me olvide...
les dejo un link de como instalar EEEPC ACPI que es con lo que podes poner el superhybrid como viene con el windows..tambien tiene otras cosas mas el lik pero no me sirvio
saldos
[http://www.tail-f.com.ar/2009/12/07/sistemas-operativos/gnu-linux/ubuntu-netbook-remix-en-eee-pc-1101ha.html](http://www.tail-f.com.ar/2009/12/07/sistemas-operativos/gnu-linux/ubuntu-netbook-remix-en-eee-pc-1101ha.html)

---

### Post by Fabrisio on 2012-03-04
Que tal!!!

Pues yo he intentado bajar el archivo con 

wget [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh)

y me manda esto:

fabrisio@Tamacolin:~$ wget [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh)
--2012-03-05 00:32:33--  [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo_lucid.sh)
Resolviendo dl.dropbox.com... 107.20.182.97, 107.20.198.68, 107.22.196.64, ...
Conectando a dl.dropbox.com|107.20.182.97|:80... conectado.
Petición HTTP enviada, esperando respuesta... 404 NOT FOUND
2012-03-05 00:33:14 ERROR 404: NOT FOUND.

Parece que ya no está disponible el parche. Al guno de ustedes sabe donde puedo bajarlo? O indicarme qué estoy haciendo mal?

Muchas gracias!!!

---

### Post by alfplayer on 2012-03-05
Desde el kernel 2.6.39 se incluye el driver psb-gfx. Tiene limitaciones pero puede servir. Creo que es para tener en cuenta.

---

