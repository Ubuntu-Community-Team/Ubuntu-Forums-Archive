---
title: "&quot;Convocatoria&quot; para hacer tutorial de webcams"
date: 2009-05-15
forum: Comunidad
---

### Post by emiliano_raso on 2009-05-15
Todo surgió en base a esto:

> > **fedeavila said:**
> si, es todo un tema las webcams... yo igual la mía nunk la usé ni con windows ni sin windows, jamás me preocupé... =;

tendrían que hacer una lista con todas las que son compatibles y el "howto" para hacerlas funcionar...

mmm... Buena idea. Que te parece si lo hacemos? Empezamos a rejuntar informacion de internet y armamos un supertutorial de webcams.
A la gente que recien migra le ayudaria muchisimo.

Quien me ayuda a hacer ese tutorial?
Basicamente es hacer una lista de las webcams que funcionan y tutoriales de como hacerlas funcionar a las que no arrancan de una, dicho en criollo.

---

### Post by Hei Ku on 2009-05-15
Esta es la pagina oficial de la wiki de ubuntu sobre webcams:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Yo traduciría eso.

---

### Post by emiliano_raso on 2009-05-15
> **Hei Ku said:**
> Esta es la pagina oficial de la wiki de ubuntu sobre webcams:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Yo traduciría eso.

Opa. Interesante. No lo conocía. Estoy probando a ver si hago funcionar mi webcam xD

EDIT: Está super desactualizada esa pagina u.u Las repos del EasyCam son para Hardy, dice que el Camera Monitor no esta en las repos y si está.
Finalmente no me sirvió :-P

O sea acutaliza esa o hacemos un tuto casero xD

---

### Post by Hei Ku on 2009-05-15
Podrian actualizarla ustedes.

Por ejemplo, aca hay un tuto sobre como configurar la AspireOne, que recuerdo que alguien tenia problemas.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

A lo que me refiero es a que esas paginas no surgen por arte de magia, sino con el aporte de todos, y ese es un lugar al que llega mucho mas gente que a este foro.

---

### Post by emiliano_raso on 2009-05-15
> **Hei Ku said:**
> Podrian actualizarla ustedes.

Por ejemplo, aca hay un tuto sobre como configurar la AspireOne, que recuerdo que alguien tenia problemas.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

A lo que me refiero es a que esas paginas no surgen por arte de magia, sino con el aporte de todos, y ese es un lugar al que llega mucho mas gente que a este foro.

Momento... Podemos modificar eso nosotros? :-S
Sea como sea, no se como crear un repositorio, podriamos buscar info pero... QUE ALGUIEN ME AYUDEEE XD

---

### Post by Hei Ku on 2009-05-15
Teniendo cuenta de Launchpad podes modificar y crear paginas de la wiki. No se trata de crear un repositorio, sino de utilizar los que hay de manera inteligente.

---

### Post by emiliano_raso on 2009-05-15
> **Hei Ku said:**
> Teniendo cuenta de Launchpad podes modificar y crear paginas de la wiki. No se trata de crear un repositorio, sino de utilizar los que hay de manera inteligente.

Pero... en [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) dan estas repos para instalar EasyCam
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main

Son para hardy, como hago para usarlas en jaunty? La criollada de escribir jaunty en vez de hardy no funciona xD

---

### Post by Hei Ku on 2009-05-15
Entonces tendrán que compilar desde el código fuente original. Se baja el tar, configure, make, alien, etc. ;)

---

### Post by Hei Ku on 2009-05-15
También con una cuenta de Launchpad podes crear tu propio repositorio. Se llaman PPA, por Personal Package Archive.

---

### Post by emiliano_raso on 2009-05-15
> **Hei Ku said:**
> También con una cuenta de Launchpad podes crear tu propio repositorio. Se llaman PPA, por Personal Package Archive.

Okas. Gracias ^^

Pero Launchpad no está funcionando desde ayer a la tarde xD Cuando vuelva pruebo.

---

### Post by juancarlospaco on 2009-05-16
**[COLOR="Blue"][prism]("apt:/prism") [http://fonomo.com/]("http://fonomo.com/")[/COLOR]**

Con eso tenes Webcam en cualquier mensajero, desde Emesene hasta los de linea de comandos.
*Si quieren File Transfer avisen.*

Despues tambien yo he notado que varias camaras que no funcionan con programas como Cheese,
andan con WxCam no me preguntes por que, ...pero asi es.

---

### Post by emiliano_raso on 2009-05-16
> **juancarlospaco said:**
> **[COLOR="Blue"][prism]("apt:/prism") [http://fonomo.com/]("http://fonomo.com/")[/COLOR]**

Con eso tenes Webcam en cualquier mensajero, desde Emesene hasta los de linea de comandos.
*Si quieren File Transfer avisen.*

Despues tambien yo he notado que varias camaras que no funcionan con programas como Cheese,
andan con WxCam no me preguntes por que, ...pero asi es.

Bajé el .deb de WxCam y cuando lo ejecuto me dice esto:
> Error: La dependencia no se puede satisfacer: libmjpegtools0c2a (>= 1:1.8.0)

---

### Post by Hei Ku on 2009-05-16
instala esa dependencia. la buscaste en synaptic?

---

### Post by emiliano_raso on 2009-05-16
> **Hei Ku said:**
> instala esa dependencia. la buscaste en synaptic?

Si si, ya lo habia buscado y no aparece u.u

---

### Post by guillermolisi on 2009-05-16
> **emiliano_raso said:**
> Si si, ya lo habia buscado y no aparece u.u
Esa libreria esta hasta II, parece que aun no salio para JJ.

Mas info en [http://packages.ubuntu.com/search?keywords=libmjpegtools0c2a](http://packages.ubuntu.com/search?keywords=libmjpegtools0c2a)

---

### Post by Hei Ku on 2009-05-16
Podes probar en getdeb.net si esta el .deb de la biblioteca.

---

