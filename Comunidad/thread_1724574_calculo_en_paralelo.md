---
title: "calculo en paralelo"
date: 2011-04-08
forum: Comunidad
---

### Post by thegreeneyes on 2011-04-08
Hola. Para poder aprovechar los cores de mi pc, instalé openmpi después de haber instalado los compiladores de gfortran y g++ (gcc ya estaba instalado). Ahora quiero ver si puedo instalar algún administrador de colas como para poder submitir programas para que corran de acuerdo a la disponibilidad de los cores, pero no me parece haber encontrado nada muy "facil" para esa tarea, hay algún código abierto que sea preferible y fácil de instalar para UBUNTU?, encontré una guía de instalación para kerrighed, y también pareciera que globus-gram-job-manager puede ser adecuado, pero ambos me resultaron complicados en sus guías, y me parece que están más destinados a administrar clusters de computadoras que computadoras individuales con varios cores. Alguna sugerencia?

Gracias

---

### Post by alfplayer on 2011-04-08
Hola.

Submitir no es una palabra ;)

Con respecto a tu pregunta, creo que sería conveniente que especifiques cuál es el objetivo, p.e. si es para, como mencionás, una computadora o un cluster de computadoras. Hay varias formas de distribuir el procesamiento. Para el caso de una única computadora se puede lograr con varios procesos o varios hilos ejecutándose en simultáneo. Un software como Open MPI entiendo que es útil por ejemplo en un cluster, en un entorno, como dice la página de Wikipedia de MPI, en el que el costo de acceso a memoria no local es alto.

---

### Post by thegreeneyes on 2011-04-11
sorry por el spanglish!!! jajaja

Mi caso es una PC con 8 cores (carozos? núcleao?). Mediante el uso de openmpi puedo compilar un código fuente por ejemplo usando gfortran puedo ingresar el comando 

mpif90 programa.f -o programa.exe

y producir un ejecutable.

luego mediante el comando 

mpirun -np 4 programa.exe

hago que el programa sobre cuatro cores simultáneamente, de modo que se intercambian información (de la manera en que lo diseñé en el archivo programa.f

yo por ejemplo puedo ingresar desde dos ventanas de comandos diferentes y parado en diferentes directorio el mpirun mencionado y dejar la pc corriendo durante la noche ocupando los 8 cores a full.

Mi problema es que desde programa.f quiero submitor, ocasionalmente, otro código que postprocese la salida de programa.f pero mediante llamadas a 

call system('mpirun -np 2 postproc.exe') 

el sistema me responde con error. He probado que tampoco es linda la respuesta que obtengo mediante un 

call system('ls > qqq.dat')

aunque el archivo qqq.dat es correcto.

En un server donde está todo funcionando bien el tema se soluciona con 

bsub < programa.csh

que a su vez tiene un 

call system('bsub < postproc.csh')

donde los csh definen el tiempo de cpu reservado en el server, y el número de cores que empleara y la cola en que se pone cada job. El server ejecuta esos csh cuando tiene los cpus disponibles y ya los usuarios que submitieron (?) jobs antes que uno han sido ejecutados.



En efecto, puede haber otros métodos de paralización más eficientes para mi caso, pero no los conozco, y supongo que modificar y validar el código original puede ser caro en tiempo. De todos modos es una posibilidad que consideraré cuando me familiarice con alguno.

Gracias

Victor

---

### Post by alfplayer on 2011-04-11
Parece que hay dos caminos: entender por qué falla la llamada a postproc en Fortran o instalar un LSF para hacerlo con tareas.

---

### Post by mama21mama on 2011-04-11
Estaba pensando que no hay aplicaciones para linux que funcionen en los [cuda]("http://es.wikipedia.org/wiki/CUDA").

---

### Post by alfplayer on 2011-04-12
Hay apps de GNU/Linux para CUDA, y para OpenCL también.

---

### Post by mama21mama on 2011-04-12
seguramente claro que hay, pero no las que deberian tener soporte de cuda.
ejemplo: Cinellera, devede y muchos mas.

me contaron los colegas que editan video en windows con el poder de los cores normales y los cuda. me cuentan marravilla de poder que tiene y lo rapidisimo que todo fluye.

hasta los antivirus corren en cuda. hay un antivirus conocido ruso que anda en cuda. 

o sea en fin, para que tener 64bit, para que tener cores de sobra si no hay todavía soporte.

---

### Post by alfplayer on 2011-04-12
CUDA es solo para Nvidia. OpenCL parece ser la solución más libre.

---

