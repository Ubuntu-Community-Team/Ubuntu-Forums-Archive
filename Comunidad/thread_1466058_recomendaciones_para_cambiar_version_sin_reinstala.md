---
title: "recomendaciones para cambiar version sin reinstalar?"
date: 2010-04-30
forum: Comunidad
---

### Post by infernus92 on 2010-04-30
hola...
recien estaba viendo la pagina de xubuntu y encontre un pequeño articulo que dice algunas recomendaciones para cambiar a lucid sin reinstalar... y revise las paginas de ubuntu y kubuntu y no encontre nada actual al respecto...
se me ocurrio de una preguntar aca algunas recomendaciones para cambiar de version con el gestor de actualizaciones... que nos sirva a los que nunca cambiamos de version sin reinstalar, y de paso a los que cambian de version por primera vez...
gracias a los que respondan!!!

Saludos

---

### Post by guillermolisi on 2010-04-30
Una que no es menor es utilizar mirrors de Brasil porque los locales no estan con buena conectividad. Inclusive en algunas oportunidades he visto que faltan paquetes (me paso con una actualizacion de KDE, por ejemplo).

La otra es hacer backup de todos tus contenidos (/home/<user>) mas lo que tengas en /etc ya que llegado el caso de tener que recuperar algun archivo de configuracion tendrias practicamente todo entre esos dos respaldos. Esto en forma general, luego cada uno deberia saber si hay mas cosas de valor en otros directorios (/var o /opt por ejemplo) segun su criterio de instalacion aplicado.

Lo que suelo hacer es lanzar la actualizacion por la noche para terminarla por la mañana siguiente. Asi aprovecho que el enlace esta mas liberado cuando muchos duermen.

Otra recomendacion es leer detenidamente las propuestas de cambio/reemplazo opcionales de archvos de configuracion (esos dialogos que suelen aparecer cuando comienzan a aplicarse los cambios, luego de haber bajado todos los paquetes).

Cuando digo leer detenidamente me refiero a ver de que se tratan esos cambios ya que a veces conviene reemplazar algun archivo por el propuesto por el upgrade y otras veces no (por ejemplo, en la actualizacion de 9.10 a 10.04 RC que hice, el archivo de configuracion del desktop de KDE seria reemplazado, si lo aceptaba tendria que reconfigurar el KDE nuevamente para que me quede como estaba originalmente).

Si pedis ver las diferencias te muestra que cosas quedan como estaba, que se va y que se incorpora, linea por linea de cada archivo (que en general son mas bien algunos pocos, dos o tres maximo dependiendo de cada instalacion).

Ver antes si se reportan problemas para hardware similar al que esas usando. Ahora tenes un sistema funcional, no tenes apuro ni urgencia ni es critico que actualices, tomate tu tiempo para no sufrir en el proceso (y de paso dejas que lleguen los ultimos arreglos y se libere la demanda en los mirrors).

---

### Post by totolinux on 2010-04-30
Hola te cuento mi experiencia yo tenia 9.04 en una notebook pakcar bell easynote 355 funcionando a full porque en 9.10 tenía que cambiar varios parámetros del kernel para funcionar.
Bajé al cd alternate rc de la 10.04 y el live cd para ver que tal y funcionaba todo así que actualicé a 9.10 desde internet (cambien al reiniciar el kernel anterior que funcionaba bien), luego actualicé a 10.04 con el alternate cd.
Con respecto a las preguntas que te hace el sistema en el caso de gnome fueron si quería conservar el archivo de configuración de networkmanager o algo así.
En lo que respecta al servidor de brasil debe estar saturado porque me funciona muy lento así que estoy en patán y  va muy rápido para instalar las últimas actualizaciones.
Ademas debo decir que estoy impresionado con esta rc :)

---

### Post by sitiomatic on 2010-04-30
Yo pensaba esperar a que alguno actualice y cuente la experiencia, pero, como soy un ansioso, me baje el alternate, lo monte para no quemar un cd y le di de una.
Mi maquina no tiene dual boot, solo ubuntu.
Es la primera vez que no tuve NI IDEA de lo que iba a instalar, no vi la alpha, ni la beta, ni la rc, ni lei nada sobre la nueva version.
Demoro 2 horas y algo, siempre que me pregunto que queria hacer con alguna configuracion, le di a conservar la que esta, es la opcion que sale por defecto.
Resultado: Anda de 10, ningun problema, todo funciona como antes e inclusive respeto mis decisiones. Por ejemplo yo uso wicd y no networkmanager.
Uso pidgin y no empathy. Todo fue respetado.
El lampp que tenia sigue funcionando perfecto. (le di que conserve el php.ini tambien)
El wifi led sigue andando.
En fin, esta vez 10 puntos para todos.
Es la primera vez que no tengo que formatear e instalar de cero despues de fracasar un update.
Estoy feliz :)

---

### Post by infernus92 on 2010-04-30
gracias por las recomendaciones... las voy a tener en cuenta para cuando actualice :)

Saludos

---

