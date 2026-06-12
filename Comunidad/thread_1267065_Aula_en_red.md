---
title: "Aula en red"
date: 2009-09-15
forum: Comunidad
---

### Post by LolaMora on 2009-09-15
Hola a todos.
Soy docente de escuela pública (GCBA). 
Trabajo en capacitación de adultos y estoy cansada (por decirlo de una manera elegante y educada) de instruir a futuros trabajadores en herramientas que pertenecen a MicroSoft exclusivamente.

Tengo proyectado para el ciclo lectivo 2010, instruir a personas en GNU/Linux en vez de windows. Con ello se puede incentivar el uso del Software Libre, fomentar su filosofía y ya que estamos tratar que migren en lo posible para estos lugares.

Esta formación de adultos estaría orientada a ofimática, internet y diseño gráfico.

Lo que necesito es armar mi aula como una subred. He estado buscando un "como/manual/tutorial" y hay muchos, pero no sé cual se adapta mejor para mi colegio.

Estuve leyendo este hilo:
[http://ubuntuforums.org/showthread.php?t=1192926&highlight=escritorio+remoto&page=3](http://ubuntuforums.org/showthread.php?t=1192926&highlight=escritorio+remoto&page=3) de JuanCarlosPaco. 
Me pareció de lo mas interesante, pero es diferente a nuestro caso.

Nosotros tenemos acceso a internet a través de un router. Este router conecta a un switch. El switch distribuye a todas las aulas de computación que son 4 en total. Cada aula tiene 10 u 11 pcs y placa de red en cada maquina.
No tenemos expertos ni especialistas, solo buenas personas con buenas intenciones.

La subred estaría en mi aula (por ahora). 
Todas estas pcs tienen arranque dual con Ubuntu 9.04 y winXP. La pc-profesor tiene en este momento nfs-server y las demas nfs-common. Pero hay problemas para que vean la carpeta compartida. :confused:

Si conocen cual es el manual que se adapte mejor a las necesidades de mi colegio, manden la dirección. 
Les quedamos muy agradecidos desde ya.

---

### Post by guillermolisi on 2009-09-15
LolaMora

Hay experiencias similares en escuelas publicas, tanto en Capital Federal como en el GBA, en las que usaron LTS (Light Terminal Server) y que posibilita contar con una maquina (server) que permite monitorear y/o interactuar con cada PC de alumno (cliente).

Recuerdo una presentacion en las jornadas EPUEL del año pasado en la cual Javier Castrillo (si buscas en Google encontraras informacion sobre el y sus proyectos) hizo una muy buena presentacion sobre ese proyecto y su aplicacion practica.

Si no es esto lo que estas buscando sino soporte de infraestructura .. ese es otro tema.

---

### Post by juancarlospaco on 2009-09-15
La verdad es que es mas simple de lo que parece,
te diria espera hasta que salga la 9.10 Karmic Koala,
que te va a resultar mas facil en muchos aspectos,
la critica constructiva de la gente en los Paper Cuts la ha pulido mucho.

Para ofimatica con el OpenOffice completo alcanza y sobra,
por la parte de diseño gráfico tenes el Gimp, el Inkscape que son muy buenos.

Pero asi mismo no entiendo si queres manual para instalarlo o para enseñarlo...

Con esa configuracion de red, pones un Ubuntu y sale andando.

Yo uso mas SSH que NFS para los archivos, 
viste que se puede usar para compartir todo tambien.

Ejemplo: 
Lugares--->Conectar con el Servidor--->Tipo de Servicio--->SSH
Tildar "Añadir Marcador", poner los datos necesarios, y conectar.


[click aca instala SSH-Server para la PC profesor]("apt:/openssh-server")

[click aca instala iTalc-Master para la PC profesor]("apt:/italc-master")
[URL="apt:/italc-client"]
click aca instala iTalc-client para las PC alumnos[/URL]

[I][SIZE="1"]Para el iTalc hay que copiar unas llaves de la PC del Profesor a todas las PC de alumnos,
yo no lo recuerdo pero en la web de italc dice, 
es sencillo como copiar un archivo de una pc a otra con un pendrive.[/SIZE][/I]


Comentanos si queres saber como instalarlo o como enseñarlo para poder seguir orientandote mas alla...

:)

---

### Post by LolaMora on 2009-09-15
Gracias Guillermo, estoy buscando y leyendo por donde me sugeriste.

Juan Carlos
Me contestaste todas mis dudas: 
asesoramiento sobre que paquetes necesito (me nombraste ssh e iTalc), 
y lo mas duro para mi que es la parte hardware; no tenía idea que se podía hacer con las aulas y tipo de red que tenemos.

Los manuales de instalación y administración de estos softwares los puedo buscar yo.

Los viernes le hago mantenimiento al aula. Después te cuento como me va, es muuuuuy probable que necesite preguntar mas cosas.

Con respecto al material didáctico, :( he estado enseñando 15 años MS Office :(  y tengo organizado este asunto. 

Lo que no les dije todavia es que me abrieron un nuevo curso de Operador Linux Basico en el que estoy enseñado a usar las pcs con Ubuntu instalado.
Estoy siguiendo el programa, pero me gustaría saber como se da en otros lados. 
Tal vez conozcas algún sitio que me puedas pasar.

Muchas gracias por sus respuestas. Hasta pronto.

---

### Post by faktorqm on 2009-09-18
[QUOTE=juancarlospaco;7954863]
Yo uso mas SSH que NFS para los archivos, 
viste que se puede usar para compartir todo tambien.
QUOTE]

¿No habras querido decir SFTP? SSH es la consola no mas. SFTP es lo que trae ya habilitado el server SSH para que puedas compartir archivos. Te corrijo esto no de mala onda, sino para el que viene atras no se piense que ssh aparte de consola es un protocolo de transferencia de archivos. 

lolamora: interesante el proyecto, pregunta todas tus dudas en la seccion software/hardware que con gusto te responderemos. Salu2!

---

### Post by juancarlospaco on 2009-09-18
Si..., adentro de SSH podes meter lo que se te ocurra, 
la X tampoco es de SSH y sin embargo se puede usar igual,
podes ejecutar programas graficos remotos con SSH, 
tambien protocolos inseguros para hacerlos seguros como Telnet o RDP,
es como un tunel cifrado, como una vpn ad-hoc, 
...pero ya nos fuimos en tenicismos.  :)

---

### Post by edudelsur on 2009-11-03
que tal LolaMora yo estoy tratando de implementar algo parecido en provincia de Bs.As. en varias escuelas de zona oeste nosotros no tenemos internet por ahora lo que conseguí es conectar todas las máquinas (instaladas con Ubuntu 8.04) del aula, a una con Winxp en la que tengo páginas web. y trabajo así. quisiera hacerlo todo en Ubuntu pero todavía no lo consigo. si te sirve podemos intercambiar experiencias, aunque yo trabajo en poimodal.
Saludos

---

### Post by edudelsur on 2009-11-03
> **juancarlospaco said:**
> La verdad es que es mas simple de lo que parece,
te diria espera hasta que salga la 9.10 Karmic Koala,
que te va a resultar mas facil en muchos aspectos,
la critica constructiva de la gente en los Paper Cuts la ha pulido mucho.

Para ofimatica con el OpenOffice completo alcanza y sobra,
por la parte de diseño gráfico tenes el Gimp, el Inkscape que son muy buenos.

Pero asi mismo no entiendo si queres manual para instalarlo o para enseñarlo...

Con esa configuracion de red, pones un Ubuntu y sale andando.

Yo uso mas SSH que NFS para los archivos, 
viste que se puede usar para compartir todo tambien.

Ejemplo: 
Lugares--->Conectar con el Servidor--->Tipo de Servicio--->SSH
Tildar "Añadir Marcador", poner los datos necesarios, y conectar.


[click aca instala SSH-Server para la PC profesor]("apt:/openssh-server")

[click aca instala iTalc-Master para la PC profesor]("apt:/italc-master")
[URL="apt:/italc-client"]
click aca instala iTalc-client para las PC alumnos[/URL]

[I][SIZE=1]Para el iTalc hay que copiar unas llaves de la PC del Profesor a todas las PC de alumnos,
yo no lo recuerdo pero en la web de italc dice, 
es sencillo como copiar un archivo de una pc a otra con un pendrive.[/SIZE][/I]


Comentanos si queres saber como instalarlo o como enseñarlo para poder seguir orientandote mas alla...

:)
Que tal juan carlos por lo que veo la tenes re clara, te copas en hacernos un tutorial de como conseguir una red tipo grupo de trabajo. con ubuntu.
gracias!!

---

### Post by LolaMora on 2009-11-03
Hola Edu del sur
Yo tambien soy del sur. 

Estoy en la etapa de detectar conflictos en la red del colegio. Como no contamos con técnicos especializados ni administradores de redes, y los que estamos hacemos lo que podemos, las respuestas y soluciones llegan muy lentamente.

Como vos ya sabrás: en la educación pública nunca hay un peso que sobre.

Busque info sobre lo que ha sugerido Juan Carlos Paco mas arriba, y se ve de lo mas interesante. Pero no lo pude probar todavía porque cuando arranco cualquier PC con Ubuntu no veo al resto de PCs ubuntu. Cuando uso escritorios remotos, le puedo manejar los comandos a distancia a una sola PC, pero no sale lo que le estoy haciendo en mi pantalla (es como trabajar a ciegas).

Y lo peor de todo es que si puedo ver todos los  dispositivos de las PCs windows (y las veo demasiado bien).

Estoy leyendo cuanto puedo sobre armado de redes y configuración de servidores. 

Si instalamos un servidor necesitamos un administradorde redes y no hay personal con tiempo (ni conocimiento) para esa tarea.

Esta es nuestra experiencia hasta ahora. Seguiré posteando novedades mas adelante.

Saludos.

---

