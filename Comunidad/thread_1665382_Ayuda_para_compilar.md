---
title: "Ayuda para compilar"
date: 2011-01-12
forum: Comunidad
---

### Post by asterix77 on 2011-01-12
Como esto es un post de ayuda (o pretende serlo) a la comunidad, creo que debiera venir aquí, o de lo contrario pido disculpas.

Como usuario de ubuntu, me he encontrado en varias oportunidades con post como este [http://ubuntuforums.org/showthread.php?t=1663381](http://ubuntuforums.org/showthread.php?t=1663381). 

La verdad es que por diversos motivos, a veces se nos hace necesario instalar software que no están en los repositorios, y que peor aún, no están en paquetes deb. La única opción entonces es descargar el código fuente para compilarlo. No es algo fácil para usuarios normales, y creo que debería haber alguna guía, un post o algo donde debiera detallarse lo necesario para poder hacer algo, o al menos guiar en el proceso.

Buscando en la red he encontrado algunas directrices para ayudar en esta materia. Sería interesante poder seguir completando este post para de esta forma ayudar a los que quieran usar este método.

Vamos al grano.

Compilar es un proceso por el cual se traducen programas en código  fuente a programas en código objeto. El programa que realiza esta  traducción se llama compilador.


 Pues bien, a muchísima gente, les pasa que a la hora de instalar  programas que vienen comprimidos en .tar.gz u otras extensiones, no  pueden compilar, ¿Por qué? Les falta el compilador..


 Ubuntu no trae por defecto uno de estos, así que instalarlo es sencillo, ya que viene en repositorios:


 $ sudo apt-get install build-essential
 Esto instala los paquetes necesarios para poder compilar, que son los siguientes:
 
[LIST]
[*]g++
[*]g++-3.3
[*]gcc
[*]gcc-3.3
[*]libstdc++5-3.3-dev
[/LIST]
 Así que si alguna vez a pasado, ya sabes por qué y su solución..
 Vale, esto ha quedado claro, una vez tenemos el compilador, qué  hacemos? Imaginemos que queremos instalar un archivo .tar.gz, que son  los más comunes a la hora de compilar, el proceso es sencillo, lo  primero será descomprimir el archivo:


 $ tar -xzvf *nombre_archivo*.tar.gz
 Después, te descomprimirá una carpeta, solo tenemos que ir hasta ella:


 $ cd *directorio_carpeta*
 Una vez en la misma, configuramos:


 $ ./configure
 En el próximo comando esta la complicación, donde hay que compilar,  si te da errores, fíjate bien qué paquete falta. Le echas un vistazo a  Synaptic y lo instalas. Si aún así te sigue dando el mismo error, tienes  que instalar el mismo paquete pero que tiene “**-dev**” en su nombre, son las cabeceras de la biblioteca y el desarrollo.. El comando del que hablo es:


 $ make
 Una vez compilado, solo queda instalar:


 $ sudo make install
 Borras la carpeta, y listo.

**Algunas reglas básicas para la compilación de código fuente:**
[INDENT]-  Siempre lee el README y el INSTALL adjunto con el codigo fuente. Cuando  compilas manualmente no se resuelven las dependencias, asi que  asegurate de tener los paquetes necesarios para la compilación.
-  Evita usar rutas con espacios en blanco, reemplazalas por '_' si fuera  necesario. La razón es que algunas veces el compilador se marea con los  espacios en blanco y da errores que evitan la compilación.
- Algunas  veces es mucho mejor bajarse el código fuente que usar los paquetes pre-compilados. La compilación in-situ asegura el mayor rendimiento en tu  sistema.
- Y sobre todo, LEER e INVESTIGAR es lo mas importante.

Saludos
[/INDENT]

---

