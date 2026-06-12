---
title: "Programar aplicaciones de escritorio en Ubuntu 11.04"
date: 2011-05-08
forum: Comunidad
---

### Post by andresjb on 2011-05-08
Hola gente!

Me llamo Andrés y soy prácticamente nuevo en Ubuntu. Ya había escrito en el foro hace un tiempo porque tenía problemas para instalarlo, pero el año pasado pude cambiar la PC y acá estoy, contento con Ubuntu 11.04 (recién instalado). :D

Hacía mucho que me quería cambiar de SO (siempre use WinXP y ahora 7), pero a Ubuntu no hay con que darle.

Mi pregunta era la siguiente: ¿Que lenguajes e IDEs hay para programar aplicaciones de escritorio para Ubuntu?

Se programar en Visual Basic 6 (:oops:), C, C# (mi favorito en éste momento) y he visto poco de algún que otro lenguaje más como Pascal y SmallTalk. Estoy dispuesto a aprender cualquier lenguaje que sirva.

Mi idea es hacer aplicaciones de propósito general para escritorio, por diversión y por negocio :D. También quisiera poder usar MySQL.

Perdón por éste mensaje largo y tedioso.

Desde ya, muchas gracias por la ayuda que me puedan dar.

Nos vemos por el foro. :P

Saludos.

---

### Post by juancarlospaco on 2011-05-09
> **andresjb said:**
> Hola gente!

Hola   ^&#8255;^

> **andresjb said:**
> 
Mi pregunta era la siguiente: ¿Que lenguajes e IDEs hay para programar aplicaciones de escritorio para Ubuntu?

Lenguajes, hay de todos colores y gustos.
IDEs, hay de todos colores y gustos.
Lo bueno es que todo es Libre!, 
con codigo y documentacion de IDEs, Lenguajes, Librerias, APIs, etc.

> **andresjb said:**
> Se programar en Visual Basic 6 (:oops:), C, C# (mi favorito en éste momento) y he visto poco de algún que otro lenguaje más como Pascal y SmallTalk. Estoy dispuesto a aprender cualquier lenguaje que sirva.


De esa lista, C es el mas interesante de los que mencionas.
Todos los lenguajes sirven de alguna manera, en determinada medida y nicho tecnico.
Igualmente muchos de esos se frecuentan mas solo en la plataforma de Windows.

> **andresjb said:**
> Mi idea es hacer aplicaciones de propósito general para escritorio, por diversión y por negocio :D. También quisiera poder usar MySQL.

Interesante, pienso algo similar, por diversion, no es mi favorito la Web. 
Podes probar usar SQLite que para Desktop anda re bien.
La base de SQLite, Python y Vim ya viene instalado en Ubuntu, 
no las herramientas de desarollo y IDEs para programar.


La orientacion que te puedo dar es tendenciosa, pero bueno... 
conociendo esos lenguajes que mencionas, si te diria Bash te aburris enseguida;
es lo que yo uso y me agrada, podes investigar el Lenguaje Python:

[http://python.org/about/](http://python.org/about/)

Como IDE uso Vim (Personalizado) en Linea de comandos, o si es con Interface Grafica Ninja:

[http://ninja-ide.org/ide.html](http://ninja-ide.org/ide.html)

un Hola Mundo en Python seria:

```
print ('Hola Mundo')
```

Cualquier cosa que necesites avisa.
:p

---

### Post by andresjb on 2011-05-09
> **juancarlospaco said:**
> Hola   ^&#8255;^



Lenguajes, hay de todos colores y gustos.
IDEs, hay de todos colores y gustos.
Lo bueno es que todo es Libre!, 
con codigo y documentacion de IDEs, Lenguajes, Librerias, APIs, etc.



De esa lista, C es el mas interesante de los que mencionas.
Todos los lenguajes sirven de alguna manera, en determinada medida y nicho tecnico.
Igualmente muchos de esos se frecuentan mas solo en la plataforma de Windows.



Interesante, pienso algo similar, por diversion, no es mi favorito la Web. 
Podes probar usar SQLite que para Desktop anda re bien.
La base de SQLite, Python y Vim ya viene instalado en Ubuntu, 
no las herramientas de desarollo y IDEs para programar.


La orientacion que te puedo dar es tendenciosa, pero bueno... 
conociendo esos lenguajes que mencionas, si te diria Bash te aburris enseguida;
es lo que yo uso y me agrada, podes investigar el Lenguaje Python:

[http://python.org/about/](http://python.org/about/)

Como IDE uso Vim (Personalizado) en Linea de comandos, o si es con Interface Grafica Ninja:

[http://ninja-ide.org/ide.html](http://ninja-ide.org/ide.html)

un Hola Mundo en Python seria:

```
print ('Hola Mundo')
```

Cualquier cosa que necesites avisa.
:p


¡Muchas gracias por la respuesta! 

Cuando leía tu mensaje me acordé de Java. ¿Es bueno para aplicaciones de escritorio? A mi siempre me pareció que consumía muchos recursos (porque tenía una PC vieja) y que era lento. Además, teniendo en cuenta que ya conozco C#, calculo que no me será tan difícil de aprender Java porque la sintaxis es muy parecida.

Bueno, no jodo más :D, gracias por la info.

Saludos.

---

### Post by juancarlospaco on 2011-05-09
Ni idea, ninguna aplicacion de Ubuntu viene hecha en Java, no se si sera muy usado en Desktops,
la ultima cosa que probe en Java era el JDownloader y lo cambie por Tucan, por que era muy lento.

---

### Post by MeduZa on 2011-05-09
si te vas por el lado de C o C++ (también soporta otros creo) Anjuta sin dudarlo!

si lo que queres es C# mono es lo tuyo.

---

### Post by andresjb on 2011-05-09
Estuve mirando mucho por internet y más o menos me voy decidiendo por C++, aunque todavía tengo mis dudas.

El otro problema que tengo es que quiero poder usar MySQL y que ande bien. Me gustaría seguir con C# usando Mono pero tengo miedo (injustificado) de que Mono no ande bien con MySQL.

Y algo que me gustaría es un IDE donde se pueda hacer la interfaz gráfica al estilo de Visual Studio y que tenga buenos controles para utilizar.

Muchas gracias a todos por las respuestas.

Perdonen que sea tan pesado. :oops:

---

### Post by juancarlospaco on 2011-05-09
QT Designer

---

### Post by MeduZa on 2011-05-13
> **andresjb said:**
> 
Y algo que me gustaría es un IDE donde se pueda hacer la interfaz gráfica al estilo de Visual Studio y que tenga buenos controles para utilizar.



anjuta + glade con eso podes dibujar el entorno gráfico y después mandarle código, yo trabajo de esa manera, solo que glade se conecta mejor con C que con C++ pero no es ningún problema solo tenes que leer un poco las guiás.

Glade se integra a anjuta sin problemas o lo pones usar aparte.

---

### Post by andresjb on 2011-05-17
Muchas gracias por sus respuestas!

Ya me decidí por C y Anjuta. Ahora quedará empezar a usarlo y ver como me sale :D.

Saludos, y gracias de nuevo!

---

### Post by juancarlospaco on 2011-05-19
Que bueno, espero compartas las aplicaciones y el codigo con nosotros...   &#664;&#8255;&#664;

---

### Post by MeduZa on 2011-05-25
yo en estos dias voy a empezar a laburar de nuevo en mi [LCDspicer]("http://lcdspicer.sourceforge.net/") y lo voy a cambiar todo, en ese programa laburo c++ con anjuta y glade

---

