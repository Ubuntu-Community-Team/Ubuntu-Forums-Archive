---
title: "Reinstalación de Windows imposible!!!"
date: 2008-10-09
forum: Comunidad
---

### Post by erdosain9 on 2008-10-09
Hola a todos.  Les comento que tengo dos discos.  en el primario tengo ubuntu... y tenía un windows xp recortado en el segundo.  Pues bien, en mi largo camino a eliminar completamente el windows xp de la máquina decidí borrar todo lo que había en el disco secundario.

Ahora bien.  La intención era instalar un windows xp que es sólo para los juegos.  Llamesé "Windows XP - Extreme Gaming Edition" más recortado imposible... se supone que sólo es para los juegos y no puede correr nada más (excepto la red... para juegos!).

Pues bien.  Me encuentro sacando el primer disco para que ni se le ocurra al windows tocar nada y poniendo al esclavo como primario.  resulta que al momento del particionado, cuando va a formatear me dice:

"El programa de instalación no ha podido formatear la partición.  Es posible que el disco esté dañado... etc, etc".

Chamuyo porque funciona muy bien.  
¿Qué puede ser??? Pienso que el Grub habrá metido manos en el asunto... ¿puede ser?  ¿qué hago?

Saludos.

---

### Post by erdosain9 on 2008-10-09
La cosa empeoró.  Luego del intento fallido con la instalación volví a entrar en ubuntu.... el disco rígido figuraba, pensé que estaba todo bien.  Intenté entrar pero me dijo algo de que windows estaba cargado o algo así.  Entonces apagué, volví a desconectar el disco rígido donde está ubuntu y puse primario donde quería instalar windows... todo volvió a comenzar... creo que una parte se instaló... pero mal... volví a intentarlo y esta vez, si bien en el booteo de la máquina aparece el discorígido y windows lo reconoce... dice que no tiene partición, cuando voy a particionarlo no lo puede particionar... intenté el ntfs lento y luego de un montón de tiempo me dijo "no puedo particionarlo"... volví a ubuntu y ubuntu no lo pone... no lo reconoce supongo, no sabe que existe.

Qué hago????????????????????????????????????? ayuda!!!!!!!!!

---

### Post by leo_rockway on 2008-10-09
Ubuntu funciona, GRUB funciona, el disco rígido funciona... Windows no funciona.

Este es el foro de Ubuntu, no sé si es el lugar más indicado para recibir ayuda con la instalación de Windows.

---

### Post by WanderingKnight on 2008-10-09
Windows hace cosas muy raras cuando hay más de 4 particiones en un mismo disco. Yo me peleé mucho con el instalador la última vez que tuve que instalar en un sistema que ya corría Ubuntu. Honestamente fue hace tanto que no recuerdo qué hice, así que disculpas.

De todas formas, concuerdo con Leo, no sé si vamos a poder ayudarte demasiado al respecto.

---

### Post by erdosain9 on 2008-10-09
Bueno, entiendo lo que decís.  Pero este windows que intento instalar como digo no corre nada... (bueno, claro, excepto los juegos):

[http://www.taringa.net/posts/downloads/1570919/Windows-XP-Extreme-Gaming-Edition-(SP3+SATA-Drivers).html](http://www.taringa.net/posts/downloads/1570919/Windows-XP-Extreme-Gaming-Edition-(SP3+SATA-Drivers).html)

y pido ayuda porque se jodió algo o no sé cómo instalarlo y tal vez ustedes si.

También si bien es un windows... creo que hay varios post que tratan el tema de la red entre ubuntu y windows y si te fijas en otro thread que hice estuve preguntando cómo lograr la red ubuntu-ubuntu.  Mi intención es eliminar windows pero por ahora no quiero abandonar sus juegos y mandando con el wine me va lento, mi máquina es vieja (no tanto pa' mi).

Entiendo que no es tan descolgado lo que digo... hay muuuuuchos thread ubuntu - windows... y encima yo sólo digo que voy a instalar un windows que funca tan sólo para juegos...

Pero bueno.  La cosa es que ya logré que ubuntu reconozca el disco rígido; metí el cd de instalación de ubuntu e hice como una instalación... logró formatear y entonces ya me aparece en el ubuntu principal.  

Pero el hijoeput de windows cuando lo quiero instalar dice que la partición no es compatible.  Entonces probé con un gparted que trae un puppy linux y lo particioné como ntfs... pero nuevamente cuando voy a instalar el windows me dice:

"este disco no contiene una partición compatible con windows xp"... esto es raro porque la partición que yo hice es ntfs y así aparece en la pantalla azul de instalación.  Y por supuesto si le digo que elimine la partición y la cree él pues me repite lo mismo...  Creo que tendrá que ver con el grub y el MBR porque al decirme eso que cité aparecen por ahí eso del MBR.

Bueno, esperando ayuda.
Saludos y gracias
   Erdosain9

P.D.: si me decís algo que funcione similar a este windows recortado que te digo y que no me relantice la máquina no lo instalo,pero seriamente los juegos me van lentín.

P.d.: no había leído la segunda respuesta... son dos discos rígidos.  En uno tengo ubuntu... y en el otro por ahora... nada.

---

### Post by WanderingKnight on 2008-10-09
Podrías postear ENTERA la tabla de particiones de los discos? Se me hace bastante complicado entender qué particiones tenés...

---

### Post by leo_rockway on 2008-10-09
Es que yo no te lo digo de mala onda.
Las preguntas sobre redes Ubuntu-Windows van a tener respuestas porque son cosas que los usuarios de GNU/Linux saben hacer.

Tu pregunta de "¿Cómo hago para poder instalar este Windows?" no va a tener muchas respuestas simplemente porque acá hay pocos usuarios de Windows.

Mi recomendación es que hagas la pregunta en un foro de Windows simplemente para que no te quedes colgado esperando una respuesta que acá quizás nunca llegue.

---

### Post by erdosain9 on 2008-10-09
Bueno, bueno, está bien... veré en un foro windows... pero si alguien sabe me tira una mano???

con respecto a lo de las particiones... soy muy nuevo en linux si me decís cómo hacerlo lo posteo.  

Gracias nuevamente.

P.D.:ustedes saben ;-)

---

### Post by leo_rockway on 2008-10-09
> **erdosain9 said:**
> con respecto a lo de las particiones... soy muy nuevo en linux si me decís cómo hacerlo lo posteo.  


```
sudo fdisk -l
```

---

### Post by erdosain9 on 2008-10-09
gracias....

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x48184817

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extendida
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disco /dev/sdb: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf170f170

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

---

### Post by erdosain9 on 2008-10-10
Una pregunta:

Se supone entonces que el disco rígido que tengo me ha quedado inutilizado, a menos que lo use para UBUNTU... pues poniendo este que les cuento como primario, maestro, único disco rígido de una computadora... sólo le puedo instalar un linux... pues el windows me da el error que comenté.!!!

Pues que mala leche...

No por Ubuntu, que sí... bueno, hice todo un despelote para que lo pusieran en mi casa mis viejos... no sólo yo... pero bueno, odio estar obligado.

veré la forma.

Saludos y gracias

Erdosain9

---

### Post by faktorqm on 2008-10-10
Proba de borrarle la particion al disco, y dejarlo asi, no generar ninguna nueva. ¿Por que ponés el disco como primario y despues lo pones secundario? No se que tan recomendable es hacer eso. 
Dejá enchufados todos los discos como van a quedar en el futuro, y de ultima deshabilitalo de la bios, pero que windows se instale en el segundo disco. Cuando arrancas el instalador, creas una nueva particion, la formateas, y ahi te fijas que pasa. Salu2!

---

