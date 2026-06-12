---
title: "Ubuntu Edicion de 64Bits"
date: 2010-08-17
forum: Comunidad
---

### Post by drazhe on 2010-08-17
Hola a todos, estoy por hacer una inversión y comprar una computadora monstruo como las que usan en la nave espacial **Enterprise de viaje a las estrellas** mas o menos y obviamente tengo pensado poner **Ubuntu**, pero en esta ocasión usar la versión de **64bits** para poder utilizar todo el potencial de dicho monstruo.
La pregunta que quiero hacer, es cuanto seria el espacio recomendado para dicha versión, en estos momentos con la de **32bits** le doy unos **50gb** mas o menos, y tenia pensado darle algo similar, pero cuanto me recomiendan que use?

---

### Post by guillermolisi on 2010-08-17
Disculpa que responda tu pregunta con otra pregunta (cosa que nunca me gusto hacer) pero esos 50Gb como los tenes distribuidos para Ubuntu ? Cuanto para /, cuanto para /home, etc. ?

---

### Post by drazhe on 2010-08-18
> **guillermolisi said:**
> Disculpa que responda tu pregunta con otra pregunta (cosa que nunca me gusto hacer) pero esos 50Gb como los tenes distribuidos para Ubuntu ? Cuanto para /, cuanto para /home, etc. ?

la verdad no tengo idea, mi HD es de 120gb, y aunque me gusta muchísimo Ubuntu, no puedo darle el total ya que para algunas aplicaciones aun sigo necesitando Windows, así que partí el rígido 70gb para win y 50gb para Ubuntu, ya que desde Linux puedo alcanzar la partición de Windows no me molesta tener algunas cosas metidas ahí (fotos, música, etc)

---

### Post by guillermolisi on 2010-08-18
Ok, entonces por que pensas que necesitarias mas espcio en el disco que lo que estas usando ahora ?
Que sea de 32 o 64 bits no cambia cuanto espacio ocupa en el disco.

---

### Post by drazhe on 2010-08-18
> **guillermolisi said:**
> Ok, entonces por que pensas que necesitarias mas espcio en el disco que lo que estas usando ahora ?
Que sea de 32 o 64 bits no cambia cuanto espacio ocupa en el disco.

Se que me van a putear mucho por lo que voy a decir ahora, pero nunca utilicé un Linux de 64bits y pensé que tenia mayores requerimientos con si pasa con Windows...
Gracias por el dato de cualquier manera...

---

### Post by alfplayer on 2010-08-18
64-bits requiere más memoria RAM.

---

### Post by joseluis on 2010-08-18
hola...
alfplayer ¿podrias dar algun detalle sobre esto que comentas de que 64 bits requiere más memoria Ram? En lo particular yo no veo diferencia, al menos me parece, pero es interesante si  podrías comentar un poco ese tema. Es muy interesante para mi.
Gracias

---

### Post by alfplayer on 2010-08-18
> **joseluis said:**
> hola...
alfplayer ¿podrias dar algun detalle sobre esto que comentas de que 64 bits requiere más memoria Ram? En lo particular yo no veo diferencia, al menos me parece, pero es interesante si  podrías comentar un poco ese tema. Es muy interesante para mi.
Gracias

Hola. No tengo más información a mano, pero seguramente se puede encontrar más información buscando en la web, por ejemplo, diferencia de uso de memoria entre Ubuntu 10.04 de 32 y 64 bits después que el sistema bootea por primera vez (sin modificar el sistema).

---

### Post by biale on 2010-08-18
Tomo un caso muy burdo. Suponiendo que se almacene una dirección absoluta en RAM, si se direcciona en 32 bits necesitaríamos ocupar 32 bits, si se direcciona en 64 bits necesitaríamos ocupar 64 bits.

---

### Post by joseluis on 2010-08-19
Lo que pude rastrear me llevan, aparentemente, a las siguientes conclusiones:
1. 64 bits permite usar sistemas de mas de 4 gigas de ram.
2. 64 bits es más apta para las tecnologías más modernas de 64 bits, y se comporta mejor en esos sistemas que una distro de 32 bits en un sistema de 64.
3. Nada encontré acerca de que 64 bits necesite más ram que uno de 32.

¿esta bien esto?

---

### Post by biale on 2010-08-19
Salvo kernel pae, ya si tenes 4 Gb de Ram, con un sist op en 32 bits vas a "ver" solo 3 Gb de Ram ...

Nadie lo dijo todavía, pero hay también problemas con algunas aplicaciones. Para mi ese tema puede ser mas importante que las diferencias en cuanto a la performance. Por ejemplo: ¿Seguirán los problemas con el flash?

---

### Post by alfplayer on 2010-08-19
> **joseluis said:**
> Lo que pude rastrear me llevan, aparentemente, a las siguientes conclusiones:
1. 64 bits permite usar sistemas de mas de 4 gigas de ram.
2. 64 bits es más apta para las tecnologías más modernas de 64 bits, y se comporta mejor en esos sistemas que una distro de 32 bits en un sistema de 64.
3. Nada encontré acerca de que 64 bits necesite más ram que uno de 32.

¿esta bien esto?

No le veo sentido al punto 2.

En cuanto a la diferencia de uso de RAM, hay muchas opiniones de usuarios en la web recomendando 32-bit para menor uso de memoria, especialmente en VPSs de poca memoria RAM. También encontré esta comparación con valores para 8.04 [http://gquigs.blogspot.com/2008/07/blog-post.html]("http://gquigs.blogspot.com/2008/07/blog-post.html")

---

### Post by guillermolisi on 2010-08-19
> **joseluis said:**
> Lo que pude rastrear me llevan, aparentemente, a las siguientes conclusiones:
1. 64 bits permite usar sistemas de mas de 4 gigas de ram.
2. 64 bits es más apta para las tecnologías más modernas de 64 bits, y se comporta mejor en esos sistemas que una distro de 32 bits en un sistema de 64.
3. Nada encontré acerca de que 64 bits necesite más ram que uno de 32.

¿esta bien esto?
El punto 1 es cierto pero no excluyente. Con un kernel de 32 bits apropiado (pae) tambien podes acceder mas alla de los 4Gb RAM

Sobre el punto 2 no veo fundamento valido como para decir que es cierto o falso. En el laburo tenemos hardware de 64 bits corriendo Ubuntu server de 32 bits (pae) con 8 Gb RAM virtualizando maquinas y anda un avion.

Sobre el punto 3 hay muchisimo material en Ingles y Español sobre el tema, empezando por Wikipedia (citado oportunamente en una conversacion similar, aqui en este foro). De todas formas mi parecer es similar y parte desde los mismos fundamentos rudimentarios expuestos por biale para concluir que los sistemas (software) de 64 bits necesariamente consumen mas RAM que sus equivalentes de 32. Ahora, cuanto mas ? No tuve oportunidad (ni ganas, en realidad) de medir.

---

### Post by joseluis on 2010-08-20
ok...yo estoy usando de 64 bits en un amd64, con 2 Giga de RAM, con estas observaciones, lo mejor sería usar de 32. Si es que todo lo dicho es así.

---

### Post by biale on 2010-08-20
> con estas observaciones, lo mejor sería usar de 32. Si es que todo lo dicho es así.

Hay algunos benchmarks dando vueltas por la Web. Para mi gusto y salvo el caso de tareas cpu intensivas, en los tiempos que corren las mejoras no son importantes. Aclaro que no analicé el tema a fondo.

Pero eso no significa necesariamente "que sea malo". La realidad es que la disyuntiva (y ni siquiera) solo aparece cuando pasamos los 3 Gb en uso de RAM, situación que en estaciones de trabajo no es la típica. 

Y supongo que la gente que hace CAD/CAM, simulación 3d y algunas ediciones ya migró hace rato.

Mas bien la pregunta que valdría la pena contestar sería: ¿con la versión en 64 bits (de lo que sea), has tenido problemas?

---

### Post by alfplayer on 2010-08-20
> **biale said:**
> Pero eso no significa necesariamente "que sea malo". La realidad es que la disyuntiva (y ni siquiera) solo aparece cuando pasamos los 3 Gb en uso de RAM, situación que en estaciones de trabajo no es la típica.

Posiblemente la mayoría tiene menos de 3 GB, pero también creo que hay muchos casos de estaciones de trabajo con más de 3 GB. La disyuntiva sí aparece con menos de 3 GB. Para menos de 3 GB el uso de RAM y la velocidad general del sistema y aplicaciones son o pueden ser importantes.

Hay informes de problemas de compatibilidad con 64-bits. Muchos se pueden resolver, pero con algún paso adicional desconocido por novatos, como la instalación de debs de 32 bits (muchos debs que no están en los repositorios de ubuntu no tienen versión de 64 bits).

---

### Post by z37a on 2010-08-21
> **alfplayer said:**
> Posiblemente la mayoría tiene menos de 3 GB, pero también creo que hay muchos casos de estaciones de trabajo con más de 3 GB. La disyuntiva sí aparece con menos de 3 GB. Para menos de 3 GB el uso de RAM y la velocidad general del sistema y aplicaciones son o pueden ser importantes.

Hay informes de problemas de compatibilidad con 64-bits. Muchos se pueden resolver, pero con algún paso adicional desconocido por novatos, como la instalación de debs de 32 bits (muchos debs que no están en los repositorios de ubuntu no tienen versión de 64 bits).

Yo soy usuario de 64bits en mi caso mas que nada lo uso por que tengo 4GB de ram(por ahora, pineso agregar otros 4) y la desktop la uso como para virtualizar a veces, pero tambien como para navegar y demas tareas simples que con 1GB me sobraria!!!

Si no tenes mas de 4GB es inutil, a menos claro que pienses ampliar la memoria a futuro y asi te evitas tener que migrar luego de 32 a 64 bits!

Y con lo de los paquetes como mencionan ahi, son muy pocos que no hay disponibles para 64 bits, por asi decirlo solo 1 paquete hay que no me funciona y tengo que instalar librerias de 32, el de flash, la alternativa es bajar la beta de flash para 64 bits que ya se quedo atras, peor ese es el unico que realmente me preocupa, es mas ahora mismo estoy usando una beta de firefox 4 y sin problemas, ya esta disponible para 64 bits!.

---

### Post by alfplayer on 2010-08-21
> **z37a said:**
> Yo soy usuario de 64bits en mi caso mas que nada lo uso por que tengo 4GB de ram(por ahora, pineso agregar otros 4) y la desktop la uso como para virtualizar a veces, pero tambien como para navegar y demas tareas simples que con 1GB me sobraria!!!

El uso que le doy a mi computadora principal es similar (uso PAE), pero con una diferencia: uso Chromium con muchísimas pestañas y es posible que use 4 GB casi totalmente.

> **z37a said:**
> Si no tenes mas de 4GB es inutil, a menos claro que pienses ampliar la memoria a futuro y asi te evitas tener que migrar luego de 32 a 64 bits!

No es así. Se puede usar PAE con menos de 4 GB y hasta 64 GB. Se instala el kernel PAE y se actualiza automáticamente en las actualizaciones normales de Ubuntu.

32 o 64 bits es una elección que depende de varios factores, y puede ser indiferente en algunos casos. Ubuntu ofrece las dos opciones. No hay una bien y otra mal.

---

### Post by guillermolisi on 2010-08-21
Ayer, casualmente, mientras esperabamos que unos servers terminen de hacer unos trabajos que habiamos iniciado, hablabamos sobre este tema con un amigo:
> Amigo: Pero la industria esta yendo a 64 bits. De hecho las versiones nuevas de Windows y otros productos de MS, solo estan en esa plataforma, asi que a los 32 bits les queda poco tiempo.

Yo: Fijate que los ejemplos que mencionas estan relacionados con los requerimientos de recursos de esos productos, mas precisamente referidos a cantidad minima de RAM, y es por eso que solo funcionarian en 64 bits, de ahi que MS lance versiones de sus SOs con caracteristicas que permitan usarlos (caso Exchange, SQL Server, SharePoint, etc.). Como las versiones server y desktop comparten el mismo kernel, son todos de 64 bits. No hay otra razon porque en ningun lado he visto mensajes como "mejora radicalmente el rendimiento de tu sistema usando software y hardware de 64 bits", como argumento de marketing.

---

### Post by biale on 2010-08-21
> ...en ningun lado he visto mensajes como "mejora radicalmente el rendimiento de tu sistema usando software y hardware de 64 bits", como argumento de marketing.

100% de acuerdo. Y todo induce a pensar que son muchísimas las piezas que estan funcionando en "modo compatible".

---

### Post by alfplayer on 2010-08-21
Me parece cierto lo que decís, Guillermo.

Además, creo que un sistema de escritorio solo de 64-bit es negativo para usar (o imposible de usar) en hardware viejo o con pocos recursos, y hace que distros como Puppy tengan cada vez más importancia. Además, hay que pensar que mucho hardware moderno como smartphones tienen memoria limitada comparando con un escritorio, y necesitan minimizar el espacio con energía.

---

