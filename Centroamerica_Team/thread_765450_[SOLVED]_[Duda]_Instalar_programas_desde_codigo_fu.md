---
title: "[SOLVED] [Duda] Instalar programas desde codigo fuente"
date: 2008-04-24
forum: Centroamerica Team
---

### Post by meldon12 on 2008-04-24
hola amigos, me gustaria saber como puedo instalar los programas que vienen comprimidos en archivos con extension tar.bz o tar.bz2 (algo asi) y que al descomprimirlos salen un monton de archivos.

He leido manuales en todos lados, y nunca explican poniendose en la piel de un novato, nisiquiera en la **wiki Guia Ubuntu** lo explican bn.

Espero que alguien pueda ayudarme.

Saludos a todos.

meldon12

---

### Post by greer on 2008-04-24
eso depende de cada programa, en el mismo paquete debe salir como hacerlo.

por lo general es asi:

primero y antes que todo te instalas unos programas para hecerlo

# sudo aptitude install build-essential

despues extraes y entras en el directorio y por consola pones

# sudo ./configure

despues

# sudo make

y

# sudo make install

listo... pero deberias leerte el readme! del programa a compilar, por que pueden haber otros pasos o pueden haber otros requerimientos para compilar, osea que necesites hacer otras cosas o instalar otros programas para poder compilar, eso depende. pero por lo general es asi como te dije.

---

### Post by meldon12 on 2008-04-24
> **greer said:**
> pero deberias leerte el readme! del programa a compilar, por que pueden haber otros pasos o pueden haber otros requerimientos para compilar, osea que necesites hacer otras cosas o instalar otros programas para poder compilar, eso depende. pero por lo general es asi como te dije.

si, siempre lo leo, pero nunca he podido, muchas gracias den uevo greer, lo ntentare aver como me va.

saludos

---

### Post by eivar on 2008-04-24
Saludos meldon12, una de las cosas me más me gusta de los programas que te dan el código fuente es que funciona igual la instalación en el GNU/Linux que sea.


[LIST]
[*] Ahora bien tienes que descomprimir el archivo, preferiblemente en una carpeta para el sólo y te evitas problemas.
[/LIST]


[LIST]
[*] Estos paquetes generalmente contienen un archivo README, léelo  para encontrar cualquier nota que el autor dejara para ti, a veces encuentras también un archivo INSTALL ese te puede dar más detalles de cómo instalar. En estos dos archivos por algún lado o en el lugar donde bajaste el programa debe estar la lista de las librerías que necesita para funcionar, verifica que están todas instaladas y que tienes instaldo también el compilador necesario, por ejemplo algunas veces necesitas instalar qmake u otro.
[/LIST]

[LIST]
[*]Algunos programas vienen con un archivo ejecutable llamado *configure*, si en las instrucciones de algunos de los dos archivos README o INSTALL te piden ejecutar este archivo, en una consola vas hasta la carpeta donde descomprimiste el paquete tar.gz y ejecutas el archivo con el comando:
[/LIST]
[INDENT]> **./configure** (escribe ./ y presiona tab para que veas las opciones de autocompletado)Debes mirar cuidadosamente la salida del comando anterior pues te informará del progreso, si todo está bien, si algo no está pero no es necesario y si algo sale mal te sirve para verificar, es probable que mande errores en algunas librerías, revisa que estén instaladas las necesarias para compilar [SIZE=1]*1[/SIZE]. Una vez todo se ejecute bien podemos continuar.
[/INDENT]
[LIST]
[*]Ahora debes ejecutar el comando **make **[SIZE=1]*2[/SIZE] en la consola estando en el folder donde descomprimiste el tar.gz, no es necesario ser admin porque los ejecutables resultantes de compilar se escriben dentro de la misma carpeta donde estas compilando.
[/LIST]

[LIST]
[*]Por ultimo el comando make install instalará el programa en el sistema, para esto si necesitas permisos de administrador pues tocaras carpetas como /usr o /share dependiendo del programa así que en la misma consola anterior escribes:
[/LIST]
[INDENT]> **sudo make install**[/INDENT]
[LIST]
[*]Ahora es cuestión de probar que todo funciona bien... :lolflag:
[/LIST]
[SIZE=1]*1[/SIZE] Las librerías vienen en dos versiones, la binaria y la de compilación, si se llama libaux tendrás dos paquetes libaux y libaux-dev y algunas veces un paquete que configura variables necesarias para que el compilador, que ahora no recuerdo como se llama pero, si en la descripción dice algo de que es para compilar mejor instalarlo :popcorn:.
[SIZE=1]*2[/SIZE] Aquí puede que sea necesario ejecutar otro compilador distinto de make pero eso debe estar detallado o en el archivo README o el archivo INSTALL.

¡Suerte!
Eivar.

---

### Post by meldon12 on 2008-04-24
hice lo que me han dicho y miren lo que me sale:

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.

nose que sera.

saludos

---

### Post by eivar on 2008-04-25
Una pregunta ¿tienes instalado gcc?
Mira ese config.log que te dice la salida y sino puedes entender cual es el problema postealo aquí para revisarlo. 

Suerte

---

### Post by greer on 2008-04-25
como dije antes, primero que todo...

# sudo aptitude install **build-essential**

---

### Post by mayeco on 2008-04-29
meldon12 instalando el paquete de **build-essential** instalas todo lo necesario para compilar e instalar paquetes desde código fuente o tarballs (.tar.gz) 

un comando para configurar el paquete:

**./configure**

luego un paquete para compilarlo:

**make**

y por ultimo un comando para instalarlo:

**sudo make install**

Saludos,

---

### Post by meldon12 on 2008-05-02
gracias mayeco, vere si puedo lograrlo, pero tengo que instalar ubuntu de nuevo porque formatie la partivion de windows y se fue al ****** mi ubuntu :(.

saludos

---

