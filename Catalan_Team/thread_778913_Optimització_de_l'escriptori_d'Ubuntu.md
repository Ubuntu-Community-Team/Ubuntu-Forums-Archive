---
title: "Optimització de l'escriptori d'Ubuntu"
date: 2008-05-02
forum: Catalan Team
---

### Post by Satboy on 2008-05-02
Hola,
 Googlejant he trobat aquesta guia per optimitzar l'escriptori d'Ubuntu.Què en penseu? És fiable?

 A10!;-)

 **OPTIMIZAR EL ESCRITORIO**
Autor: Michael Garcia

CÓMO optimizar Ubuntu GNU/Linux para sistemas de escritorio v. 0.3

1. Introducción

La configuración que trae por defecto Ubuntu GNU/Linux es perfectamente estable y segura. Sin embargo, es posible realizar pequeños ajustes que optimicen el uso de los recursos para tener un sistema de escritorio más ágil.

No voy a entrar en valoraciones sobre si tal o cuál valor en este o aquel parámetro es mejor o peor. Sólo mencionaré que después de aplicar todo lo escrito aquí se obtiene una mejora en el rendimiento y la respuesta del sistema (no la he medido con ningún programa, se nota a simple vista). Supongo que la mejora dependerá cada sistema. Además, no entraré en cambios complejos (compilaciones de núcleo o bibliotecas) ni peligrosos para el hardware (véase hdparm), por considerar que la relación riesgo/beneficio no es buena.

Los cambios que voy a proponer son aplicables con pequeños cambios a cualquier distribución GNU/Linux que queramos usar en nuestro escritorio. Las órdenes necesarias está entre comillas, hay que teclear sólo el texto que está dentro. Por ejemplo, en “sudo nano /boot/grub/menu.lst”, teclearíamos en el ordenador: sudo nano /boot/grub/menu.lst. El editor para realizar los cambios que se usa en los ejemplos es siempre nano. Evidentemente, puede usarse desde vim hasta gedit, pasando por emacs algooooo

2. Cambios generales

2.1 Swappiness

Por defecto, en la rama 2.6, el núcleo de linux tiene este valor a un 60% (en la rama 2.4 no existe). Esto quiere decir que se hará bastante uso de la memoria de intercambio (swap). Resulta útil si tenemos un servidor con gran carga de trabajo y poca RAM, o si compilamos frecuentemente aplicaciones muuuuy grandes. Sin embargo, en un sistema de escritorio, con varias aplicaciones pequeñas ejecutándose, podemos bajar este valor a 10 para que el núcleo use más a menudo la memoria RAM (más rápida) y recurra menos a la memoria de intercambio. Para ello, abrimos una terminal y hacemos lo siguiente:

- Consultamos el valor inicial: “sudo cat /proc/sys/vm/swappiness”. Después de introducir la contraseña, nos muestra un valor de 60 (si ya nos muestra 10, no hay nada que hacer. Pasa al siguiente apartado algooooo

- Probamos cómo responde el sistema al bajar el valor: “sudo sysctl -w vm.swappiness=10&#8243;. Ejecutamos después un par de aplicaciones.

- Si el resultado es satisfactorio, vamos a modificar un archivo de configuración para que el cambio sea permanente: “sudo nano /etc/sysctl.conf”. En la última línea añadimos: “vm.swappiness=10&#8243;.

- Guardamos los cambios pulsando las teclas CONTROL+o y salimos pulsando CONTROL+x.

2.2 Consolas virtuales

Al acceder a nuestro sistema, aparte de la pantalla de login gráfica, hay 6 consolas en modo texto (a las que se puede acceder pulsando CONTROL+ALT+(desde la tecla F1 hasta la tecla F6, la tecla F7 vuelve a acceder al sistema gráfico) ejecutándose en segundo plano. En mi caso, por ejemplo, cada una ocupa 1,5 megas de RAM. Para ahorrar memoria, pueden no activarse las 6, sino dejar sólo 1 ó 2, por si el sistema gráfico tiene algún problema.

- Abrimos una terminal y tecleamos lo siguiente: “sudo nano /etc/inittab”. Dentro de este archivo, vamos hasta unas líneas en las que se lee:

1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

- Comentamos las consolas que no queremos que se inicien. Esto se hace poniendo una almohadilla (#) delante de la línea correspondiente. Para desactivar todas las consolas de texto menos la primera debe quedar así:

1:2345:respawn:/sbin/getty 38400 tty1
#2:23:respawn:/sbin/getty 38400 tty2
#3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

- Guardamos los cambios pulsando las teclas CONTROL+o y salimos pulsando CONTROL+x.

2.3 Xorg

Podemos bajar la profundidad de color a 24-bit a 16-bit notando poca diferencia. Esto reduce uso de la memoria de la tarjeta gráfica.

- Abrimos una terminal y tecleamos: “cd /etc/X11&#8243;.

- Ahora vamos a modificar el archivo de configuración xorg.conf: “sudo nano xorg.conf”.

- Buscamos la línea que pone DefaultDepth y modificamos su valor de 24 a 16.

- Guardamos los cambios pulsando las teclas CONTROL+o y salimos pulsando CONTROL+x.

2.4 Cambiar el núcleo

Por defecto, Ubuntu GNU/Linux viene con un núcleo estándar compilado para i386 de modo que funcione desde en el viejo Pentium 100 del trastero hasta en el potente Pentium 2,2 del salón. Sin embargo, si escogemos un núcleo precompilado de Ubuntu que se ajuste a nuestro procesador, notaremos una mejora. Pasos a seguir:

- Vamos al menú Sistema de GNOME, abrimos Administración e iniciamos el Gestor de Paquetes Synaptic.

- Una vez dentro de Synaptic, si disponemos de conexión a Internet, pulsamos en Recargar para obtener los últimos paquetes.

- Tras actualizar, escogemos la sección Sistema Base. OJO!!: para evitar problemas con núcleos no oficiales, marcamos Sistema base, no Sistema base(universe)

- Bajamos hasta la zona dónde tenemos paquetes que se llaman: linux-image-X.X.X-nombre_de_nuestro_procesador y marcamos la versión más actual. Por ejemplo, en este momento, para mi ordenador sería: linux-image-2.6.10-5-k7.

- Si tenemos algún hardware que requiera módulos del núcleo especiales (véase tarjetas Nvidia), debemos marcar también los linux-restricted-modules correspondientes al núcleo seleccionado.

- Aplicamos los cambios. Al reiniciar la próxima vez, se cargará el núcleo seleccionado.

2.5 Parar servicios no necesarios

Para cubrir el mayor número de situaciones posibles, Ubuntu GNU/Linux inicia toda una serie de servicios que, a veces, no son necesarios. Si deshabilitamos los que no necesitamos, no estarán durmiendo y consumiendo memoria. Existen otros programas y formas de evitar iniciar servicios, por ejemplo update-rc.d o el programa boot-Up Manager ([http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)), pero esta forma es simple y efectiva (es la recomendada también por [http://www.ubuntuguide.org](http://www.ubuntuguide.org)).

- Abrimos una terminal y vamos al directorio /etc/init.d: “cd etc/init.d/”.

- Vemos qué servicios puede ejecutar el ordenador: “ls” (son los que aparecen en verde).

- Denegamos el permiso de ejecución para el que no queramos arrancar: “sudo chmod -x nombre_del_servicio”. Por ejemplo, si no usamos fetchmail, teclearemos “sudo chmod -x fetchmail”

- Si nos equivocamos, siempre podemos volver a habilitar el servicio haciendo: “sudo chmod +x nombre_del_servicio”.

- Sugerencias de servicios que normalmente no se usan en un ordenador de escritorio:

- ntpdate: actualiza el reloj del sistema sincronizándolo cada vez que se reinicia.
- pcmcia: sólo se usa con portátiles que tengan tarjetas PCMCIA.
- ppp: protocolo punto a punto. Sólo se utiliza si usas un módem para conectarte a Internet
- powernowd: en teoría lo usan los procesadores AMD para gestionar el uso de la energía, personalmente nunca lo he usado.
- rsync: utilidad para transferir archivos para hacer copias o mantener un espejo sincronizado.
- fetchmail: recoge y reenvía correo y actúa como pasarela hacia el servicio smtp.
- postfix: agente de transferencia de correo, parecido a sendmail. Personalmente, con Yahoo y Evolution me llega.

En este punto, al ser cada caso distinto, sólo puedo recomendar que antes de evitar que arranque un servicio se sepa para que sirve: “man nombre_del_servicio” o bien busquemos en Google más información sobre el mismo.
Hay que tener cuidado si se desactiva algún servicio que usen otras aplicaciones. Por ejemplo: Gnome usa cupsys, demonio de impresión. Si se hace desde Gnome una llamada al mismo y no está ejecutándose, el sistema se vuelve inestable. Para evitar esto, hay que modificar, desde el menú Sistema, Preferencias, Sesiones, los demonios del escritorio que se inician en el arranque (en este caso se quitaría del arranque el proceso de Gnome relacionado con cupsys).

2.6 Inicio de procesos en paralelo

No entro en tecnicismos sobre el arranque, resumo la idea. Init.d invoca los procesos de uno en uno en el arranque. Si los invocamos en paralelo, ahorramos tiempo en el inicio del sistema. Puede ser que se produzca algún error de dependencias porque ciertos procesos “suponen” que hay otros ejecutándose cuándo se inician. Aún así, en un sistema de escritorio no debe haber problemas. Pasos que se deben seguir:

- Abrimos una terminal y tecleamos: “cd /etc/init.d”.

- Ahora vamos a modificar el archivo de configuración rc: “sudo nano rc”.

- Buscamos la línea que pone “startup $i start” y añadimos un &, de modo que quede cómo sigue: “startup $i start &”.

- Guardamos los cambios pulsando las teclas CONTROL+o y salimos pulsando CONTROL+x.

La próxima vez que iniciemos la máquina, veremos cómo todos los procesos salen “disparados” de una sola vez en la traza del inicio.

2.7 Gnome

Para iniciar más rápido Gnome, podemos desactivar la pantalla de bienvenida desde el menú Sistema, Preferencias, Sesiones, en la pestaña Opciones de la sesión desmarcando la opción: Mostrar la pantalla de bienvenida al iniciar sesión.

Si somos la única persona que accede al ordenador o si todos acceden con el mismo usuario, podemos iniciar la sesión sin hacer login ni cargar GDM de este modo:

- Vamos al menú Sistema y, dentro de Administración, escogemos: Configuración de la pantalla de inicio de sesión. Vamos a la pestaña General y marcamos la opción Acceder automáticamente con un usuario al arrancar por primera vez. Debajo escribimos nuestro nombre de usuario. OJO!!: a partir de la activación de este cambio NO se pedirá contraseña al entrar en el sistema.

Los escritorios virtuales son, para mí, un atractivo más para usar Linux, pero puede ser que 4 consuman demasiados recursos. Para cambiar el número de escritorios virtuales hacemos click con el botón derecho del ratón en el panel inferior, justo en el paginador de escritorios (a la izquierda de la papelera). En el menú que aparece seleccionamos Preferencias y escogemos en Cantidad de espacios de trabajo el número que queramos.

2.8 Prelink

Existe una utilidad que se encuentra en los repositorios Universe que se llama “Prelink”. Según su página del manual su función es: “pre-enlazar binarios y bibliotecas ELF compartidas para acelerar su tiempo de inicio”. Hay que tener en cuenta que para disponer del progrma prelink, debemos tener los repositorios Universe activos, el modo de hacerlo se explica aquí: [http://www.guia-ubuntu.org/hoary/doku.php](http://www.guia-ubuntu.org/hoary/doku.php)). Para ponerlo en funcionamiento haremos lo siguiente:

- Vamos al menú Sistema de GNOME, abrimos Administración e iniciamos el Gestor de Paquetes Synaptic.

- Una vez dentro de Synaptic, si disponemos de conexión a Internet, pulsamos en Recargar para obtener los últimos paquetes.

- Tras actualizar, le damos al botón Buscar y tecleamos prelink. Una vez que aparece el programa lo marcamos y lo instalamos.

- Ahora modificamos las opciones de prelink: “sudo nano /etc/default/prelink”. En la línea que pone: PRELINKING=unknown, lo modificamos y ponemos: PRELINKING=yes. El resto de opciones por defecto funcionan bien.

- Para iniciar prelink por primera vez (la primera vez puede llevar algo de tiempo). Tecleamos: “sudo /etc/cron.daily/prelink”.

- Si no queremos enlazar todo el sistema, sino sólo Openoffice.org (aplicación bastante pesada) nos saltaríamos el paso anteiror y haríamos: “sudo /usr/sbin/oooprelink -f”

- Debemos tener en cuenta que al actualizar bibliotecas, debemos ejecutar de nuevo “sudo /etc/cron.daily/prelink”, para evitar inestabilidades en el sistema.

- Si no nos gusta el rendimiento de prelink, podemos hacer “sudo nano /etc/default/prelink”. En la línea que pone: PRELINKING=yes, lo modificamos y ponemos: PRELINKING=no. Ejecutamos de nuevo “sudo /etc/cron.daily/prelink”.

3. Optimizar las aplicaciones

Si en el menú Aplicaciones de Gnome vamos a la opción Herramientas del sistema e iniciamos Monitor del sistema, veremos una lista de procesos y aplicaciones junto con la memoria que consume cada uno. Ahora intentaremos “aligerar” los más pesados.

3.1 Nautilus

Aunque me encanta el modo espacial nativo de Gnome, hay que reconocer que el navegador de archivos viene con unas cuántas opciones que hacen que sea bastante lento. Podemos desactivar algunas para hacerlo más ágil.

- Abrimos Nautilus. Por ejemplo, entrando en el menú Lugares de Gnome y abriendo Carpeta personal. Entramos en el menú Editar y después en preferencias. Vamos a la pestaña Vista previa y las desactivamos todas, marcando en todos los apartados la opción Nunca.

3.2 Firefox

Se pueden hacer cambios en Firefox para aumentar el número de conexiones y para que aproveche otros parámetros.

- Abrimos Firefox pulsando en su icono. En una ventana escribimos la dirección: “about:config” y pulsamos enter.

- Cambiamos estos valores. Para ello, hacemos doble click encima de la línea que queremos modificar y en el cuadro de diálogo que aparece, escribimos el valor nuevo:

network.dns.disableIPv6 &#8594; Cambiamos el valor a true (basta con un doble click)
network.http.max-connections &#8594; Cambiamos el valor a 128
network.http.max-connections-per-server &#8594; Cambiamos el valor a 48
network.http.max-persistent-connections-per-proxy &#8594; Cambiamos el valor a 24
network.http.max-persistent-connections-per-server &#8594; Cambiamos el valor a 12

- Si se dispone de conexión de banda ancha, también se puede modificar los siguientes valores:

network.http.pipelining &#8594; Cambiamos el valor a true (basta con un doble click)
network.http.proxy.pipelining &#8594; Cambiamos el valor a true (basta con un doble click)
network.http.pipelining.maxrequests &#8594; Cambiamos el valor a 30

3.3 Openoffice.org

Una de las aplicaciones más pesadas es Openoffice.org. Utilizando la caché intentamos que se ejecute más rápido.

- Abrimos Openoffice.org. Por ejemplo: menú Aplicaciones, Oficina, Openoffice.org Word Processor.

. Entramos en el menu Herramientas, apartado Opciones y marcamos memoria de trabajo. A la derecha en Antememoria de la imagen, cambiamos los valores de Uso de Openoffice.org de 6 a 128 y de Memoria por objeto de 0,5 a 20. Aceptamos los cambios. Al ejecutar Openoffice.org repetidas veces, notaremos la diferencia.

4. Conclusión
Estos cambios pueden ayudar a obtener un sistema Ubuntu más rápido y que responda mejor. Espero que os sea de utilidad y que esté bien explicado para que todo el mundo pueda aplicar las sugerencias.

---

### Post by pespin on 2008-05-02
Aquesta guia ja fa bastant temps que corre. Suposo que amb el temps molts dels valors que surten hauran anat canviant. És qüestió d'anar mirant i aplicar el que creguis que et pot ser útil.:)

---

### Post by papapep on 2008-05-02
Satboy, no és bona pràctica enganxar tot aquest totxo quan pots posar només el tros que t'interessa o, encara millor, posar l'enllaç a la informació.

---

### Post by Satboy on 2008-05-02
> **papapep said:**
> Satboy, no és bona pràctica enganxar tot aquest totxo quan pots posar només el tros que t'interessa o, encara millor, posar l'enllaç a la informació.
 Hola,
 Jo només ho he penjat per si a algú li interessava, no em pensava que estès fent res malament.
 Siau!

---

### Post by papapep on 2008-05-02
El fet de que no pensessis que feies res malament no implica que estigui ben fet. I per si a algú li fa falta amb l'enllaç va sobrat.

---

### Post by CarlesOriol on 2008-05-02
Nens... la mitat d'optimitzacions que surten en aquesta guia et poden deixar el hardy bastant fregit.
El prelink esta caduc, els processos en paralel et poden produir un caos més que considerable si fas el que et diu i els estalvis dels punts 2.1 i 2.2 son bastant dubtosos.

---

