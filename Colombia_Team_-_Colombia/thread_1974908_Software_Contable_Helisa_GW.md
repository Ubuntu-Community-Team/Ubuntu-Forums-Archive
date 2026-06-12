---
title: "Software Contable Helisa GW"
date: 2012-05-06
forum: Colombia Team - Colombia
---

### Post by isayuron on 2012-05-06
Buenas tardes miembros de Ubuntu Colombia, quisiera saber si alguno podría ayudarme para instalar Helisa GW en una máquina con Ubuntu, ya que solo existe versión para Windows. He instalado el Wine y también las aplicaciones que vienen para el funcionamiento de la aplicación que son: Firebird 1.5.2, BDE y el Software Contable HelisaGW, que por cierto, recien los instalo, funciona. Es decir corro la aplicación y puedo ingresar con el usuario y me muestra los diferentes elementos del programa. Sin embargo al apagar (o reiniciar) ya no funciona. El error que aparentemente se presenta es que no hay comunicación con el manejador de BD que esta ubicado en el localhost.

Ya he intentado con varias versiones de Ubuntu: 10.04, 11.10 y la 12.04 pero todavía nada, así que si me pueden ayudar, muchas gracias

---

### Post by rodsarm on 2012-05-08
> **isayuron said:**
> Buenas tardes miembros de Ubuntu Colombia, quisiera saber si alguno podría ayudarme para instalar Helisa GW en una máquina con Ubuntu, ya que solo existe versión para Windows. He instalado el Wine y también las aplicaciones que vienen para el funcionamiento de la aplicación que son: Firebird 1.5.2, BDE y el Software Contable HelisaGW, que por cierto, recien los instalo, funciona. Es decir corro la aplicación y puedo ingresar con el usuario y me muestra los diferentes elementos del programa. Sin embargo al apagar (o reiniciar) ya no funciona. El error que aparentemente se presenta es que no hay comunicación con el manejador de BD que esta ubicado en el localhost.

Ya he intentado con varias versiones de Ubuntu: 10.04, 11.10 y la 12.04 pero todavía nada, así que si me pueden ayudar, muchas gracias


Lo mejor es que instale el virtualBox en Ubuntu (la 12.04 va mejor) y allí cree una maquina virtual; Windows (XP es la mas liviana y robusta)  instala Helisa con todos sus componentes en dicha maquina y ya. Es sencillo, fácil... haga siempre backup de los datos!!!

---

### Post by rodsarm on 2012-05-08
> **rodsarm said:**
> Lo mejor es que instale el virtualBox en Ubuntu (la 12.04 va mejor) y allí cree una maquina virtual; Windows (XP es la mas liviana y robusta)  instala Helisa con todos sus componentes en dicha maquina y ya. Es sencillo, fácil... haga siempre backup de los datos!!!

Por cierto en esta pagina descarga el VirtualBox
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by isayuron on 2012-05-09
La idea era no tener que recurrir nuevamente a Microsoft, se que funciona porque así lo hice en una máquina personal, pero la idea es que algunos de mis equipo que tienen 512MB de ram y Procesadores de 1.5 o 1.8 puedan correrlo sin necesidad de sobrecargarlo con 2 sistemas operativos

---

### Post by isayuron on 2012-05-09
> **isayuron said:**
> La idea era no tener que recurrir nuevamente a Microsoft, se que funciona porque así lo hice en una máquina personal, pero la idea es que algunos de mis equipo que tienen 512MB de ram y Procesadores de 1.5 o 1.8 puedan correrlo sin necesidad de sobrecargarlo con 2 sistemas operativos

Aclaro que he realizado la instalción de virtual box en linux y la instalación de xp en la máquina virtual y en esta el helisa y claro, funciona. Pero mi intención es hacerlo funcionar en Linux usando solamente wine.

En caso forzoso, ¿se puede instalar una impresora en red desde Virtual Box? La impresora está en un equipo con XP. 

Perdón si me desvío del tema.

---

### Post by darkhole on 2012-05-13
Hola!

Si es posible instalar la impresora en red... Ahora, lo de instalar con Wine, ya lo haz intentado??? Que errores aparecen?

---

### Post by isayuron on 2012-05-14
> **darkhole said:**
> Hola!

Si es posible instalar la impresora en red... Ahora, lo de instalar con Wine, ya lo haz intentado??? Que errores aparecen?

Al instalar todos los componentes, la primera vez funciona. Helisa abre, puedo ver los diferentes módulos. Pero al reiniciar la máquina ya no arranca pues aparece un problema de conexion. Lo que he podido comprobar es que el firebird server debe estarse ejecutando para que el Helisa pueda arrancar de lo contrario se presenta esa falla. En windows, si lo cierro o finalizo (el firebird server), puedo inicializarlo manualmente desde una archivo en el system 32 llamado firebird2control.cpl (tengo dudas de la extensión ahora), pero el caso es que en linux usando el wine, no hay forma de abrir un archivo con dicha extensión, por lo que no tengo idea de como hacerlo arrancar nuevamente y que lo haga automaticamente. Con el Ubuntu 10.04 es más estable que con el 11.10 y el 12.04

---

### Post by edgamen on 2012-05-24
Hola, mi recomendacion seria que instalara esas aplicaciones, no directamente sobre Wine, sino usando PlayOnLinux, a mi me ha servido para ejecutar aplicaciones para Windows que no me corrian en Wine directamente o que tenia que personalizar o "tunear" , como dicen algunos, en la configuración de Wine. Espero que sea de ayuda.  Nos cuenta como le termina de ir, por favor. Yo también estoy interesado en el uso de Helisa sobre GNU/Linux.Suerte.

---

