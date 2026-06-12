---
title: "Ubuntu en HP 2135 LA"
date: 2007-09-12
forum: Ecuador Team
---

### Post by emendieta on 2007-09-12
Saludos

Tengo una HP 2135 LA instale primero la version 6.06 y tenía ya algunos problemas con la laptop, luego al salir 7.04 hice el update y algunas cosas se resolvieron, pero todavia tengo algunos pendientes como:

1. La bateria de la laptop no me dura casi nada al desconectarla, máximo 1 hora
2. La compu se calienta mucho parece que es un problema de los sensores, que no funciona bien y hace que se caliente y por obvias razones la bateria se acaba, incluso a ratos esta tan caliente la laptop que la apago para que se enfrie
3. No me funciona la salida de video el momento de conectarme con algun infocus o proyector

Alguien puede darme una solucion???

Pensaba en volver a formatearla e instalar desde cero el 7.04, o alguien sabe donde puedo conseguir informacion para resolver estos problemas

gracias

---

### Post by hubuntu on 2007-09-13
Hola!

He estado leyendo en foros y buscando info acerca del tema.

Lo que es seguro es que para una gran parte de las nuevas PCs de HP el kernel de Gutsy 7.10 (2.6.21 o estable 2.6.22) viene con cambios que hacen posible la activación de los modulos para control automático de temperatura.

No recomedaría cambiar a Gutsy todavía en una maquina que se a de uso primario. Esperen al menos a que salga el beta mo mejor la versión oficial... Falta poco más de un mes.

>1. La bateria de la laptop no me dura casi nada al desconectarla, máximo 1 hora

No se si este problema es de la maquina o de ubuntu. Puedes apagar el modulo de Bluetooth si no lo usas comunmente (toma mucha energía) y el wireless.Una buena idea es bajar la intensidad de la pantalla tan bajo como sea posible. Esto ayuda a mejorar la bateria hasta en un 30%!!

Puede ser simplemente que la bateria sea mala (pero una hora como que es muy poco, no?)

>2. La compu se calienta mucho parece que es un problema de los sensores, que no funciona bien y hace que se caliente y por obvias razones la bateria se acaba, incluso a ratos esta tan caliente la laptop que la apago para que se enfrie

Hace unos meses en planet.ubuntulinux.org ví un comando que ayuda para la activación de el manejo de energía en ciertas compus. Desgraciadamente no lo he vuelto a encontrar, pero he descubierto que power-manager-gnome se encarga de esto mediante el sistema de comunicación D-BUS de HAL (Capa de abstracción de software).
El kernel 2.6.22 resolverá esto en Gutsy. Recomendaría no instalarlo en Feisty (inestable) y esperar hasta mediados de octubre.

3. No me funciona la salida de video el momento de conectarme con algun infocus o proyector

Yo he tenido este problema, pero tiene solución :)
Apaga la compu y conecta tu monitor/proyector externo. 

Reinicia y aplasta escape para ir al menu de grub. Ahora antes de escoger el kernel para iniciar aplasta FN+Cambio de monitor (osea la combinación esa... en mi caso es Fn+F8).

Ahi veras de una que el monitor/proyector ya esta listo transmitiendo la imagen de grub. Si no ves esto pero tampoco la imagen de tu monitor, pues aplasta enter y prueba :)

Mi problema generalmente es la resolución. Para no hacerme lio la cambio a 800x600 y punto. F11 en Evince o Shift+Alt+S en OOO y ya tienes pantalla completa.

Si no se soluciona haz como yo: En casa mi config es de 1360x768. Y para eso hay que usar nano o geidt y xorg.conf y editar ahi la resolución... mejor es esperar a que salga Gutsy que ese problema tb ya lo están resolviendo :)

Espero con esto haber ayudado un poco en tu inquietud.

R

---

### Post by hubuntu on 2007-10-18
Hola Esteban!

Gutsy Gibbon ha sido lanzado hoy. Actualizalo a la últim versión y cuentanos si tu  hardware tiene ya mejor soporte.

Suerte!
R.

---

### Post by compuniversal on 2007-10-23
Hola emendieta
Mira no estoy seguro de que se ubuntu, porque si es problema mas de hardward como le veo, segun lo que describes a lo mejor puede ser tu bateria que ya esta usada, la mayoria de las laptops duran las baterias regularmente de 1hora a 2 horas dependiendo lo que hagas en tu compu.
Con el calentamiento tambien puede ser varias razones, te digo esto por que razon, donde estoy ahorita viviendo (San Jose California USA) en los veranos a mi laptop le tengo que poner un ventilador cuando la uso por que se calienta mucho, aun que la huce 10 o 1 hora, pero en invierons pasa bien, ten en cuenta que no la tengo en parte de solo ni fria, esta dentro de mi cuarto donde el medio ambiente es templado.

Ahora lo que has hecho una actualizacion de ubuntu 6 a 7 no se si actualizaste tu maquina oh hiciste una instalacion desde cero, yo tengo ahora una Laptop Acer TravelMate 4230-6704 con ubuntu gutsy y me funciona casi todo bien, lo unico que tengo problemas es con el card reader que viene incorporado pero aun no el eh puesto empenio en hacer algo por que casi no lo uso.

Espero te sirva.

Salu2 :)

---

### Post by hubuntu on 2007-11-30
Hola esteban!

Conozco a un usuario de una máquina HP que se recalienta y muere y que ha encontrado una solución:

Bajalé la velocidad del procesador en BIOS!

Aunque no es la mejor forma de hacer las cosas, él me explico que el problema gradualmente apareció y no hay diferencia entre linux y windows en ese aspecto, pro ende el decidió resolverlo de una manera drástica y al fin ha logrado poder usar su laptop racionalemnte.

La batería puede ser muy variable y he usado máquinas que tienen una hora y 15 minutos como estándard y otra que tienen 9 horas (con batería doble) de uso CON ubuntu.

Suerte!

---

### Post by estebandid0 on 2008-03-25
Bueno

Luego de tanto tiempo con este problema del recalentamiento de la maquina le envie a servicio técnico, pensé que era un problema de Ubuntu.

Pero en el servicio técnico me indicaron que estas maquinas tienen un problema y que se recalientan mucho, ya que tienen como un disipador de calor entre el disco duro y la placa (parece un papel de aluminio), pero que la verdad no ayuda en nada y que por eso optan en quitarlo.

Luego de la revisión me indicaron que como tenia este disipador que no ayudaba para nada, se quemo el ventilador, lo cual lo cambiaron, incluso uno de los usb tambien estaba defectuoso debido al calor.

Así que cambiaron el ventilador, el usb, y quitaron ese papel de alumunio y listo, asunto solucionado, instale nuevamente desde cero ubuntu 7.10 y quedo super bien, sin ningún problema la máquina.

---

