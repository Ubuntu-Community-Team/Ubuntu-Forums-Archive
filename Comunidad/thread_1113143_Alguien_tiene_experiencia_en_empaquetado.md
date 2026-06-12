---
title: "Alguien tiene experiencia en empaquetado?"
date: 2009-04-01
forum: Comunidad
---

### Post by pablo.s on 2009-04-01
Hola: Hace tiempo que quiero aprender a preparar debs. Hoy empecé
a ver el Wiki de MOTU, pero hay algunos puntos que están explicados
muy vagamente y no logro pasar de cierto punto.
¿Alguno de ustedes tiene experiencia con empaquetado y puede ayudarme
a terminar un deb? Gracias.

---

### Post by guisheca on 2009-04-01
Verás, mucho mucho no se del tema, pero visto y conciderando que no estás recibiendo respuestas te voy a dar mi humilde aporte.
Tenés por un lado debcreator que te crea debs a partir de fuentes, pero tengo entendido que solamente sirve para tu propia pc. Pero tiene sus limitaciones. Te dejo dos enlaces, uno a un post de taringa que hice yo y otro a la página oficial.

[URL="http://taringa.net/posts/linux/1389685/Debcreator-crea-debs-a-partir-de-fuentes.html"]
Enlace1[/URL]

[Enlace2]("http://debcreator.cmsoft.net/")

Después conozco otra herramienta: El comando checkinstall (sudo aptitude checkinstall). Te descargás las fuentes del programa y compilas como de costumbre. Sólo que al final, en ves de poner "sudo make install" ponés "sudo checkinstall" y te genera un deb :p.

Vale decir que nunca pude crear ningún deb con estos métodos, pero quizás vos estes sabiendo algo que yo no :-)

Espero te sirva, saludos.

---

### Post by Hei Ku on 2009-04-01
Te puedo conseguir los scripts que usamos para el PPA de KMyMoney, si te sirve de algo.

Te trabaste en algun punto en particular?

---

### Post by pablo.s on 2009-04-01
No cazo la parte de todos los documentos que 
hay que armar para las descripciones, copyright,
y el archivo control. Leí en el Wiki que si no
están de forma aceptable no te forma el deb al
final con dh-make. También me vi los videos que
han puesto de MOTU y le sale todo barbaro a 
Daniel Holbach, pero a mi parece que no.
Aparte hay un par de paquetes que quiero armar
con programas compilados (son de Java) y no lo
estoy haciendo bien. La onda es que sean paquetes
con clave GPG y para ser bajados desde mi PPA, por
lo tanto tienen que ser "kosher".
Si tenés los scripts y podés pasarmelos buenisimo,
que veo como sale. Saludos y gracias.

---

### Post by infernus92 on 2009-04-01
no se si viene al caso... pero muchas veces cuando sos como yo y no sabes manejar paquetes manualmente y rogas que el programa que estas buscando este en formato deb, lo encontras en otro... tgz, tar.bz, rpm, slm o pkg... lo queres instalar pero no sabes hacerlo... googleando encontre un comando interesante... se llama alien
lo que hace es convertir de un formato de paquetes a otro
por ejemplo... si tengo un paquete que se llama paquete1.tgz y lo quiero instalar en ubuntu con un doble click y listo
```
sudo alien -d paquete1.tgz
```

me resulto muy util... tambien se puede usar al reves... tngo un paquete deb y lo quiero transformar por ejemplo en rpm

```
sudo alien -r pquete2.deb
```

para obtenerlo solamente alcanza con poner
```
sudo aptitude alien
```

no creo que es lo que quieras pablo... pero creo que a otros les va a servir

Saludos

---

### Post by pablo.s on 2009-04-01
> **infernus92 said:**
> no creo que es lo que quieras pablo... pero creo que a otros les va a servir Saludos

Lo que vale es la intención... Estoy a un pelo de
sacarle la vuelta... Conseguí un tutorial muy bueno
de un alemán que explica paso a paso y con su
propio proyecto lo que estoy tratando de hacer.

Es probable que mañana ya tenga el primer
paquete para testear, que es el gestor de descargas
Tucán 0.3.6. No voy a empezar empaquetando
algo super complejo y este programa me parece que
va a tener testers dispuestos. Saludos.

---

### Post by josecuervo86 on 2009-04-01
Apenas lo armes colgalo asi lo pruebo! ;)

---

### Post by clasificado on 2009-04-02
¿No te servirá el paquete que arma el checkinstall?

---

### Post by pablo.s on 2009-04-02
No usa checkinstall en el proceso. Usa dh-make 
y dpkg-buildpackage.
Ahora mismo estoy buscando por todo Internet
la forma correcta de hacerlo porque resulta que
como quiero hacer paquetes de aplicaciones en
Python y no necesitan compilación se hace con
otro tipo de descripción en el archivo rules.
El tema es que seguí un tutorial en video de un
programador alemán que supuestamente daba
resultado pero a mi no y buscando en este mismo
foro alguien escribió que ese tutorial está mal
realizado porque no es la forma correcta de hacer
ese tipo de empaquetado.
Otro tema es que iba a empaquetar Tucán al
release 0.3.6 y resulta que en Getdeb ya está
disponible. Asi que me quedan dos opciones:
o le pido ayuda a la gente de Getdeb para que me
den unas clases o me hago apadrinar por algún
MOTU que tenga disponibilidad.
Saludos.

---

### Post by clasificado on 2009-04-02
Estoy convencido de que cualquier ser humano no usa checkinstall para hacer debs :KS

pero yo, que soy medio animal, cuando quiero compilar uso checkinstall, de esa forma se hace un deb, y se instala.

Y el deb queda, por lo que me lo guardo por si después quiero hacer lo mismo de nuevo, y me evito el checkinstall

Pero tu camino me parece mas correcto, siga nomás y vuelva que nos interesa :P si llegas a un modelo tuto-able, podemos hacer que lo revisen los de ubuntu-ar para mandarlo a su excelente lista de tutoriales y que quede haciendo el bien por toda la eternidad

clasificado

---

### Post by Hei Ku on 2009-04-02
Pablo, consulte con el usuario que hace nuestro PPA. Me dijo que no usa scripts, simplemente modifica el archivo rules y el changelog para cada version. Pero, se ofrecio a que te pase su mail y darte una mano en lo que pueda. Si te interesa, avisame y te lo paso por PM.

---

