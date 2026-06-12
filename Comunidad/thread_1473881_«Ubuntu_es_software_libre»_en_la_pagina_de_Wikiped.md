---
title: "«Ubuntu es software libre» en la pagina de Wikipedia"
date: 2010-05-05
forum: Comunidad
---

### Post by DrKenobi on 2010-05-05
Hola! Estaba leyendo la pagina de Ubuntu en Wikipedia, y me detuve en esto:

> «Ubuntu es software libre»

Aunque las carátulas se imprimen en inglés, a partir de la versión 5.10 se incluyó el texto «Ubuntu is software libre», usando la palabra en español libre, para eliminar la ambigüedad del término free (del inglés free software) que puede significar tanto libre como gratis.

La existencia de software no libre en los repositorios de Ubuntu (concretamente en los componentes restricted y multiverse), además de firmware no libre en el núcleo Linux dio lugar a derivaciones no oficiales y rigurosamente libres de software no libre entre las que destaca gNewSense.

Como respuesta a esto, el 10 de julio de 2007[66] se anunció Gobuntu, una derivación oficial de Ubuntu caracterizada por "una visión ultra-ortodoxa de licenciamiento: sin firmwares, controladores, imágenes realizadas previamente, sonidos, aplicaciones, u otro contenido que no incluya completamente las fuentes y venga con todos los derechos de modificación, remezclado y redistribución."[67]

Sin embargo, después del lanzamiento de Hardy Heron, el desarrollo de Gobuntu quedó descontinuado y se anunció que pasaría a funcionar como una opción de instalación de "sólo software libre" en Ubuntu y no una distribución independiente.[68]

Yo creia que el firmware no libre en el núcleo Linux lo habian sacado/cambiado. ¿Wikipedia esta desactualizado o yo estoy mal informado?

---

### Post by clasificado on 2010-05-05
> **DrKenobi said:**
> Hola! Estaba leyendo la pagina de Ubuntu en Wikipedia, y me detuve en esto:



Yo creia que el firmware no libre en el núcleo Linux lo habian sacado/cambiado. ¿Wikipedia esta desactualizado o yo estoy mal informado?

Desconozco la situación actual, pero la interpretación de "software libre" es diferente en el mundo linux y el mundo gnu, y desde ahi la interpretación no queda clara hacia el resto del sistema operativo sino hasta que alguien se agarra de los pelos.

En el núcleo, la situación sobre los blobs permite a nvidia, ati y demases dejar nucleos cerrados para controlar las placas de video.

Sobre el escritorio, firefox y debian han tenido sus diferencias sobre que el software es libre pero el artwork es "cerrado" (particularmente el nombre Firefox, aunque también el logo).

Y así hay un montón de ejemplos, sobre los cuales ubuntu no está parado muy a la derecha, pero tampoco muy a la izquierda.

---

### Post by alfplayer on 2010-05-05
Me parece válida la explicación de clasificado. Al incluir "binary blobs", Linux no es 100 % software libre, pero lo es casi en su totalidad.

---

### Post by DrKenobi on 2010-05-05
Buenisimo, ahora entiendo mucho mas.

En la wikipedia de Gobuntu lei que ésta se discontinuo y ahora en los CD's de Ubuntu esta la opcion para instalar solo software libre segun la FSF. ¿Como hago? Nunca lo vi...

---

### Post by santiagoward2000 on 2010-05-06
> **DrKenobi said:**
> Buenisimo, ahora entiendo mucho mas.

En la wikipedia de Gobuntu lei que ésta se discontinuo y ahora en los CD's de Ubuntu esta la opcion para instalar solo software libre segun la FSF. ¿Como hago? Nunca lo vi...

Hola!
En la primer pantalla que te aparece cuando inicias la máquina desde el CD (donde podés elegir el idioma, teclado, instalar o probar el sistema) (por lo que ví, en Ubuntu ahora aparece una pantalla con dos íconos, ahí tocás cualquier tecla para que aparezca esta otra pantalla) tocás F6 para ver otras opciones. Es una de ellas.
Saludos!

---

### Post by DrKenobi on 2010-05-06
Gracia santiagoward2000, me parece que esta un poquito escondido jaja

Cuando pueda lo probare pa ver q onda

---

### Post by guillermolisi on 2010-05-06
> **alfplayer said:**
> Me parece válida la explicación de clasificado. Al incluir "binary blobs", Linux no es 100 % software libre, pero lo es casi en su totalidad.
De igual forma que ocurre con Debian y otras distribuciones.

---

### Post by juancarlospaco on 2010-05-07
Depende a cuan bajo nivel vas nada es completamente libre,
no hay codigo fuente del software firmware *(el que va dentro del microcontrolador)* necesario para hacer andar el touchpad de las Lemote,
*but who cares...*

---

### Post by guillermolisi on 2010-05-07
> **juancarlospaco said:**
> Depende a cuan bajo nivel vas nada es completamente libre,
no hay codigo fuente del software firmware *(el que va dentro del microcontrolador)* necesario para hacer andar el touchpad de las Lemote,
*but who cares...*
Perhaps the talibans of SL ? :)

---

### Post by alfplayer on 2010-05-07
Les importa por ejemplo a los que quieren modificar esos programas.

---

### Post by DrKenobi on 2010-05-07
MOMENTO! jaja

Entonces el gNewSense q tanto promociona Richard Stallman es 100% Libre?

---

### Post by alfplayer on 2010-05-07
> **DrKenobi said:**
> MOMENTO! jaja

Entonces el gNewSense q tanto promociona Richard Stallman es 100% Libre?

No se si pueden verificar todo el código, pero la idea es que sea todo software libre.

---

### Post by juancarlospaco on 2010-05-08
> **alfplayer said:**
> Les importa por ejemplo a los que quieren modificar esos programas.

Si hubiera codigo fuente del software que va dentro del microcontrolador de esas cosas,
por ejemplo se podria poner todas las placas WIFI en modo MASTER,
y desafortunadamente solo se puede en aquellas que el software las habilita,
ya me paso mas de una vez, yo queria usar mi AirCrack...

:)

---

### Post by cladelpino on 2010-05-09
Yo ahora estoy usando una distro muy linda que se llama Trisquel. Básicamente usan el kernell libre (el fámoso linux-libre) y arriba los repos de ubuntu pasados por blacklists de software privativo. También modifican firefox para quitar nombre, logos, etc. 

gnewsense me resulto un poco... desactualizada por así decirlo, por ahí es más para meter mano, pero trisquel anda muy bien out of the box, obvio que en mi hardware (una hp dv4 2013la)

Hay mas distros 100% libres (y que no ofrecen en sus repos soft privativo), exploren en la pagina de la FSF si a alguien le interesa. 

Saludos!
Claudio

---

