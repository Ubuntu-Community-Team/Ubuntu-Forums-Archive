---
title: "Posible problema?"
date: 2008-09-20
forum: Comunidad
---

### Post by Guillermo08 on 2008-09-20
Hola, soy nuevo por aquí, el año pasado bajé Ubuntu 7.10 y lo probé en el live CD, ahora bajé el 8.04 y lo probé, el tema es que desde hace un año quiero instalarlo en la computadora que ya tengo, pero me dijeron que no conviene tener dos sistemas operativos en la misma máquina, 1- Eso es cierto?:confused:
2-Y si compro otro disco e instalo Linux ahí?
Gracias!!

---

### Post by santiagoward2000 on 2008-09-20
BIENVENIDO!

> **Guillermo08 said:**
> pero me dijeron que no conviene tener dos sistemas operativos en la misma máquina, 1- Eso es cierto?:confused:
2-Y si compro otro disco e instalo Linux ahí?

La verdad que es la primera vez que escucho eso... Acá somos varios los que tenemos 2 (o algunos más) sistemas en la misma máquina. Yo NUNCA tuve ningún problema con eso.
Comprar otro disco para hacer instalarlo puede complicarte las cosas para configurar el grub (el programa que cuando prendés la máquina te deja elegir en qué sistema querés entrar). Se puede hacer, pero no veo que ganes nada (aparte del espacio, claro).
Si te sigue preocupando tener los 2 juntos, podés probar con Wubi, que te deja instalar Ubuntu dentro de Windows, como si fuera un programa más. (Aunque personalmente nunca lo usé, así que no sé cómo anda).
Si tenés alguna duda sobre cómo instalarlo, preguntá!
SUERTE!

---

### Post by eldragon on 2008-09-20
yo nunca lo probe, porque directamente empeze con una maquina vieja como mi banco de prueba...  pero deberia de andar sin problemas. el instalador de ubuntu del live cd re conoce windows. y ayuda a particionar..

---

### Post by pol666 on 2008-09-20
Osea es mejor tenerlo en un solo disco que en 2. 

te digo tengo 5 So y puedo levantar 3 por que los que estan en el otro disco no los puedo hacer funcionar...cuestiones de grub.

---

### Post by Guillermo08 on 2008-09-20
Grcias!
Entonces no le hace mal a la máquina?
Bueno, entonces creo que voy a empezar a liberar espacio en el disco, y después (en unas horas) voy a hablar con el que me vedió la máquina a ver que dice. 
(siempre me pasa que cuando voy a averiguar algo que quiero hacer con la coputadora no conviene! esta es la primera vez que todo va bien!!:) jeje)
Ya me van a ver dentro de poco preguntado algo sobre la instalación...jeje

---

### Post by rojojuan on 2008-09-20
Yo tengo tres discos en la pc y todo anda de diez. Ubuntu lo tengo en el tercer disco. El grub perfecto. Hay que tener clara la identificación de los discos por el sistema: hd0, hd1, hd2 que es igual a sda, sdb, sdc. En grub creo recordar que es hd y en el sistema sd.

---

### Post by faktorqm on 2008-09-20
Hola y bienvenido al foro. 
El que te dijo que no te convenia instalar varios sistemas operativos no sabe absolutamente nada de computacion/informatica y afines.
Yo en una epoca tenia 3 SO, un windows xp y dos gnu/linux y todo andaba sobre ruedas. Podes tener un windows, un gnu/linux y un opensolaris si tenes ganas, o un openbsd.
Si queres informarte mas por algun motivo, no tenes mas que buscar en google o en la guiaubuntu que ahi dice todo. Esperamos tus consultas.
Salu2!

---

### Post by Guillermo08 on 2008-09-20
Bueno, muchas gracias a todos
Ya instalé ubuntu, le puse un disco de 40 GB a la máquina y lo instalé ahí!!:) Lo único que me impide estar escribiendo esto desde Linux, es que no se conectarlo a internet, me puden dar una mano?

---

### Post by santiagoward2000 on 2008-09-20
> **Guillermo08 said:**
> Bueno, muchas gracias a todos
Ya instalé ubuntu, le puse un disco de 40 GB a la máquina y lo instalé ahí!!:) Lo único que me impide estar escribiendo esto desde Linux, es que no se conectarlo a internet, me puden dar una mano?

¿Podés decirnos qué servicio tenés (Speedy, Arnet...) y qué tipo de modem (ethernet, usb)?

---

### Post by Guillermo08 on 2008-09-20
Nop, Anteldata, soy de Uruguay.

---

### Post by santiagoward2000 on 2008-09-20
> **Guillermo08 said:**
> Nop, Anteldata, soy de Uruguay.

Ahhh, igual lo más importante es el tipo de modem. ¿Qué modelo es? ¿Que tipo de conexión tiene?

---

### Post by Guillermo08 on 2008-09-20
Bueno, me matas con esa pregunta jeje ni idea
Te pongo unas fotos del modem:

[http://img218.imageshack.us/img218/3523/p9140259zm1.jpg](http://img218.imageshack.us/img218/3523/p9140259zm1.jpg)

[http://img216.imageshack.us/img216/353/p9140260hu1.jpg](http://img216.imageshack.us/img216/353/p9140260hu1.jpg)

---

### Post by santiagoward2000 on 2008-09-20
Por lo que veo, tiene un cable ethernet, por lo que no debería haber problemas. Andá a Aplicaciones>Accesorios>Terminal y escribí:
```
pppoeconf
```
Te va a pedir primero tu contraseña de Ubuntu. Después seguí los pasos para configurar tu servicio, nombre de usuario y contraseña.
Cualquier duda avisá.
Saludos!

---

### Post by faktorqm on 2008-09-20
La marca es ZTE, fijate el modelo que creo que esta abajo por que la foto que pusiste esta fuera de foco.......
Si no dice ahi, debe decir abajo. Yo lo que te recomiendo es no usar pppoeconf, por que seguro es un modem ruteable, y te conviene usar las capacidades del modem y no las de tu pc. Cualquier cosa pregunta salu2!

---

### Post by Guillermo08 on 2008-09-20
Muchísimas gracias!!!! Ya estoy en Linux.:)

---

