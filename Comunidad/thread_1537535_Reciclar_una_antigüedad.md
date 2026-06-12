---
title: "Reciclar una antigüedad"
date: 2010-07-23
forum: Comunidad
---

### Post by LolaMora on 2010-07-23
Holas a todos. :p
Tengo que ayudar a un amigo a poner en marcha una Pentium MMX 200 Mhz que le regalaron; es una de esas personas que reciclan y que están abiertas al cambio. No han visto funcionar los GNU/Linux pero saben de su existencia y les gusta la filosofía. Les comenté de instalarles un Ubuntu y aceptaron la sugerencia.

La ficha técnica de la PC es esta:
RAM 65536 kb
HD 4303 MB
Video 1024 kb 32 bit
Placa de red incorporada.
Acceso a banda ancha de telecentro.
Tiene instalado Win98 con problemas de configuración de drivers, por lo que no pueden acceder a internet.
El uso que le van a dar es con programas tipo: firefox, amsn, open office 

Que versión me recomiendan?

María

---

### Post by euzkoarima on 2010-07-23
Es realmente poca máquina, por eso en orden recomendaría:

1. [DeliLinux]("http://www.delilinux.de/")
2. [DLS]("http://www.damnsmalllinux.org/")
3. [Puppy]("http://www.puppylinux.com/")

La primera corre seguro. La segunda casi segura, la tercera puede ser.

Saludos,
Eduardo

---

### Post by guillermolisi on 2010-07-23
Oportunamente y con fines similares probe DSL (Damn Small Linux) y Puppy (una version de dos o tres años atras).

Recientemente volvi a probar Puppy 5.0 porque incluyeron los repositorios de Ubuntu y la verdad me parecio muy buena para alguien que ya tuvo una experiencia previa como usuario.
No es taaaan amigable como Ubuntu pero funciona y muy pero muy bien con 64Mb.

Es altamente configurable y permite tanto una ejecucion completamente funcional "on the fly" como una instalacion permanente. Tambien podria decirse que es portable ya que contempla guardar los archivos con las configuraciones en el medio removible que se este usando (siempre que sea regrabable).

---

### Post by mama21mama on 2010-07-24
Entra al [foro oficial]("http://www.murga-linux.com/puppy/index.php?f=24") de puppy y tendrás mejor soporte sobre el.

Seguramente [puppy 2.13 ]("http://mamalibre.eshost.com.ar/?q=content/nicolinux213-esta-basada-en-puppy-linux-versi%C3%B3n-213-en-espa%C3%B1ol-casi-en-su-totalidad") o el [4.3.1]("http://mamalibre.eshost.com.ar/?q=content/descargar-gnulinux"). La ultima en español; por que la 5 esta en ingles todavía.

[Como instalarlo]("http://mamalibre.eshost.com.ar/?q=content/puppy-linux-en-el-disco-duro").

Saludos

---

### Post by LolaMora on 2010-07-24
Me dedicaré a probar las opciones que me dieron porque no las conozco. En este caso, podré testear la facilidad de uso de los sistemas que pasaron.
Cuando tenga una opinión formada les cuento como me fue en la instalación y que me parecieron los Linux probados.
Les agradezco sus rápidas respuestas.

Saludos.
Maria.  :p

---

### Post by harryscode on 2010-07-24
Hola Lola, yo reciclè una antigüedad PI con 64kb de RAM y un video de 8mb sin acceso a red ya que no tiene placa con Slitaz. Es el único que pude hacer andar, Debo ser sincero con PuppyLinux, nunca pude hacer que quede instalado en el rigido. Probe Delinux, Puppy, y cuanta minidistro existe, y el que más me convenció fue Slitaz, baje el dvd con todos los packages y pude instalar todos los programas. Viene bien básico y despuès le instalas lo que queres. Para que no se achanche mucho esa pc, no le pongas OOffice, gnumeric y abiword andan bien y no consumen muchos recursos. 
Exitos

---

### Post by andy_91 on 2010-07-24
conozco una distro española basada en debian con ICEWM, roxfiler y Kazehakase en español.

Alguno me ayuda con el nombre??? eran dos proyectos que se unieron ???

Te la recomiendo, si encuentro el site te lo paso

Lo encontre, [http://minino.galpon.org/wiki/doku.php](http://minino.galpon.org/wiki/doku.php)

Se llama galpon minino y es la union de galpon mini y minino

---

### Post by biale on 2010-07-24
Yo parto de la base de que en PCs muy antiguas no se justifica invertir demasiado tiempo.

La idea de Puppy Linux en principio es "no instalar". O hacer una "instalación frugal" que a la larga es casi lo mismo. Se copia a Puppy en una partición, se le dice a Grub que lo arranque desde lo que sea, se descomprime al vuelo, y se crea un archivo de persistencia. No hay mas...

Cuando una PC no tiene lectora de CD ni hay un pendrive arrancable es casi la única solución. Puppy anda muy bien y es razonablemente sencillo de usar.

Con menos requerimientos DSL era mucho mas duro. Y Slitaz parecia funcionar muy bien, pero requería mas tiempo.

Edito: Y si no piensan usar editores y cosas raras hasta el SystemRescueCD permite acceder a la internet ("dochcp") cabledada con facilidad.

 
Mientras la memoria se lo banque, para empezar me inclino por Puppy.

Un saludo a todos.

---

### Post by alfplayer on 2010-07-24
> **biale said:**
> Yo parto de la base de que en PCs muy antiguas no se justifica invertir demasiado tiempo.

Es bueno este comentario. Mucha gente le dedica mucho tiempo, sin antes pensar cuál es el costo de la pc que están recuperando ni el costo de una más rápida y más moderna.

---

### Post by mama21mama on 2010-07-25
> **biale said:**
> 
La idea de Puppy Linux en principio es "no instalar". O hacer una "instalación frugal" que a la larga es casi lo mismo. 


Bueno no seria tan así.
Frugal consume mas que instalación normal; y por la escasa ram... seria conveniente instalación normal.

diccionario: instalación frugal :. como el modo live/cd/usb persistente en ubuntu.

---

### Post by EnriqueK on 2010-07-25
Estimo que el mayor problema que tendrás que afrontar es si vas a poder conseguir un DD de reemplazo , por que seguro que el que tiene debe estar sobrepasado en su vida útil y en cualquier momento va a fallar , por esta razón opino que si no podés conseguir un DD nuevo de reeplazo, mejor dejalo que será pérdida de tiempo.
Si grabás la ISO del Puppy sin cerrar la sesión. podés usarlo para guardar las modificaciones en multisesión, no es necesario que sean regrabaqbles, podés usar un CD-R pero repito. tenés que dejarlo abierto. de esta manera no usarás el disco duro

---

### Post by biale on 2010-07-26
Yo he tenido la experiencia opuesta: los HDD no han fallado tanto. Si las unidades de cd, por ejemplo. Por supuesto que igual almacenaría mis datos en el primer pendrive que aparezca. 

Salvo un error que ahora encuentro en el post original. El secreto de las distros livianas recide en usar aplicaciones livianas. Donde dice Open Office debería decir Abiword, también un navegador liviano en lugar de FFox y así siguiendo. No hay dramas en eso, todo queda mas usable de lo que se pensaría.

---

### Post by LolaMora on 2010-07-28
Probé Slitaz, y se quedó parado en la mitad del inicio del proceso LIVE (decía algo de kernel-help). Es una pena porque lo había testeado previamente en mi PC y me pareció muy amigable para quien viene de usar windows. Me gustó mucho esta distro.

Probé DSL, y funcionó bastante bien. Me faltó tiempo para ajustarle la configuración inicial de video y se veía mal. Pero se conectó a internet al toque. El uso del SO es mas complejo pero no quita que se adapten a él.

Al Delilinux lo tengo que instalar y todavía les falta tomar la decisión.

Me faltó probar el Puppy. 

En unos días les cuento como termina esta historia.

---

### Post by mama21mama on 2010-07-28
Hola,

anduve probando una que se llama **minino** --> [http://w2t.us/fd](http://w2t.us/fd) 
No es como mi favorito puppy 4.3.1 pero bue...

con probar no se pierde nada.

Saludos

---

### Post by euzkoarima on 2010-07-30
> **mama21mama said:**
> Hola,

anduve probando una que se llama **minino** --> [http://w2t.us/fd](http://w2t.us/fd) 
No es como mi favorito puppy 4.3.1 pero bue...

con probar no se pierde nada.

Saludos

Podrías comentar un poquito más sobre cual fué tu impresión de minino (vs puppy).

Explico el por qué mi pregunta: en una ONG [0] donan PC (con 64 Mb de RAM similar a lo de este post). Quieren salir de windows y entregar con soft libre. Los encaminé para puppy 4.3.1 pero después en este post vi todas las recomendaciones hechas y a minino lo vi como interesante.

[0] [Maria de las cárceles]("http://www.mariadelascarceles.org.ar/")

Saludos,
Eduardo

---

### Post by mama21mama on 2010-07-30
minino ocupa mas hardisk, unos 1.5gb
todavía no le encontré el botón de apagado xD
a comparación de puppy le falta pulir un montón de cosas.

puppy lo veo mas para usuarios únicos que se sentaran a la pc ya que siempre seras root.

en cambio minino por defecto trae para multiusuario.

pero si vemos quien consume menos recursos puppy creo que es el indicado.
El detalle que minino trae synaptic y apt-get o sea podes instalar desde terminal (ya que es un debian disfrazado).

puppy solo podes usar una GUI para instalar paquetes.
**Puppy** para entusiastas a mi parecer.
**Minino** puede llegar a ser para usuario final novatos.

es mi parecer pero hay que probar y sacar conclusiones.

---

### Post by euzkoarima on 2010-07-30
Gracias por los datos.

Saludos,
Eduardo

---

