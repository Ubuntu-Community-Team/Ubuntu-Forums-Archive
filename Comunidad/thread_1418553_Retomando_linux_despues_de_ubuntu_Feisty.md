---
title: "Retomando linux despues de ubuntu Feisty"
date: 2010-02-28
forum: Comunidad
---

### Post by bronto64 on 2010-02-28
Hola, supongo que por la cantidad de dudas deberia postear en varios threads, pero como leo antes de tocar algo les cuento mi situacion y ustedes me guian, despues ire preguntasndo sobre algun topico en gral mas especificamente.
Bueno ahora estoy asi:
tengo experiencia con linux, pero hace un par de años que no toco nada (mas que nada fiaca y poco tiempo), he probado e instalado desde red hat 2.0 en adelante casi cualquier distro. Ahora estoy saliendo del entorno Windows para configurar en casa mis compus, todas con ubuntu.
Las preguntas empiezan en: (por favor podrian decirme de donde leer? )
ya instale desde el alternate cd  esta maquina y supongo que las demas tambien, tengo algunas trabas, el gestor de paquetes por defecto en el 9.10 no me permite instalar APT, rpm o lo que sea (seguro algo mal configurado) de donde leo para resolverlo?
el entorno de escritorio esta bien, pero a mi me gusta "toquetearlo, en feisty habia instalado Beryl-Compiz, aca no se donde esta cada cosa (estoy medio perdido en el koala)
que es eso de los plasmoids y otras cosas nuevas que veo en los escritorios en el foro.
Los utilitarios para manejo de particiones y otras cosas relativas a los discos no los encuentro (no puedo poner el automount de los discos windows )
Bueno esto es para empezar espero no parecer pesado, solo tirenme un cable, seguro que despues arranco.
Gracias
Federico.

---

### Post by guillermolisi on 2010-02-28
> **bronto64 said:**
> Hola, supongo que por la cantidad de dudas deberia postear en varios threads, pero como leo antes de tocar algo les cuento mi situacion y ustedes me guian, despues ire preguntasndo sobre algun topico en gral mas especificamente.
Bueno ahora estoy asi:
tengo experiencia con linux, pero hace un par de años que no toco nada (mas que nada fiaca y poco tiempo), he probado e instalado desde red hat 2.0 en adelante casi cualquier distro. Ahora estoy saliendo del entorno Windows para configurar en casa mis compus, todas con ubuntu.
Las preguntas empiezan en: (por favor podrian decirme de donde leer? )
ya instale desde el alternate cd  esta maquina y supongo que las demas tambien, tengo algunas trabas, el gestor de paquetes por defecto en el 9.10 no me permite instalar APT, rpm o lo que sea (seguro algo mal configurado) de donde leo para resolverlo?
el entorno de escritorio esta bien, pero a mi me gusta "toquetearlo, en feisty habia instalado Beryl-Compiz, aca no se donde esta cada cosa (estoy medio perdido en el koala)
que es eso de los plasmoids y otras cosas nuevas que veo en los escritorios en el foro.
Los utilitarios para manejo de particiones y otras cosas relativas a los discos no los encuentro (no puedo poner el automount de los discos windows )
Bueno esto es para empezar espero no parecer pesado, solo tirenme un cable, seguro que despues arranco.
Gracias
Federico.
Movi el thread a Comunidad ya que hay varios temas que tocas con tu mensaje y la idea del foro es que las consultas sean especificas para facilitar las respuestas y, mas importante aun, la busqueda de casos y sus soluciones por parte de terceros.

Respecto de APT, podrias decirnos que mensaje o sintoma observas cuando queres instalar paquetes ? En KDE se usa KpackageKit y en Gnome, Synaptic.

Los plasmoides existen solo en KDE 4 ya que son parte del nuevo desarrollo que dio origen a esa version de KDE (el backend que permite que funcionen se llama Plasma).

El Gestor de Particiones, Gparted en Gnome, no existe en KDE, por lo tanto aclaranos si estas usando KDE o Gnome para aconsejarte (esto inducido por tu pregunta sobre los plasmoides).

Que serian las otras cosas relativas a los discos (y al automount) ?

---

### Post by bronto64 on 2010-02-28
Antes que nada gracias por la rapidez de la respuesta, como te imaginaras, estoy despertando algunas neuronas (mucho windows vio? ), ya encontré como montar y desmontar (la terminal sigue siendo una buena opción, mas ahora con apt, me fue facil encontrar e instalar algunas cosillas). 
Ahora que empiezo a despegar algunas preguntas mas concretas. Como hace mucho que no meto mano, hoy que es mas practico y mejor como interface KDE o Gnome (yo siempre use o Gnome o Enlightment , pero veo que KDE ha crecido mucho), teniendo en cuenta que estamos hablando de un uso hogareño en red (voy a poner en las compus, algun reproductor multimedia, open Office y alguna aplicacion educativa para los mas chicos), o sea voy a compartir archivos dentro de la red y navegar.
gracias y espero poder colaborar cuando despierte alguna neurona mas, ya que suelo andar chusmeando de todo un poco.
Federico.

---

### Post by guillermolisi on 2010-02-28
> **bronto64 said:**
> Antes que nada gracias por la rapidez de la respuesta, como te imaginaras, estoy despertando algunas neuronas (mucho windows vio? ), ya encontré como montar y desmontar (la terminal sigue siendo una buena opción, mas ahora con apt, me fue facil encontrar e instalar algunas cosillas). 
Ahora que empiezo a despegar algunas preguntas mas concretas. Como hace mucho que no meto mano, hoy que es mas practico y mejor como interface KDE o Gnome (yo siempre use o Gnome o Enlightment , pero veo que KDE ha crecido mucho), teniendo en cuenta que estamos hablando de un uso hogareño en red (voy a poner en las compus, algun reproductor multimedia, open Office y alguna aplicacion educativa para los mas chicos), o sea voy a compartir archivos dentro de la red y navegar.
gracias y espero poder colaborar cuando despierte alguna neurona mas, ya que suelo andar chusmeando de todo un poco.
Federico.
No hay nada escrito sobre cual es el mas apropiado para cada uno. Tanto Gnome como KDE tienen sus cosas buenas y malas y esta en el "feeling" propio que cada uno experimenta cuando los usa decidir por uno o por otro (algunos usan los dos segun las circunstancias).

Una aclaracion: Los dos escritorios graficos mas utilizados y conocidos son los que mencione. Agregale LXDE (Lubuntu), XFCE (Xubuntu) y algun otro que queda en el tintero. El resto son gestores de ventanas (E!, BlackBox, etc.) y la diferencia esta en que un escritorio grafico es un entorno operativo integrado, con funcionalidades propias que mejoran su desempeño y la experiencia del usuario. Un gestor de ventanas solo se encarga de eso y no posee funcionalidades integradas entre sus componentes (mas alla del gestor mismo).

En general, los paquetes mas completos y el mas amplio surtido de software educativo esta desarrollado para KDE pero eso no quita que encuentres algunos paquetes que lo esten para Gnome.

De hecho uso KDE desde que incursione en Linux pero uso Gnome o componentes y paquetes de el para ciertas cosas. Y como hago yo, hay muchos mas casos similares.

Multimedia, OO y aducacion funcionan por igual en cualquiera de los dos (tres o cuatro) escritorios graficos comunmente disponibles.

---

### Post by bronto64 on 2010-03-01
Bueno, muchas gracias por la respuesta. Si tenia lo de los gestores de ventanas, yo use el E¡ porque era el que mas me dejaba customizar, el blacbox era demasiado minimalista. La utlima vez que use xfce, era casi una interface para celular :) . Voy a probar con el nuevo KDE a ver que onda, los graficos (iconos y etc. ) son medio "duritos", pero con la variedad que vengo viendo seguro alguno que me guste encontrare.
Bueno ahora estoy migrando todas las compu en casa (algunos de los chicos estan medio mal porque les baje el Lineage de un plumazo, pero bueno en todo caso si hacen merito, vere de terminar de toquetear el wine para ver si lo arranco desde ahi), si me surgen nuevas cosas preguntare y si encuentro problemas y los soluciono, contare como.
Federico.

---

### Post by juancarlospaco on 2010-03-01
QTParted no seria como GParted pero para KDE *(?)*

---

### Post by guillermolisi on 2010-03-01
> **juancarlospaco said:**
> QTParted no seria como GParted pero para KDE *(?)*
Si, es el equivalente pero basado en Qt. Si bien los dos hacen basicamente lo mismo, personalmente me gusta mas Gparted ya que me parece mejor logrado (aunque no sea Qt :) )

---

### Post by juancarlospaco on 2010-03-02
smartpm es un buen gui para gestor de paquetes, si no te gusta el de KDE, 
no usa mucha dependencia asi no te trae medio gnome,
es muy bueno, fue creado por canonical y conectiva en el 2006.

---

### Post by guillermolisi on 2010-03-02
> **juancarlospaco said:**
> smartpm es un buen gui para gestor de paquetes, si no te gusta el de KDE, 
no usa mucha dependencia asi no te trae medio gnome,
es muy bueno, fue creado por canonical y conectiva en el 2006.
Otro caso de ejemplo. Si bien KpackageKit funciona, muchas veces recurro a Synaptic (que esta hecho para Gnome) y otras a Aptitude (consola).

Synaptic posee un buscador mas intuitivo que KpackageKit, al igual que Aptitude, y eso te facilita las cosas muchas veces.

---

