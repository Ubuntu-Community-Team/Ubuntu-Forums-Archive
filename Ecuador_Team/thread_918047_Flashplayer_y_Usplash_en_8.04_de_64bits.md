---
title: "Flashplayer y Usplash en 8.04 de 64bits"
date: 2008-09-12
forum: Ecuador Team
---

### Post by carlitossanchez on 2008-09-12
Que tal amigos ubunteros, en la version 7.10 no he tenido problemas en instalar flashplayer de 32 bits pero con el nuevo ubuntu 8.04 he tratado de las 3 formas posibles que he encontrado en internet pero no e logrado hacer funcionar, lo mismo ocurre con los usplash, con el administrador de arranque no se me cargan los usplash.

Alguien sabe como arreglar o hacer funcionar estos 2 problemitas que tengo???

Gracias la Atencion

---

### Post by hubuntu on 2008-09-13
Adhiere [ubuntu-restricted-extras]("http://packages.ubuntu.com/hardy/ubuntu-restricted-extras") (como describió [Alex]("https://lists.ubuntu.com/archives/ubuntu-ec/2008-September/000502.html"))

Otra opción, si necesitas más oporte multimedia, es usar [medibuntu]("http://medibuntu.org/"). Soporta arquitecturas 32, 64 bit o PowerPC. Aparte obviamente soporta Java tb en las mismas.

Saludos,

R.

---

### Post by carlitossanchez on 2008-09-25
Muchas gracias Ruben, ya encontre el problema, y lamentablemente a sido la resolucion del video por parte del problema del Usplash, hay que revisar siempre antes de modificar el archivo usplash.conf

sudo gedit /etc/usplash.conf

ahi defines la resolucion de video en dependencia de tu maquina.

Con relacion a lo de Flashplayer pues le volvi a instalar los ubuntu-restricted-extras y por lo menos cuando entro al youtube ya no me dice que no tengo instalado el flashplayer, es decir ya le reconoce al plugin pero cuando selecciono algun video se queda cargando y no pasa de ahi.

---

