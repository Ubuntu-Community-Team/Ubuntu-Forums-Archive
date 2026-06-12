---
title: "Ubuntu-Co Metadistribución"
date: 2006-12-15
forum: Colombia Team - Colombia
---

### Post by cablop on 2006-12-15
Hola muchachos como están?

Primero decir que me gusta ya disponer de un foro oficial en Ubuntu.

Como les había comentado iba a crear un espacio en mi sitio web para que pudieramos adelantar elproyecto de la Metadistribución.

La dirección de la página es:
[B][http://www.cablop.quadragon.co.uk/floss/forum](http://www.cablop.quadragon.co.uk/floss/forum)
[/B]
La idea es hacer la parte de bosquejo y borrador en este espacio, y una vez que lo vayamos oficializando colocarlo aquí, en el foro oficial y en el wiki.

Hasta pronto.

---

### Post by wasert on 2007-01-06
hola

soy colombiano y quisiera saber un poco mas acerca del proyecto.  vivisté la página, pero no pude encontrar mucha información. gracias

---

### Post by leo1a0 on 2007-01-06
*"Coordinación y Creación de una metadistribución de ubuntu que satisfaga las necesidades de Colombia."*

me podrian explicar cuales son esas necesidades de Colombia que hacen que sea importante crear una meta distribucion? :confused: 

Que otra clase de software deberia tener aparte de los repositorios normales de Ubuntu? :confused: [-(

---

### Post by Nemesis Teufel on 2007-01-07
Me parece una idea interesante.

Creo que si bien, no se va a cambiar mucho el ubuntu original se puede optimizar bastante sacando los idiomas que no nos interesan, agregar los codecs de audio y video, quizá cambiar openoffice por abiword (aunque el soporte de .doc no sea el mejor, eso queda a su criterio).
Si queremos/quieren que el producto sea masivo y tenga una mayor difusión, se tendría que correr en toda maquina; todos sabemos que en los países tercermundistas de sudamérica todavía hay gente que no tiene una PC muy nueva. Quizá otra idea, aunque un poco mas compleja, seria crear dos metadistribuciones: una de Xfce con las aplicaciones básicas y necesarias y otra con Gnome (o Kde, la que les guste) para usuarios con un mejor hardware.

Supongo que faltaran muchas cosas, estas son las que se me ocurren.
Yo en su lugar, trataría de hacer un producto básico destinado a la educacion o empresas (los que siempren pagan licencia de windows), además que el usuario hogareño si terminara usando Ubuntu, se daría mas entusiasmo para personalizar y configurar su entorno con lo que mas le guste (abiword u openoffice; amarok o xmms; gaim o kopete; etc)

---

### Post by jairo.serrano on 2007-02-28
Podemos hacer una meta-distribución sin openOffice y con GnomeOffice o Koffice como prefieran, no veo porque nos cerraremos ;)

por cierto... Pidan que estoy regalando linux y paquetes que da miedo .. ejeje  ;) donde estan las listas de paquetes para organizar????

---

### Post by luis_lopez on 2007-02-28
> **leo1a0 said:**
> *"Coordinación y Creación de una metadistribución de ubuntu que satisfaga las necesidades de Colombia."*

me podrian explicar cuales son esas necesidades de Colombia que hacen que sea importante crear una meta distribucion? :confused: 

Que otra clase de software deberia tener aparte de los repositorios normales de Ubuntu? :confused: [-(

La idea es hacer un Live DVD o Cd que pueda ser utlizado en los festivales de instalacion en Colombia, especialmente en lugares en donde no haya conexion a internet. El usuario promedio de esta meta distro seria pues, aquella persona que no tiene acceso a internet (o acceso de baja velocidad) y para la cual el escenario de los repositorios normales no funcionaria....

---

### Post by luis_lopez on 2007-02-28
Para ir organizando un poco las cosas, voy a enumerar algunas de las caracteristicas del DVD que Jairo Serrano esta construyendo:

Herramienta: [COLOR="Blue"][Ubuntu Customization Kit 1.4 ]("http://uck.sourceforge.net")[/COLOR]

Distribucion Base: [COLOR="Blue"][Ubuntu Feisty Fawn  Herd 4]("http://www.ubuntu.com/testing/herd4")[/COLOR]

Listado inicial de paquetes: Disponible [COLOR="Blue"][aqui]("http://www.ubuntuforums.org/attachment.php?attachmentid=26346&d=1172697540")[/COLOR]

Metodologia de trabajo:

Mi propuesta es la siguiente: UCK dispone de una serie de scripts para automatizar la remasterizacion de un LiveCD/DVD, la documentacion acerca de como funcionan esta disponible [COLOR="Blue"][aqui]("http://svn.sourceforge.net/viewvc/*checkout*/uck/trunk/uck/docs/building-script.html")[/COLOR]. Se podria crear un repositorio central para el directorio mencionado en la documentacion y mediante cvs o svn, ir modificando la lista de paquetes a incluir. Con solo hacer un checkout del directorio, las personas interesadas en colaborar con el proyecto podrian remasterizar con la version mas reciente, si lo desean (y tienen acceso a modificar el repositorio) podrian colocar sus propias modificaciones (o tareas que les hayan sido previamente asignadas) y asi hacer mas colaborativo el proceso...

Otras ideas, comentarios?

---

### Post by jairo.serrano on 2007-03-01
Para el fin de semana tengo:

Edgy con las actualizaciones.
Paquetes en común acuerdo del Wiki de Ubuntu-co
Paquetes Extra.

Versiones:

[LIST]
[*]Ubuntu Edgy CD + Actualizaciones + Español por defecto.
[*]Kubuntu Edgy CD + Actualizaciones + Español por defecto.
[*]Xubuntu Edgy CD + Actualizaciones + Español por defecto.
[*]Ubuntu Edgy DVD + Actualizaciones + Español por defecto + Paquetes del Wiki + Paquetes de Diseño gráfico
[*]Kubuntu Edgy DVD + Actualizaciones + Español por defecto + Paquetes del Wiki + Paquetes de Diseño gráfico
[*]Xubuntu Edgy DVD + Actualizaciones + Español por defecto + Paquetes del Wiki + Paquetes de Diseño gráfico
[/LIST]


Todo esto es un **Creo que me alcanza el tiempo** :popcorn: 

El otro detalle es: Como lo distribuimos?
Probe con el KTorrent pero no me fue posible... (no se que paso)
Intentamos con AMule?

---

### Post by beuno on 2007-03-02
> **Nemesis Teufel said:**
> Me parece una idea interesante.

Creo que si bien, no se va a cambiar mucho el ubuntu original se puede optimizar bastante sacando los idiomas que no nos interesan, agregar los codecs de audio y video, quizá cambiar openoffice por abiword (aunque el soporte de .doc no sea el mejor, eso queda a su criterio).

Si, abiword por defecto con gnumeric.
Cada vez que instalo cambio el OO por esos dos.
Por otro lado, cambiar "gedit" por "leafpad" seria IDEAL.
El gedit tarda años en abrir, y el leafpad milisegundos.

¿Alguien conoce alguna calculadora mas rapida que la que viene con gnome?

Tambien es eterno para abrir...

---

### Post by cablop on 2007-03-05
Comencemos a discutir los paquetes que deben hacer parte de la distribución.

Primero: Deben ir los paquetes en español base y según aplicación, es decir KDE, Xubuntu, etc

Segundo: ¿Debemos eliminar los otros paquetes de idiomas (excepto el de inglés) para hacer más campo en el CD?

Deberíamos hasta hacer una votación

---

### Post by jairo.serrano on 2007-03-12
Votación? pa ke? :)

Primero lo primero:
[LIST=1]
[*]Adicionar paquetes del español
[*]Eliminar paquetes de otros idiomas
[*]adicionar codecs
[*]Adicionar los programas extras
[/LIST]

ahora cuales programas extras?

Inkscape
Planner
Koffice?
vlc

---

### Post by luis_lopez on 2007-03-20
De acuerdo contigo, como se organizaria la votacion?

Mi opinion es que deberiamos usar las herramienta de encuentas de launchpad. Solo los miembros del grupo votarian....

Ahora, acerca de los paquetes... Se podria hacer una encuesta por categoria, por ejemplo: como se deberia incluir soporte para formatos restringidos?

Otra opcion es simplemente hacer votacion de una aplicacion vs otra, por ejemplo: Amsn vs kopete vs gaim vs monkeymessenger...

---

### Post by cablop on 2007-03-20
Comencemos por definir los paquetes importantes y los paquetes que no deben hacer parte de la metadistribución... claro, entonces nos preguntamos ¿para que?

Entonces, empecemos por definir el para que...

Para las necesidades de Colombia... del usuario de Colombia, no de los linuxeros de Colombia...

Entonces necesitamos definir la Misión de la Meta-Distribución y el Publico Objetivo (Target Group).

Comencemos por definir el Target Group:[LIST=1]
[*]usuario residente en el interior del país (el usuario extranjero, per se, tiene necesidades diferentes)
[*]no conoce el inglés
[*]no tiene la capacidad tecnológica o económica para instalar los paquetes adicionales desde internet
[*]no ha estudiado ni programación ni sistemas
[*]busca un sistema fácil de instalar y que tiene TODO lo básico para dejar atrás Windows, por ejemplo[/LIST]También puede ser el usuario que busca emplear el sistema para tareas especificas:[LIST=1]
[*]Montar una oficina
[*]Montar un café internet
[*]Montar una sala de informática en un colegio[/LIST]¿Alguien define alguna otras características que tenga el usuario colombiano en Colombia?

---

### Post by dcantomo on 2007-03-20
Bueno Cablop de acuerdo menos en el punto de que no sabe sistemas, ya que por mas que queramos todavia Linux en cualquiera de sus distribuciones no alcanza a ser totalmente de usuario final y al usuario solo le queda resetear el equipo. Podriamos cambiarlo por conocimientos minimos en sistemas. No?

---

### Post by cablop on 2007-03-21
Quedo a mitad de camino entre describir al usuario como quien no conoce sistemas y como quien si los conoce...

Argumentos de porque conoce:[LIST]
[*]Obvio, para lidiar con Linux se debe saber algo de sistemas... ¿o no?
[*]Linux pide medirsele a veces a darle a la máquina a bajo nivel, línea de comandos, parametros, en fin...[/LIST]Argumentos de porque no conoce:[LIST]
[*]Cuando comenzamos con los sistemas no conociamos, ¿verdad? y a algunos de nosotros nos tocó arrancar desde el DOS, o el SH, o BASH, pasando por el Win3.1 o el X11 plano, pelado con WindowMaker.
[*]Si saben algo de sistemas... y no fue con linux, ¿significa que estamos esperando que ellos hayan aprendido sus bases y pinitos en sistemas... desde Windows?[/LIST]...

medito unos segundos

...

Citando a Dijkstra:
«Es prácticamente imposible enseñar programación correctamente a estudiantes que han estado expuestos al lenguaje BASIC con anterioridad. Como potenciales programadores, tienen la mente mutilada sin esperanza alguna de regeneración.»
Cambiemos BASIC por Windows y programador por usuario... y nos acercamos a la situación... Por supuesto, suena exagerado y fatalista por no decir fanático...

Pero visualicemos un entorno en el que la frase modificada pueda ser cierta...

Una comunidad indígena y un pueblo remoto, si a ambos los entrenamos primero en sistemas con Windows... los hemos perdido, sobre todo porque el aporte que estas comunidades pueden hacer y recibir de Linux se perdería irremediablemente, una vez hayan sido influenciados por el Software Privativo... No solo por su concepción del Software, sino porque esta gente sin conocer ningún software está innatamente más cercana a la filosofía de Ubuntu que lo que estará desúés de conocer Windows.

O un caso más cercano...
¿No ha bastado para nosotros estar unos pocos segundos frente a un equipo MAC (software aún más cerrado que el mismo Windows) y sentir envidia de lo que vemos ahí? ¿Acaso no hemos deseado tener entre nuestros haberes un MAC? Y eso que sabemos de sistemas...

Entonces creo que la frase correcta es:

El usuario sin o con pocos conocimientos de sistemas y que no ha estudiado  programación ni software.


Nota.- La cita de Dijkstra: [http://es.wikiquote.org/wiki/Edsger_Wybe_Dijkstra](http://es.wikiquote.org/wiki/Edsger_Wybe_Dijkstra)

---

### Post by luis_lopez on 2007-03-21
> **cablop said:**
> 

Una comunidad indígena y un pueblo remoto, si a ambos los entrenamos primero en sistemas con Windows... los hemos perdido, sobre todo porque el aporte que estas comunidades pueden hacer y recibir de Linux se perdería irremediablemente, una vez hayan sido influenciados por el Software Privativo... No solo por su concepción del Software, sino porque esta gente sin conocer ningún software está innatamente más cercana a la filosofía de Ubuntu que lo que estará después de conocer Windows.



No comparto tu opinion, de hecho en mi caso fui iniciado en sistemas en el mundo del software privativo y despues de entender como funcionaba la filosofia del software libre decidi aceptarlo. Estoy seguro de que habra muchos usuarios que aceptaran la filosofia del software libre una vez se les haya explicado en que consiste.

> 

O un caso más cercano...
¿No ha bastado para nosotros estar unos pocos segundos frente a un equipo MAC (software aún más cerrado que el mismo Windows) y sentir envidia de lo que vemos ahí? ¿Acaso no hemos deseado tener entre nuestros haberes un MAC? Y eso que sabemos de sistemas...


En este caso, a ese usuario se le puede facilmente convencer de usar Ogg Vorbis frente a MP3 una vez escuche la calidad del sonido

> 
Entonces creo que la frase correcta es:

El usuario sin o con pocos conocimientos de sistemas y que no ha estudiado  programación ni software.



Obviamente esta definicion no influencia de ninguna manera el listado de paquetes a incluir...

Porque no aplicamos el proceso de definicion de especificaciones que sigue ubuntu?

[https://wiki.ubuntu.com/FeatureSpecifications]("https://wiki.ubuntu.com/FeatureSpecifications")

---

### Post by cablop on 2007-03-31
> No comparto tu opinión, de hecho en mi caso fui iniciado en sistemas en el mundo del software privativo y después de entender como funcionaba la filosofía del software libre decidí aceptarlo. Estoy seguro de que habrá muchos usuarios que aceptaran la filosofía del software libre una vez se les haya explicado en que consiste.

No comparto esa idea... es que eso significa que... esperaremos a que ellos conozcan primero Windows antes de medírsele a Ubuntu..

> Obviamente esta definicion no influencia de ninguna manera el listado de paquetes a incluir...

mmmmm

Obviamente esta definicion SI influencia el listado de paquetes a incluir

definir el Usuario, es definir el Target Group, lo cual define las necesidades del CD de acuerdo a lo que el público necesita... no a lo que nosotros queramos...

>  Porque no aplicamos el proceso de definicion de especificaciones que sigue ubuntu?

[https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)

Voy a mirarla en este momento

---

### Post by cablop on 2007-03-31
> En este caso, a ese usuario se le puede facilmente convencer de usar Ogg Vorbis frente a MP3 una vez escuche la calidad del sonido

la verdad... eso es otra discusión, yo por ejemplo, poseoo más de 30GB en mp3... lo cual significa dos cosas
[LIST=1]
[*]no voy a ganar calidad volviéndolas ogg
[*]¿cuando voy a terminar de convertirlas?
[*]de todas maneras, para convertirlas, debo poder leer el formato mp3... ¿no?[/LIST]Si alguien me obliga a pasarme a ogg, lo dejaré de lado y me quedaré con una solución que me deje oir mi música y cursos actuales en vez de una que me obligue a borrarla del disco duro... y menos porque no es ilegal oir mp3 en el país...

Insisto, que nosotros queramos que el usuario escuche ogg no significa que el usuario deba oir ogg, el usuario tiene una necesidad diferente, necesita oir su música en el formato en que la tiene, por ejemplo

> Porque no aplicamos el proceso de definicion de especificaciones que sigue ubuntu?

[https://wiki.ubuntu.com/FeatureSpecifications](https://wiki.ubuntu.com/FeatureSpecifications)

Es bueno, pero me parece más orientado al desarrollo y por el momento solo queremos cambiar los paquetes que trae el ubuntu standard para ajustarlo a nuestras necesidades... o mejor dicho, a las necesidades de nuestro usuario en Colombia... es decir paquetes o features que ya pasaron por este proceso y ya hacen parte del Ubuntu
[]("https://wiki.ubuntu.com/FeatureSpecifications")

---

### Post by luis_lopez on 2007-05-02
> Es bueno, pero me parece más orientado al desarrollo y por el momento solo queremos cambiar los paquetes que trae el ubuntu standard para ajustarlo a nuestras necesidades... o mejor dicho, a las necesidades de nuestro usuario en Colombia... es decir paquetes o features que ya pasaron por este proceso y ya hacen parte del Ubuntu
[]("https://wiki.ubuntu.com/FeatureSpecifications")


Un ejemplo de una especificacion no orientada al desarrollo:

[https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-planet-editorial-policy]("https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-planet-editorial-policy")

La idea es usar el proceso, no necesariamente al pie de la letra, siguiendo los lineamientos (Summary, Rationale, Use Cases, Scope, Implementation, Outstanding issues, BoF Agenda and discussion, Comments) y obviamente los recursos de infraestructura que se tienen disponibles.

---

### Post by luisg on 2007-07-05
Aunque no pertezco al grupo de ubuntuco, me permito expresarles mi opinión al respecto:
1. Una persona que conoce Linux es capaz por sí sola de satisfacer sus propias necesidades. A quien le serviría el esfuerzo de la metadistribución es a aquellos que no tienen el conocimiento o las ganas de invertir tiempo en aprender del tema, no necesariamente completamente ignorantes sobre informática, pero sí personas que no están metidas en el tema.
2. Hay que reconocer el entorno colombiano: poco acceso a banda ancha, equipos desactualizados con muy poca RAM (hay cantidades de equipos con 128 y 256 MB), sin DVD, alta piratería de software MS y desconocimiento de alternativas opensource.
3. Teniendo en cuenta eso, yo sugeriría enfocar los esfuerzos a algun ambiente gráfico de poco consumo, por mucho XFCE, preferible Fluxbox o Icewm.
4. Los aplicativos de ofimática a incluir son un tema espinoso, por un lado sería conveniente el uso de alternativas livianas como Abiword o Gnumeric, pero por otro lado OOo tiene más funcionalidad y sobre todo compatibilidad con el omnipresente ms oriffice. Creo que se podrían dejar por defecto la alternativa liviana, dejando como opcionales las alternativas pesadas. Lo mismo se puede decir de Firefox...
5. Recordar que el no acceso a banda ancha es una limitante muy severa para el aprovechamiento de los repositorios de Ubuntu, así como de la aplicación de actualizaciones. Pienso que el producto final no debería necesariamente limitarse a un solo CD, sino que se debe incluir todo lo que sea necesario a mediano plazo, incluyendo cosas como drivers, juegos, amsn, compiladores (en caso de que se necesite para un paquete especial), software educativo, codecs, wine, etc., así las opciones queden en el CD 2. De cualquier manera, la configuración de los CDs que sean debe ser automática en el sources.list.
6. Debería considerarse la posibilidad de generar los CDs mediante versiones intermedias que adopten las actualizaciones de paquetes ya realizadas. Por ejemplo, generar ubuntuco 7.07 que incluirá los parches de Feisty hechos hasta Julio.

---

### Post by Rohen on 2007-07-11
Muchachos.... Porque no se calman... y mas bien trabajen juntos para compartir con las personas Colombianas que no conocen las alternativas de OpenSource Software.

Anywayz...  creo que seria excelente que se pusieran de acuerdo para ver como se puede hacer esto.  Yo no se absolutamente nada sobre programacion.  Pero hablo ingles 100%, Web Design, & SEO.

Si puedo ayudar en cualquier cosa me avisan... pero quisiera ver mas actividad en este thread.

[-o<

---

### Post by Rohen on 2007-07-16
hmmm.... looks like this "team" is off doing things on their own.

:(

---

### Post by luisg on 2007-07-29
> **Rohen said:**
> hmmm.... looks like this "team" is off doing things on their own.

:(

Sí, anda un poco lento este foro.

---

### Post by Takmadeus on 2007-08-01
> Muchachos.... Porque no se calman... y mas bien trabajen juntos para compartir con las personas Colombianas que no conocen las alternativas de OpenSource Software.

Anywayz... creo que seria excelente que se pusieran de acuerdo para ver como se puede hacer esto. Yo no se absolutamente nada sobre programacion. Pero hablo ingles 100%, Web Design, & SEO.

Si puedo ayudar en cualquier cosa me avisan... pero quisiera ver mas actividad en este thread.



Bueno.... la idea esta buena, por mi parte voy a comenzar a buscar pagiunas de foros Colombianas par ver quien y quien no usa linux y por ahi dewrecho promocionarlo ;)

Aqui en Armenia estoy haciendo un gran esfuerzo y aunque ha rendido uno que otro fruto, poco a poco la gente va considerando a ubuntu como una gran alternativa ;). Un evento inesperado (la reciente aparición de un monton de virus en los PCs de mi universidad) ha hecho que mucha gente se haya dado cuenta de que linux es una opción muy conveniente y segura ;) (todo por que con linux yo "desparasitaba" sus memorias USB).

---

