---
title: "Ya tengo instalado Ubuntu, pero..."
date: 2008-05-23
forum: Comunidad
---

### Post by rxx266 on 2008-05-23
Bueno practicamente no configure casi nada solamente, el driver de la nvidia que me lo baje.Ahora pregunto me estan surgiendo algunas dudas, sobre la instalacion y borrado de programas, elijo mejor forma, compilo el programa para que mejor se adapte y optimice segun a mi arquitectura.Como veran me gusta renegar un poquito, o tal vez investigar por mi propia cuenta luego me saco las dudas, buscando info, bueno vayamos al grano, ubuntu ya viene con el GIMP, pero lo desintale poniendo $ sudo apt-get remove gimp funciono de maravilla lo desinstalo, verifique si se econtraba en el menu aplicacion/graficos y ya no se encontraba, inmediatamente, descargue el paquete fuente gimp usando $ sudo apt-get source gimp y me descarga 3 archivos:

gimp_2.4.5-1ubuntu2.dsc
gimp_2.4.5-1ubuntu2.diff.gz
gimp_2.4.5.orig.tar.gz

luego de descargarlos automaticamente,me descomprime el paquete, el comando dpkg-source, y me deja una carpeta llamada gimp-2.4.5, luego entro a la carpeta y ejecuto el comando $ sudo apt-get build-dep gimp, con eso obtengo las librerias necesaria, para el programa, por ultimo pasaria a compilar,pongo $ sudo ./configure, luego $ sudo make, y por ultimo $ sudo make install. por lo menos a mi me esta forma funcionando, pero quisiera corroborar si estoy haciendo bien las cosas.

Preguntas
1) Con que comando puedo verificar, donde se instala,la aplicacion? es decir que me muestra todas las ramas de directorios.
2) Si ya compile el programa, donde queda guardado el Binario?
3) Que consejos me dan o que deberia tener en cuenta gracias a todos.

---

### Post by sajnox on 2008-05-23
Con el punto 1 te puedo ayudar

```
whereis gimp
```

---

### Post by pol666 on 2008-05-23
Perdoname pero que laburo al divino p###

---

### Post by Mister X on 2008-05-23
> **pol666 said:**
> Perdoname pero que laburo al divino p###

No me parece. 
Lo que está haciendo es una buena forma de aprender.

---

### Post by Hei Ku on 2008-05-23
si vas a compilar, por que no bajas el programa desde la pagina oficial que seguramente va a estar mas actualizado????
O instalate Slackware :D

---

### Post by rxx266 on 2008-05-23
Bueno veo que ha generado interes, el post, pero segun la pagina ofcial de ubuntu, aclara muy bien que lo mejor para sacarle provecho, es compilar el programa.Les pido a la gente que postee con un argumento, y de ahi ver lo bueno y lo malo de cada cosa si no no tiene sentido, responder tales cosas como "me parece al reverendo ****" no tiene criterio. no aclara nada y no deja ningun mensaje constructivo gracias.

pd: la pregunta 2 y 3 please si alguien tiene algun dato gracias.

---

### Post by WanderingKnight on 2008-05-23
Bueno, está bueno compilar, pero si realmente te querés poner a hacer eso tenés que agarrar un distro como Gentoo que viene específicamente armado para que compiles todo.

La mayor ventaja de Ubuntu y de los distros basados en Debian es, justamente, la enorme cantidad de software precompilado disponible desde los repositorios.

---

### Post by Hei Ku on 2008-05-23
No es que sea inutil, sino que además rompes la utilidad del sistema de gestion de paquetes. O sea, estas rompiendo Ubuntu de a un paquete por vez. Hay distros que estan preparadas para eso, y por eso la recomendacion de que uses esas.

Respecto a la 2), queda guardado en donde el programa defina internamente que debe quedar guardado de acuerdo a la forma que lo instalaste. Si compilaste sin hacer un cambio de path en el configure, entonces va a quedar en el lugar definido por defecto, generalmente bajo /usr/bin para los ejecutables y otras rutas para archivos de configuracion, documentacion, etc.

Para la 3), antes de hacer un upgrade, desinstala todos los programas que compilaste, o vas a tener problemas. El proceso de upgrade asume que se instalo todo desde el gestor de paquetes. Y sacar los sources desde el gestor de paquetes no es lo optimo, porque las versiones estan mas desactualizadas, asi que tenes un codigo mas viejo que el que podrias tener si bajaras el source directamente desde la pagina del programa. Eso es por el tiempo que lleva entre la salida de una version y el momento en que se pone disponible como paquete. Como ejemplo muy cercano, KMyMoney esta en la version 0.9, pero para Hardy esta disponible la version 0.8.8-1 que es de fines del año pasado. Y la diferencia es grande en ese tiempo.

Como nota general, salvo para casos particulares, la mejora que logras es minima. El tiempo que ganes, lo perdes en la gestion manual que vas a tener que hacer.

---

### Post by pol666 on 2008-05-23
No te lo tomes a mal, te entiendo pero estas dando vueltas alrededor de una pista que es recta..

No se si me entendes pero si queres aprender a compilar o a adaptar en un debian o ubuntu es re contra al al pe**.

---

### Post by MeduZa on 2008-05-23
> **rxx266 said:**
> 
Preguntas
1) Con que comando puedo verificar, donde se instala,la aplicacion? es decir que me muestra todas las ramas de directorios.
2) Si ya compile el programa, donde queda guardado el Binario?
3) Que consejos me dan o que deberia tener en cuenta gracias a todos.

1) si no pusiste nada fue a parar a /usr/share creo por eso siempre es recomendable hacer ./configure --prefix=/usr

2) cuando compilas queda en la misma carpeta donde compilaste (en alguna de las subcarpertas nunca mire cual) y cuando haces sudo make install pasa a donde debe estar para ser ejecutado

3) primero lo que te dije en el paso 1 y segundo en vez de hacer make y make install uses checkinstall que te crea un .deb y es mas facil despues quitar el soft de tu sistema. y otra cosa que podes hacer si te gusta mucho compilar y tener lo ultimo es bajar el codigo de subversion o la pagina del proyecto.

Suerte.

---

### Post by rxx266 on 2008-05-24
Excelente, gracias a todos, buscando un poco de informacion en la red, econtre sobre este problema si realmente combiene o no compilar un kernel para nuesto equipo, leanlo y despues opinen como dato dejo que a partir de kernel 2.6 practiamente la mejora de rendimiento casi que no se ve,comparandola con un kernel precompilado.Voy a dejar 3 link el primero con el tema si comviene o no compilar, y el segundo es un procedimiento para compilar el kernel, y el tercero el concepto de Geek

1)[http://diegocg.blogspot.com/2005/12/razones-para-usar-kernels.html](http://diegocg.blogspot.com/2005/12/razones-para-usar-kernels.html)
2)[http://www.frikis.org/staticpages/index.php?page=kernel](http://www.frikis.org/staticpages/index.php?page=kernel)
3)[http://es.wikipedia.org/wiki/Geek](http://es.wikipedia.org/wiki/Geek)

PD:No dejen de leer nada, esto esta interesante para seguir desarrollandolo.Gentoo es un buena opcion,maneja paquetes no precompilados,
[http://es.wikipedia.org/wiki/Gentoo](http://es.wikipedia.org/wiki/Gentoo)

---

### Post by rxx266 on 2008-05-25
> **MeduZa said:**
> 1) si no pusiste nada fue a parar a /usr/share creo por eso siempre es recomendable hacer ./configure --prefix=/usr

2) cuando compilas queda en la misma carpeta donde compilaste (en alguna de las subcarpertas nunca mire cual) y cuando haces sudo make install pasa a donde debe estar para ser ejecutado

3) primero lo que te dije en el paso 1 y segundo en vez de hacer make y make install uses checkinstall que te crea un .deb y es mas facil despues quitar el soft de tu sistema. y otra cosa que podes hacer si te gusta mucho compilar y tener lo ultimo es bajar el codigo de subversion o la pagina del proyecto.

Suerte.

Recien termine de compilar Inkview no puse --prefix=/usr, y instalo el ejecutable /usr/local/bin vos que opinas que asigna todo mis programas a ese directorio o /usr/bin

---

### Post by MeduZa on 2008-05-26
> **rxx266 said:**
> Recien termine de compilar Inkview no puse --prefix=/usr, y instalo el ejecutable /usr/local/bin vos que opinas que asigna todo mis programas a ese directorio o /usr/bin

no dejalo asi si no te molesta, yo antes hacia eso pero no recuerdo que problema me traia :P

ahh que no andaban las cosas de una porque el path no estaba asigando, con asignar el path estas echo.

---

### Post by clasificado on 2008-05-27
> **MeduZa said:**
> /usr/local/bin

Siempre es un quilombo el donde es que deben ir los archivos, si en /bin, /usr/bin o /usr/local/bin y no hay una regla general sobre como trabajarlos.

Una manera es decir que /bin es lo necesario para usar la consola, /usr/bin queda a disposición del manejador de paquetes y /usr/local/bin es el lugar donde va todo lo que compila uno mismo.

clasificado

---

### Post by rxx266 on 2008-05-27
Voy a agregar un dato importante, nunca pongan asi:

./configure prefix=/usr/local/bin

Saben por que?, porque el ejecutable queda guardado en /usr/local/bin/bin, te crea otra carpeta bin, o sea hace un duplicado. la forma correcta es:

./configure prefix=/usr/local

---

