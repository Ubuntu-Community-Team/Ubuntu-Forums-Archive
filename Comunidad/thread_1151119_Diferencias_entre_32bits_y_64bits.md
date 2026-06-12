---
title: "Diferencias entre 32bits y 64bits"
date: 2009-05-06
forum: Comunidad
---

### Post by dirty fingers on 2009-05-06
lo de los 64bit es una farza comercial. si la plataforma del micro fuera realmente de 64 bit nada de 32 funcionaría. lo que tienen estos famosos micros de 64bit son solo un set de instrucciones que se procesan con 64bit pero la arquitectura de fondo sigue siendo 32bits. en sintesis, ponele sistema de 32 a cualquier micro de 64 que no va a pasar nada malo.

busca en el  bios que seguro que hay para elegir que version de acpi queres usar. con eso deberias resolverlo.

---

### Post by pablo.s on 2009-05-06
> **dirty fingers said:**
> lo que tienen estos famosos micros de 64bit son solo un set de instrucciones que se procesan con 64bit pero la arquitectura de fondo sigue siendo 32bits.

Es justamente al revés.

---

### Post by dirty fingers on 2009-05-06
> **pablo.s said:**
> Es justamente al revés.

me parece que lo dije bien. :-k
[http://es.wikipedia.org/wiki/X86-64](http://es.wikipedia.org/wiki/X86-64)

---

### Post by pablo.s on 2009-05-06
> **dirty fingers said:**
> me parece que lo dije bien.

Si hablás de procesadores de 64 bits en general,
no es asi:

> Mientras las arquitecturas de 64 bits incontestablemente 
hacen más sencillo el trabajar con grandes co[I]njuntos de datos en 
aplicaciones como el [vídeo digital]("http://es.wikipedia.org/wiki/V%C3%ADdeo_digital"), computación científica y grandes 
[bases de datos]("http://es.wikipedia.org/wiki/Base_de_datos"), ha habido un debate considerable sobre si los modos
de compatibilidad[/I] con 32 bits serán más rápidos que los sistemas de 
32 bits del mismo precio para otras tareas. En las arquitecturas [x86-64]("http://es.wikipedia.org/wiki/AMD64")
(AMD64 y EM64T, IA-32e), la mayoría de los sistemas operativos de 32 
bits y aplicaciones pueden ejecutarse sin problemas en el hardware de 
64 bits.

Extractado de la [Wikipedia]("http://es.wikipedia.org/wiki/64_bits"). Supongo que también
leiste ese artículo...

---

### Post by Hei Ku on 2009-05-06
> **dirty fingers said:**
> me parece que lo dije bien. :-k
[http://es.wikipedia.org/wiki/X86-64](http://es.wikipedia.org/wiki/X86-64)

Aparte de copiar el link, lo leiste? 
Justamente dice que todos los registros se agrandaron a 64 bits, y agrega registros adicionales de 128 bits. Pero, siguiendo con la tradicion de cambios anteriores, mantiene compatibilidad con arquitecturas de 32 y 16 bits, que es bastante distinto a decir que agregaron un par de instrucciones y nada mas. 
Prueba de eso es la diferencia de performance cuando haces procesamiento intensivo de video, y similares.

---

### Post by Hei Ku on 2009-05-06
Movido a un thread aparte para no profundizar el off-topic

---

### Post by z37a on 2009-05-06
A ver si me corrigen algo que tengo entendido hace algún tiempo.

AMD trabaja con una arquitectura de 64 bits y emula los 32 bits para correr SO de ese estilo, mientras que Intel(por lo menos al principio) utiliza procesadores de 32 bits con una instrucción para direccionar mayor cantidad de memoria y utilizar así los 64 bits.

---

### Post by Hei Ku on 2009-05-06
No veo donde hace mención a eso. Lo que sí te puedo decir es que en los Pentium 4 de Intel el metodo utilizado es igual al de los AMD64, porque Intel licencio la tecnologia desarrollada por AMD.

---

### Post by z37a on 2009-05-06
> **Hei Ku said:**
> No veo donde hace mención a eso. Lo que sí te puedo decir es que en los Pentium 4 de Intel el metodo utilizado es igual al de los AMD64, porque Intel licencio la tecnologia desarrollada por AMD.

Si eso también lo lei, pero en lo personal no se pro que intel va para atras en 64 bits, no me preguntes, pero en mi laptop anda mejor las versiones de 32 biits(Celeron M520 con EM64T) y en mi desktop anda de 10(AMD Athlon 64 LE1620).

OFF: La ***** es que en mi laptop tengo video intel y este anda de 10!! jajajaja en la desktop tengo video AMD y lo detesto!!!!!

---

### Post by pablo.s on 2009-05-06
Mirá, interpreto que la opinión equivocada
que los AMD y los Intel no sean procesadores
de 64 bits debe venir del historial que tienen
como fabricantes de la gama personal, mas que
otra cosa. Por lo contrario no creo que nadie
discuta que un MIPS o un SPARC sean de 64 bits,
o los procesadores de las Playstation.
Por ende, y haciendo una adaptación del
principio de Hei Ku, si es de Intel se puede
patear...

---

### Post by dirty fingers on 2009-05-06
> **Hei Ku said:**
> Aparte de copiar el link, lo leiste? 
normalmente leo lo que pego ( que sea nuevo en el foro no es indicativo de que deban tratarme como *******)

Para que no me saquen de contexto. aclaro de que se hablaba de los típicos micros amd y intel que se usan en computadoras personales. nada de micros profesionales.

Lo voy a volver a leer por si me equivoque y me retractare en ese caso; pero yo interprete que los micros siguen operando en 32 y que gracias a un bus de 64, un registro de 64 y intrucciones de 64 corren aplicaciones de 64.

---

### Post by Hei Ku on 2009-05-06
No me fijo en la edad, sino en el contenido. 

El articulo menciona justamente los micros personales, y hace la aclaracion que para servers Intel continúa usando Itanium, que no es derivado de la arquitectura de AMD que utilizando en los chips para desktops.

---

### Post by pablo.s on 2009-05-06
Bueno, todo bien, interpretaste mal,
a todos nos pasa (por suerte no seguido)

---

### Post by z37a on 2009-05-07
Para el que menciono a los itanium, si es verdad son 64 hits, pero tampoco son RISC ni CISC como todo micro, si no que es un EPIC, es otra arquitectura completamente distinta, no tiene nada que ver con x86 ni x86_64!!! Fijate que hasta el kernel del SO es distinto(Sea Win, Linux, BSD, etc...)

PD: Los x86 son CISC! los MIPS creo son RISC junto con SPARC

---

### Post by pablo.s on 2009-05-07
> **z37a said:**
> Para el que menciono a los itanium, si es verdad son 64 hits, pero tampoco son RISC ni CISC como todo micro, si no que es un EPIC, es otra arquitectura completamente distinta

Na na na, nadie dijo nada de eso, y no tiene nada
que ver que sea RISC o CISC, eso es muy 90's...

---

### Post by zampes on 2009-05-07
Hola!
Hasta donde tengo entendido, no importa que uses software de 32bits sobre Kernel 64bits... en AMD64. Los procesadores Intel sí tienen algunos problemas y eso por eso que a los dual y quad core les agregan un core 32 bit para que puedan correr las aplicaciones 32 bit en un procesador de 64. Más acerca de esto - Wiki: [http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit](http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit)

 "In x86-64 architecture (AMD64), the majority of the 32-bit operating systems and applications are able to run smoothly on the 64-bit hardware."

"Although most software can run in a 32-bit compatibility mode (also known as an emulation mode, e.g. Microsoft WoW64 Technology for IA64) or run in 32-bit mode natively (on AMD64), it is usually impossible to run a driver (or similar software) in that mode since such a program usually runs in between the OS and the hardware, where direct emulation cannot be employed."

---

### Post by pablo.s on 2009-05-07
> **zampes said:**
> Los procesadores Intel sí tienen algunos problemas y eso por eso que a los dual y quad core les agregan un core 32 bit para que puedan correr las aplicaciones 32 bit en un procesador de 64. Más acerca de esto - Wiki: [http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit](http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit)

En el articulo dice que los Itanium tienen esa
peculiaridad, no dice NADA de los dual y quad
core. [B]Che, lean los articulos de pe a pa antes
de postear![/B] Y más todavia si son en inglés.
Asimismo, los Itanium ejecutan versiones full
de software 64 bits, en su mayoria servidores o
software de tareas cientificas.

---

### Post by juancarlospaco on 2009-05-07
La diferencia es 32bit mas...
*cuack!*

---

### Post by Hei Ku on 2009-05-07
> **juancarlospaco said:**
> La diferencia es 32bit mas...
*cuack!*

Hmmmm, algo para aportar? O interrumpiste una conversación técnica interesante sólo porque creías que no podíamos vivir sin tu presencia?

---

### Post by z37a on 2009-05-07
> **zampes said:**
> Hola!
Hasta donde tengo entendido, no importa que uses software de 32bits sobre Kernel 64bits... en AMD64. Los procesadores Intel sí tienen algunos problemas y eso por eso que a los dual y quad core les agregan un core 32 bit para que puedan correr las aplicaciones 32 bit en un procesador de 64. Más acerca de esto - Wiki: [http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit](http://en.wikipedia.org/wiki/64-bit#32_vs_64_bit)

 "In x86-64 architecture (AMD64), the majority of the 32-bit operating systems and applications are able to run smoothly on the 64-bit hardware."

"Although most software can run in a 32-bit compatibility mode (also known as an emulation mode, e.g. Microsoft WoW64 Technology for IA64) or run in 32-bit mode natively (on AMD64), it is usually impossible to run a driver (or similar software) in that mode since such a program usually runs in between the OS and the hardware, where direct emulation cannot be employed."


Aca mensionan Itanium, IA64 no es EM64T!!!!!!!

Como dije antes Itanium es IA64, 64 bits puros y nativos y con arquitectura del modelo EPIC

Los EM64T(o AMD64) son los intel x86 de 64 bits, que es del modelo CISC y es otra arquitectura completamente distinta!!!!!!!

Es mas creo que no hay Ubuntu desktop nativo de IA64!! No se tampoco si hay server(pero deberia, ya que muchos servers usan IA64, pero desktop, a menos que seas millonario y estes al dope o un fisico con mucho laburo!!!)

---

### Post by pablo.s on 2009-05-07
> **z37a said:**
> Es mas creo que no hay Ubuntu desktop nativo de IA64!! No se tampoco si hay server(pero deberia, ya que muchos servers usan IA64

Mmm no, no hay. El sector servidores
empresariales está copadisimo por las
empresas tradicionales. Creo que en
Canonical apuntan a servidores de medianos
a chicos, donde hay mas profesional
joven. A decir verdad tendría que
informarme bien sobre la estrategia
que armaron para ubicar Ubuntu Server.

---

### Post by pablo.s on 2009-05-07
Lo que estoy leyendo dice que
basicamente apuntan a tres
tecnologias muy en boga:
*LAMP
*Virtualización
*La nube

Bastante bien armado, si tenemos
en cuenta toda la movida actual de
virtualizar sistemas y LAMP...

---

### Post by z37a on 2009-05-08
> **pablo.s said:**
> Mmm no, no hay. El sector servidores
empresariales está copadisimo por las
empresas tradicionales. Creo que en
Canonical apuntan a servidores de medianos
a chicos, donde hay mas profesional
joven. A decir verdad tendría que
informarme bien sobre la estrategia
que armaron para ubicar Ubuntu Server.

Pero si hay para Sparc!!!(Arquitectura RISC de SUN)

Creo que canonical debería apuntar también a IA64 en sus próximos lanzamientos, por lo menos en mi visión hay mas server Itanium que Sparc

---

### Post by guillermolisi on 2009-05-08
> **z37a said:**
> Pero si hay para Sparc!!!(Arquitectura RISC de SUN)

Creo que canonical debería apuntar también a IA64 en sus próximos lanzamientos, por lo menos en mi visión hay mas server Itanium que Sparc
Mmmmm ... no puedo ni afirmar ni negar eso porque para hacerlo fundamentadamente deberia tomarme el trabajo de obtener informacion seria, peeeero .... Oracle compro Sun entre otras cosas porque la base instalada mas grande en el mundo de DBMS Oracle corre en servidores SUN Sparc y coincide en que esos servers son muy utilizados por ISPs.

Todo esto segun las notas que se han publicado al respecto de la operacion Oracle-Sun.

---

### Post by Hei Ku on 2009-05-08
> **guillermolisi said:**
> Mmmmm ... no puedo ni afirmar ni negar eso porque para hacerlo fundamentadamente deberia tomarme el trabajo de obtener informacion seria, peeeero .... Oracle compro Sun entre otras cosas porque la base instalada mas grande en el mundo de DBMS Oracle corre en servidores SUN Sparc y coincide en que esos servers son muy utilizados por ISPs.

Todo esto segun las notas que se han publicado al respecto de la operacion Oracle-Sun.

En instalaciones grandes, los Sun, HP-UX y AIX son los que tienen las aplicaciones, y los Intel sirven para compartir archivos e impresoras.

Definitivamente, Oracle no compró Sun por la licencia de Openoffice, Glassfish o Java.

---

### Post by pablo.s on 2009-05-08
> **Hei Ku said:**
> Definitivamente, Oracle no compró Sun por la licencia de Openoffice, Glassfish o Java.

Y, saber exactamente por cual de todos
los productos compraron a Sun, es una
loteria. Lo que se sabe es que hicieron
el negocio del siglo. Creo que lo más
importante que tiene Sun es el hardware
y Java/OpenSolaris. MySQL no creo que
le interese a Oracle, pero Open Office
lo veo como un punto de apoyo para
ingresar al escritorio.

---

### Post by pablo.s on 2009-05-08
> **z37a said:**
> Creo que canonical debería apuntar también a IA64 en sus próximos lanzamientos

Apuntan a lo que se está discutiendo
acá: Core 2 Duo, Core 2 Quad, Athlon,
Phenom, todos los procesadores que
podés comprar facil y armar rapido y
barato. Soluciones para chicos y medianos.

---

### Post by WanderingKnight on 2009-05-09
> 
En instalaciones grandes, los Sun, HP-UX y AIX son los que tienen las aplicaciones, y los Intel sirven para compartir archivos e impresoras.

Definitivamente, Oracle no compró Sun por la licencia de Openoffice, Glassfish o Java.

Laburo con Oracle todos los días y ellos mismos te dicen que para desplegar su base de datos recomiendan SPARC + Solaris. Nunca tuve bien en claro los fundamentos técnicos para esta recomendación, pero a partir de ahora va a ser más que obvio.

Definitivamente lo hicieron por SPARC. Y para mostrarle el dedo del medio a IBM ;)

---

### Post by dirty fingers on 2009-05-13
ya esta, ya me informe. metí la pata asquerosamente con mi descripción de los micros de 64bit.

---

### Post by Hei Ku on 2009-05-13
> **dirty fingers said:**
> ya esta, ya me informe. metí la pata asquerosamente con mi descripción de los micros de 64bit.

Y ahora lo decis, despues de la bataola que se armó? :lolflag:

Estuvo buena la charla, manteniendonos "casi" civilizados. :D

---

