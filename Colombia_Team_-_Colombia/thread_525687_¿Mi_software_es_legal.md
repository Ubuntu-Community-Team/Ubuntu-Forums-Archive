---
title: "¿Mi software es legal?"
date: 2007-08-14
forum: Colombia Team - Colombia
---

### Post by sirgazil on 2007-08-14
¡Hola equipo!

Cuando instalé Ubuntu 7.04 me vi obligado a instalar también un paquete que se llama **Ubuntu restricted extras**, porque uso un computador familiar. Este paquete permite la compatibilidad con varios formatos que no son libres, como el formato mp3.

Mi inquietud nace de la descripción que se da de este paquete en **Añadir y quitar aplicaciones**, donde se dice:

> Tenga en cuenta que los paquetes del repositorio multiverse están restringidos por asuntos legales o de copyright en algunos países.

Mi pregunta es:

¿Colombia es uno de esos países?
Cuando instalé este paquete ¿hice algo ilegal?

Yo quiero que mi instalación de Ubuntu también esté libre de problemas legales. Esta también es una de las razones por las cuales me deshice de Windows.

Saludos y gracias de antemano,

---

### Post by Alterax on 2007-08-14
Creo que su software es legal.

---

### Post by sirgazil on 2007-08-18
> Creo que su software es legal.

No, en serio.

O tal vez alguien podría decirme cómo saber qué bibliotecas se instalan con el paquete en cuestión. Así yo podría leer las licencias y averiguar si hay alguna incompatibilidad con las leyes colombianas.

Saludos,

---

### Post by luisg on 2007-08-19
> **sirgazil said:**
> No, en serio.

O tal vez alguien podría decirme cómo saber qué bibliotecas se instalan con el paquete en cuestión. Así yo podría leer las licencias y averiguar si hay alguna incompatibilidad con las leyes colombianas.

Saludos,

No le había respondido porque en realidad no soy experto en temas legales, pero hasta donde se no hay ninguna reglamentación en Colombia que prohiba específicamente usar los paquetes de ubuntu-restricted-extras. Aquí sin embargo hay que hacer una distinción entre "ilegal" y "no libre". Por ejemplo, yo estoy casi seguro que los paquetes del sun-java6 no son ilegales de instalar, pero como no son completamente libres, pues entonces los dejan ahí.

Si quiere ver qué librerías usa, abra Synaptic, busque el paquete que le intesa, lo selecciona y oprime el botón de propiedades, en la pestaña Dependencias encontrará los paquetes de los cuales depende.

Es posible que tenga que repetir el proceso para esos paquetes, ya que algunos de ellos también son metapaquetes.

Suerte.

---

### Post by sirgazil on 2007-08-20
> Si quiere ver qué librerías usa, abra Synaptic, busque el paquete que le intesa, lo selecciona y oprime el botón de propiedades, en la pestaña Dependencias encontrará los paquetes de los cuales depende.

¡Gracias luisg, eso voy a hacer!

---

### Post by sirgazil on 2007-08-20
Definitivamente creo que malinterpreté esta advertencia:

> Tenga en cuenta que los paquetes del repositorio multiverse están restringidos por asuntos legales o de copyright en algunos países.

Yo pensé que quería decir que en algunos países podría ser ilegal instalar estos paquetes. Pero parece que solo es un aviso para que los usuarios sepan que algunos de los elementos que se van a instalar no son libres.

Estas son las dependencias del paquete Ubuntu restricted extras:

* gstreamer0.10-plugins-ugly: Bajo licencia LGPL
* gstreamer0.10-plugins-ugly-multiverse: Bajo licencia LGPL
* msttcorefonts: limitaciones por copyright
* flashplugin-nonfree: No es libre
* sun-java6-plugin: No es libre

Las licencias pueden encontrarse en /usr/share/doc

¡Que vergüenza! :oops: Por favor perdonen el alboroto.

---

### Post by evalckea on 2007-12-04
Tengo entendido que en Ubuntu 7.10 Edgy prácticamente no hay que usar restringidos, la verdad es que incluso en Firefox para los plugins ofrece opciones libres completamente, si quieres estar seguro pásate al Edgy

Efraim
Cali - Colombia

---

### Post by jlpdu72 on 2007-12-17
Hola,

Piense en el siguiente ejemplo:

A usted le pueden regalar una escoba y es legal... ahora si con esa escoba mata a alguien eso no es legal.

Las distribuciones de linux se las regalan. Ahora hay formatos o actividades que ud puede o no segun su criterio realizar o ejecutar. Los plugins a los que se refiere usted son por lo que lei rapidamente son para usar formatos mp3 y m4a, pienso que es musica, por lo tanto usted mas que nadie sabra como obtiene sus archivos de musica si de forma legal o ilegal. Hay algunas distribuciones de linux que han pagado por poder usar esos formatos, es el caso de mandriva quu puede usar mp3. Ahora el formato m4a (apple-itunes) tiene unos derechos que no se han pagado por ninguna distribucion de linux que yo conozca y por ende hay que bajar los plugins que usted menciona. 

Resumiendo, su software es legal, por lo menos todo lo que diga GNU en la licencia, los plugins tambien son legales. Ahora el uso que le de a estos es lo que se podria discutir, sobre todo con el tipo de archivos que estamos intentando ejecutar.

Saludos.

---

