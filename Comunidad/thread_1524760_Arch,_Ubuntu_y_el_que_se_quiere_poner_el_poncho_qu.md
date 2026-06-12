---
title: "Arch, Ubuntu y el que se quiere poner el poncho que se lo ponga!"
date: 2010-07-05
forum: Comunidad
---

### Post by guidito73 on 2010-07-05
Bueno, hace un tiempito me instalé Arch en unas particiones que hice por ahí. Primeramente le instalé KDE, y mientras que es MUCHÍSIMO más rápido que Kubuntu, aún seguía sin gustarme tanto como Gnome (en gran parte por las aplicaciones: me gusta más Emesene que Kmess, Exaile que Amarok, etc).

Desinstalé KDE y puse Gnome (con un par de comandos no más, Pacman es una MASA), todo lindo, pero muy básico, algunos problemas configurando Compiz, otros con el cursor... y sobre todo, la lentitud notable de HAL.

Ahora, ando alternando entre mi Ubuntu y Arch. No sé con cuál quedarme. Ubuntu está hermoso, rapidísimo como nunca, estable. Compiz, una brisa. Pero siento que andar añadiendo PPAs que se rompen, que joden, etc me molesta y soy un obsesionado en tener todo actualizado al mango. Una rolling release de algo así sería genial, no quiero instalar 10.10 y que no traiga Gnome 3 instalado!

En fin, que si alguien me puede dar algo de luz en todo esto (opiniones, bah), por ahí como para tener una segunda voz además de mi dicotomía entre "LO HORRIBLE DE HAL y LO HORRIBLE DE SENTIRME DESACTUALIZADO".

---

### Post by EnriqueK on 2010-07-06
En mi opinión, las versiones nuevas de programas no necesariamente son mejores que las mas antiguas, no se si estaré equivocado pero pienso que las versiones nuevas están mas ligadas a por ejemplo a versiones nuevas de los entornos gráficos y que por eso de las librerías compartidas obligan a hacer uso de estas que en muchos casos se tuvieron que actualizar para satisfacer necesidades de otros programas , pero no necesariamente para el programa en cuestión, en mi caso por ejemplo. tengo instalada versiones antiguas de varios programas por que las nuevas versiones funcionan francamente mal.

---

### Post by guidito73 on 2010-07-06
> **EnriqueK said:**
> En mi opinión, las versiones nuevas de programas no necesariamente son mejores que las mas antiguas, no se si estaré equivocado pero pienso que las versiones nuevas están mas ligadas a por ejemplo a versiones nuevas de los entornos gráficos y que por eso de las librerías compartidas obligan a hacer uso de estas que en muchos casos se tuvieron que actualizar para satisfacer necesidades de otros programas , pero no necesariamente para el programa en cuestión, en mi caso por ejemplo. tengo instalada versiones antiguas de varios programas por que las nuevas versiones funcionan francamente mal.

Está bien, pero ese es tu caso. En el mío, me gusta que esté TODO actualizado a lo máximo posible (tampoco como para usar los repos testing de Arch). En principio creo que voy a hacer una instalación limpia de Arch y ver si puedo usar udev en vez de HAL para sentirme un poco mejor.

Alguien con alguna experiencia en la optimización de Arch?

---

### Post by juancarlospaco on 2010-07-06
No hay Gnome 3, 
Arch no es estable ni seguro, por eso no tiene ni Boletin de Seguridad Oficial,
nadie parcha nada, ...si no te anda manejate, 
algun workaround o deshabilitarlo hasta que salga la proxima version.

---

### Post by guidito73 on 2010-07-06
> **juancarlospaco said:**
> No hay Gnome 3, 
Arch no es estable ni seguro, por eso no tiene ni Boletin de Seguridad Oficial,
nadie parcha nada, ...si no te anda manejate, 
algun workaround o deshabilitarlo hasta que salga la proxima version.

Che, de onda, si llegué a instalar Arch, no te parece que sabría que Gnome 3 sale en septiembre y que Ubuntu 10.10 no lo va a traer?

No tengo problemas para arreglar las cosas, no tuve ningun error grave y la verdad, aprendí muchisimo más de cómo funciona Linux en Arch que en Ubuntu.

Pero esto no se trata de una flame war, simplemente quiero saber (porque sé que un par de acá se manejan con Arch) cómo llegar a hacer de tu experiencia con Arch algo parecido a lo que sentimos con Ubuntu cuando recién ingresamos.

---

### Post by totolinux on 2010-07-06
hola: yo usé arch un tiempo, pero no logro comprender del todo el tema de pacman. Al instalar todo bien, pero en las actualizaciones se cambian los repositorios no se. Se va todo al diablo. 
Luego probé chacra (arch live con kde4) esta espectacular pero el mismo tema se complica me dice que tengo 460 actualizaciones y no pasa nada no puedo act. ni en la consola. 
Es verdad se aprende mucho pero a mi me superó y vuelvo a ubuntu y digo que bueno, que lindo, que simple, que rápido, cuanta comunidad y soporte
Lo que me gusta de arch es la instalación mínima (kdemod me fascina)..

---

### Post by EnriqueK on 2010-07-06
Si vale de algo mi experiencia en la que vengo usando todas las versiones de Ubuntu a partir de la 6.10, te puedo decir que por lo general no noto cambios positivos entre versión a versión. por el contrario, te puedo decir que hay programas que dejaron de tener soporte en las nuevas  versiones, seguramente por los que los desarrolladores de estos simplemente colgaron los botines 
ante la aparición  de nuevas versiones de gtk o de kde  que en mi opinión estos entornos gráficos están concentrando sus esfuerzos en los aspectos visuales y no en mejorar la integracion gráfica con el sistema, lo que es la razón principal ser de dichos escritorios.
Si lo anterior pasa con Ubuntu y sus diferentes versiones, ni quiero imaginarme lo que debe ocurrir con ARCH  y no hablemos de que si o si debes tener muy buen ancho de banda para poder descargar todos los días cientos de megas en actualizaciones para que todo siga igual o peor que antes.
Otra cosa, recientemente descargué el Alfa2 del futiro Ubuntu 10.10 ,  arrancó sin prblemas y todo funciona bie, pero  ejecuté **lsmod** para ver los módulos del kernel que están cargados, me encuentro que allí figura **nouveau** , que es el nuevo cotrolador libre para tarjetas Nvidia y que muchas quejas está ocacionando en diastros que lo implentaron. A los moderadores de foro del pido que vayam preparando tutos que explique como eliminar o desactivar el módulo Nouveau en la futura versión de Uvubtu 10.10 , vaticino que las quejas serán muchísimas.

---

### Post by oktubrer on 2010-07-06
> **juancarlospaco said:**
> No hay Gnome 3, 
Arch no es estable ni seguro, por eso no tiene ni Boletin de Seguridad Oficial,
nadie parcha nada, ...si no te anda manejate, 
algun workaround o deshabilitarlo hasta que salga la proxima version.

Me veo obligado a responder que esto no es cierto.  
- Arch es tan estable y seguro como uno quiere que sea, como casi cualquier distribución de Gnu/Linux.  
- Hay una wiki oficial excelente con tutoriales y soluciones a errores comunes, además de un foro casi con el mismo movimiento que este maravilloso foro de Ubuntu.
- Que sea rolling release no significa que sea obligatorio actualizar todos los paquetes, ni todo el tiempo, tal como tampoco es necesario en Ubuntu actualizar de versión.  Es optativo.  Free as in freedom =D
Aclaro más que nada para el que nunca escuchó hablar de Arch y se puede llevar la impresión equivocada.  Perdón si termina en flamewar, prometo no contestar más por las dudas.

Respecto a la pregunta original, comparto tu descontento con HAL, asumo que en algún momento se dejará de usar, pero falta.  Por eso sigo con el dual boot entre mis dos distribuciones favoritas. ;)

---

### Post by biale on 2010-07-06
Pegarse a la cresta de la ola significa experimentar y yo no encuentro nada de malo en hacerlo. Los problemas solo comienzan cuando uno confunde "lo que eventualmente podría llegar funcionar bien" con "lo que necesariamente debería funcionar bien".

Si vale o no vale la pena es otro tema. Aqui mi modesta opinión coincide con la de EnriqueK.

Mas aún, no estoy muy convencido en el desarrollo y en la evolución de los aconteciemientos. Creo que la ganancia no siempre ha balanceado el incremento en la complejidad (hipertrofia). Y a veces hasta encuentro controversia de objetivos y una expresión de mermas.

El software privativo tiene una necesidad de vender. Si no cambia los farolitos cuadrados por redondos no genera un nuevo producto y no vende. ¿El software libre?

Por ejemplo, si Gnome 3 imita lo bueno de KDE vamos bien. En cambio si la idea fuera "simplificar la imágen de Nautilus"...

Un saludo a todos.

---

### Post by alfplayer on 2010-07-06
> **oktubrer said:**
> Me veo obligado a responder que esto no es cierto.  
- Arch es tan estable y seguro como uno quiere que sea, como casi cualquier distribución de Gnu/Linux.  
- Hay una wiki oficial excelente con tutoriales y soluciones a errores comunes, además de un foro casi con el mismo movimiento que este maravilloso foro de Ubuntu.
- Que sea rolling release no significa que sea obligatorio actualizar todos los paquetes, ni todo el tiempo, tal como tampoco es necesario en Ubuntu actualizar de versión.  Es optativo.  Free as in freedom =D

Esto creo que es *relativamente* cierto. La cuestión es la experiencia "out of the box". Muchísimas distros se pueden modificar para el fin que uno quiera instalando los paquetes adecuados y configurando como se quiera, pero no se puede pasar por alto el tiempo que se necesita para modificar a gusto, como eligiendo paquetes estables y seguros, eliminando bugs, o manteniendo versiones de paquetes que funcionen bien entre sí.

La libertad está con la mayoría de las distros, pero si no se elige bien es la libertad de aburrirse en el intento :).

---

### Post by oktubrer on 2010-07-06
> **alfplayer said:**
> Esto creo que es *relativamente* cierto. La cuestión es la experiencia "out of the box". Muchísimas distros se pueden modificar para el fin que uno quiera instalando los paquetes adecuados y configurando como se quiera, pero no se puede pasar por alto el tiempo que se necesita para modificar a gusto, como eligiendo paquetes estables y seguros, eliminando bugs, o manteniendo versiones de paquetes que funcionen bien entre sí.

La libertad está con la mayoría de las distros, pero si no se elige bien es la libertad de aburrirse en el intento :).

Ok, no mantuve mi promesa de no responder, solo para refutar un concepto que veo repetido y es erróneo.  Los repositorios por defecto de ARCH poseen paquetes tan estables y seguros como los normales de Ubuntu.  No hace falta "elegir paquetes estables y seguros".  Alguna actualización cada tanto genera algun error, tan seguido como me pasa en Ubuntu.

Lo que SI es cierto, es que out of the box ni siquiera tenés instalado el entorno gráfico.  Y lógicamente tenés que tener ganas de ponerte a instalar todo lo necesario.  
Es, si se quiere, un habitante de una punta del espectro de distribuciones, con Ubuntu en el otro extremo donde recién instalado ya funciona "casi" todo el hardware de forma impecable, la mayoría de las veces.  Ambos extremos tienen pros y contras.  Probarlos es la forma de saber cual te gusta más.

---

### Post by alfplayer on 2010-07-06
> **oktubrer said:**
> Ok, no mantuve mi promesa de no responder, solo para refutar un concepto que veo repetido y es erróneo.  Los repositorios por defecto de ARCH poseen paquetes tan estables y seguros como los normales de Ubuntu.  No hace falta "elegir paquetes estables y seguros".  Alguna actualización cada tanto genera algun error, tan seguido como me pasa en Ubuntu.

Para la mayoría de los paquetes, Ubuntu fija la versión de Debian, y después si es necesario los actualiza intentando aumentar la seguridad y la estabilidad. Al contrario, con un rolling release, las nuevas versiones de los desarrolladores pueden tener por ejemplo nuevas funciones o parte de su código reescrito, que es generalmente contrario a la seguridad y estabilidad.

> **oktubrer said:**
> Lo que SI es cierto, es que out of the box ni siquiera tenés instalado el entorno gráfico.  Y lógicamente tenés que tener ganas de ponerte a instalar todo lo necesario.  
Es, si se quiere, un habitante de una punta del espectro de distribuciones, con Ubuntu en el otro extremo donde recién instalado ya funciona "casi" todo el hardware de forma impecable, la mayoría de las veces.  Ambos extremos tienen pros y contras.  Probarlos es la forma de saber cual te gusta más.

Hay muchas características de las distribuciones que se pueden analizar. Probar no siempre es la forma. Escuchar o leer las opiniones de otros con más experiencia puede ser más informativo.

---

### Post by guillermolisi on 2010-07-06
> **EnriqueK said:**
> A los moderadores de foro del pido que vayam preparando tutos que explique como eliminar o desactivar el módulo Nouveau en la futura versión de Uvubtu 10.10 , vaticino que las quejas serán muchísimas.
Enrique

Me parece que estas confundiendo roles. Los foros los hacen quienes participan de ellos intercambiando ideas, experiencias, opiniones, ayuda y conocimiento.
Los moderadores, tal como su nombre significa, moderan cuando hace falta, sin perjuicio de que tambien participen como miembros comunes (que son) en el foro. Con lo cual, cualquiera que se sienta con ganas puede preparar lo que crea sea de utilidad para los demas, mas alla de Noveau inclusive.

---

### Post by biale on 2010-07-06
> La cuestión es la experiencia "out of the box"
Muy de acuerdo! Pero desgraciadamente hay un punto: es posible, y por motivos que desconozco que a esa experiencia out of the box se la este "desluciendo".

Flota en el ambiente una busqueda. Tradicionalmente Unix -> Linux eran sinónimos de estabilidad y predecibilidad. Hoy día ya no tanto.

Hay un bricolage necesario para pasar desde version a version, para recién luego instalar los productos que uno necesita.

Personalmente, desearía una diferencia todavia mas nítida entre la experiencia out of the box y el hobby de la experimentación.

---

### Post by EnriqueK on 2010-07-07
A partir del kernel 2.6.32 (lucid), está disponible una nueva herramienta para  recompilar el kernel "make localmodconfig", se encarga de hacer un rastreo de los módulos que tengan registro de haber sido usados y solo ellos serán tomados en cuenta en la recopilación que puede hacercela  "a lo Debian", yo lo hice quedando el linux-image con un tamaño del orden de 7,5 megas, o sea mucho mas reducido que el que viene de fábrica, todo esto de una forma simple, apto para novatos y que puede ser aprovechada muy bien en distros como Ubuntu para lograr optimizarlas  sin tener que recurrir a distros complejas tipo Gentoo . Arch, etc.
También usé este target para Make en la recompilación de un kernel de Debian que me permitió además eliminar nouveau que también está causando muchísimas quejas entre los usuarios de Debian Testing.

---

### Post by juancarlospaco on 2010-07-07
*Que flamewar ni flame war...?*, **la verdad no ofende**, 
Arch no tiene ni Boletin de Seguridad Oficial.
*[SIZE="1"]Invito a todo el que quiera que haga click en ["Subscribe to the RSS feed"]("http://www.ubuntu.com/usn")[/SIZE]*

[I]Lo que dicen arriba es cierto tambien, podes compilar y optimizar en Ubuntu,
tambien en otras distros, igual que tambien es posible usar los Repos de Arch.[/I]

:)

---

### Post by guillermolisi on 2010-07-07
> **biale said:**
> Muy de acuerdo! Pero desgraciadamente hay un punto: es posible, y por motivos que desconozco que a esa experiencia out of the box se la este "desluciendo".

Flota en el ambiente una busqueda. Tradicionalmente Unix -> Linux eran sinónimos de estabilidad y predecibilidad. Hoy día ya no tanto.

Hay un bricolage necesario para pasar desde version a version, para recién luego instalar los productos que uno necesita.

Personalmente, desearía una diferencia todavia mas nítida entre la experiencia out of the box y el hobby de la experimentación.
Es que cada uno tiene un umbral distinto, un paradigma diferente que hace que esa experiencia OOTB cambie de persona en persona sencillamente porque hay objetivos diferentes.

A algunos no le molesta (a veces hasta les gusta) tener que lidiar con algun que otro problema ya que lo toman como un desafio. A otros les gusta que la cosa se instantanea, sin mayor tramite ya que sus objetivos estan en otra parte, no en la investigacion ni en la resolucion de problemas vinculados con la base operativa.
Por eso es que ese limite es tan borroso, tan "deslucido" para algunos y tan claro para otros ("si tengo que compilar, entonces busco algo mas express que no lo requiera").

Y en este amplio y diversificado universo de distribuciones hay para para elegir y aqui en donde cada uno debe hacer su propia experiencia hasta encontrar cual es el equilibrio que acepta como razonable.

Unix/Linux son tan estables/inestables como antes solo que ahora se conocen (rapidamente) los puntos debiles que antes estaban reservados solo para una elite (los sysadmin ?) y esto permite un intercambio de opiniones "popular" mas fluido.

El gran secreto en todo esto no es lo que conocemos de cada distribucion sino lo que no conocemos y esta ahi sin que lo veamos.

---

### Post by oktubrer on 2010-07-07
> **guillermolisi said:**
> Es que cada uno tiene un umbral distinto, un paradigma diferente que hace que esa experiencia OOTB cambie de persona en persona sencillamente porque hay objetivos diferentes.

A algunos no le molesta (a veces hasta les gusta) tener que lidiar con algun que otro problema ya que lo toman como un desafio. A otros les gusta que la cosa se instantanea, sin mayor tramite ya que sus objetivos estan en otra parte, no en la investigacion ni en la resolucion de problemas vinculados con la base operativa.
Por eso es que ese limite es tan borroso, tan "deslucido" para algunos y tan claro para otros ("si tengo que compilar, entonces busco algo mas express que no lo requiera").

Y en este amplio y diversificado universo de distribuciones hay para para elegir y aqui en donde cada uno debe hacer su propia experiencia hasta encontrar cual es el equilibrio que acepta como razonable.

Unix/Linux son tan estables/inestables como antes solo que ahora se conocen (rapidamente) los puntos debiles que antes estaban reservados solo para una elite (los sysadmin ?) y esto permite un intercambio de opiniones "popular" mas fluido.

El gran secreto en todo esto no es lo que conocemos de cada distribucion sino lo que no conocemos y esta ahi sin que lo veamos.

Sabias palabras, me saco el sombrero.

---

### Post by oktubrer on 2010-07-07
> **juancarlospaco said:**
> *Que flamewar ni flame war...?*, **la verdad no ofende**, 
Arch no tiene ni Boletin de Seguridad Oficial.
*[SIZE="1"]Invito a todo el que quiera que haga click en ["Subscribe to the RSS feed"]("http://www.ubuntu.com/usn")[/SIZE]*

[I]Lo que dicen arriba es cierto tambien, podes compilar y optimizar en Ubuntu,
tambien en otras distros, igual que tambien es posible usar los Repos de Arch.[/I]

:)
¿Sabés quien tiene Boletín Oficial de Seguridad también? Microsoft! :P

---

