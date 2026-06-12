---
title: "i'm new and i don't understand how installing a program"
date: 2009-03-25
forum: General Help
---

### Post by nsblenin on 2009-03-25
nil@Nailo:~$ cd Escritorio/foobillard-3.0a/

nil@Nailo:~/Escritorio/foobillard-3.0a$ ls
aclocal.m4  config.status  data                  foobillard-SDL.spec     INSTALL      Makefile.in    README
AUTHORS     configure      depcomp               foobillard-SDL.spec.in  install-sh   missing        README.FONTS
ChangeLog   configure.in   foobillard.6          foobillard.spec         Makefile     mkinstalldirs  src
config.log  COPYING        foobillardrc.example  foobillard.spec.in      Makefile.am  NEWS           TODO
nil@Nailo:~/Escritorio/foobillard-3.0a$ configure
bash: configure: orden no encontrada
nil@Nailo:~/Escritorio/foobillard-3.0a$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c

a lot of lines xd

config.status: creating data/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands

nil@Nailo:~/Escritorio/foobillard-3.0a$ make
Making all in src
make[1]: se ingresa al directorio `/home/nil/Escritorio/foobillard-3.0a/src'
make  all-am
make[2]: se ingresa al directorio `/home/nil/Escritorio/foobillard-3.0a/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I. -DNDEBUG -DDATA_DIRECTORY='"/usr/local/share/foobillard/"'   -Wall `freetype-config --cflags` `sdl-config --cflags` -DUSE_SDL  -DUSE_SOUND  -g -O2 -MT billard3d.o -MD -MP 

a lot of lines xd

billard3d.c:4942: error: ‘GL_LEQUAL’ no se declaró aquí (primer uso en esta función)
billard3d.c:4950: aviso: declaración implícita de la función ‘SetMode’
billard3d.c: En la función ‘main’:
billard3d.c:5043: aviso: declaración implícita de la función ‘glGetIntegerv’
billard3d.c:5043: error: ‘GL_AUX_BUFFERS’ no se declaró aquí (primer uso en esta función)
billard3d.c:5046: error: ‘GL_LIGHTING’ no se declaró aquí (primer uso en esta función)
billard3d.c:5098: aviso: se descarta el valor de devolución de ‘fread’, se declaró con el atributo warn_unused_result
make[2]: *** [billard3d.o] Error 1
make[2]: se sale del directorio `/home/nil/Escritorio/foobillard-3.0a/src'
make[1]: *** [all] Error 2
make[1]: se sale del directorio `/home/nil/Escritorio/foobillard-3.0a/src'
make: *** [all-recursive] Error 1

nil@Nailo:~/Escritorio/foobillard-3.0a$ 


What should I do. There is a file called Install that tells me that i have to write <configure>, <make>, <make install>. But i don't understand why.
Thanks

---

### Post by nsblenin on 2009-03-25
sorry the firsts lines are:


nil@Nailo:~/Escritorio/foobillard-3.0a$ ls
aclocal.m4  config.status  data                  foobillard-SDL.spec     INSTALL      Makefile.in    README
AUTHORS     configure      depcomp               foobillard-SDL.spec.in  install-sh   missing        README.FONTS
ChangeLog   configure.in   foobillard.6          foobillard.spec         Makefile     mkinstalldirs  src
config.log  COPYING        foobillardrc.example  foobillard.spec.in      Makefile.am  NEWS           TODO
nil@Nailo:~/Escritorio/foobillard-3.0a$ configure
bash: configure: orden no encontrada
nil@Nailo:~/Escritorio/foobillard-3.0a$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc

---

### Post by Twitch6000 on 2009-03-25
Well first what program are you trying to install?

There are many other ways to install programs and alot easier ways.

Some ways being as easy as double click and install.

You should only need to compile as a last resort.

---

### Post by damis648 on 2009-03-25
Applications>Add/Remove
Click Show>All Available Applications, and then search for foobillard.:popcorn:

---

### Post by oldos2er on 2009-03-25
[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

[https://help.ubuntu.com/community/Applications](https://help.ubuntu.com/community/Applications)

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by mb_webguy on 2009-03-25
Foobilliard is in the Ubuntu repositories, as is the case with most applications you'd ever want to install.  You can install it using Applications->Add/Remove, System->Administration->Synaptic Package Manager, with the command "sudo apt-get install foobilliard" in the terminal, or by simply clicking [this link]("apt:foobilliard").

---

