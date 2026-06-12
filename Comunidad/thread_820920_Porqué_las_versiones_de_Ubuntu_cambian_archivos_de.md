---
title: "Porqué las versiones de Ubuntu cambian archivos de lugar y nombre???"
date: 2008-06-06
forum: Comunidad
---

### Post by matutetandil on 2008-06-06
La verdad que esto me esta llamando mucho la atención y no le encuentro razón alguna...
Me gustaría que me dijeran si es que alguien sabe el porqué de estas cosas:

El direcrio $HOME/Desktop no existe más ahora se llama $HOME/Escritorio (desde ubuntu 7.10)

El directorio de la papelera $HOME/.Trash se movio a $HOME/.local/share/Trash (ubuntu 8.04)

en Ubuntu 8.04 no existe el archivo /etc/resolv.conf en el cual se realizan las configuraciones de los DNS.

Si alguien sabe la respuesta a estos cambios y a otros que seguramente habrá pero todavía no me encontré con ellos que me los diga, porque la verdad que en vez de mejorar las cosas a veces las complican más, cada vez que instalas una version nueva, tenes que rastrear a donde estan los archivos de antes y fijarte si ahora no se llama de otra manera...
Yo se que muchos de esas cosas pasa entre distribuciones distintas, por ejemplo slakware con debian... pero en Ubuntu que estando basada en Debian no respete por lo menos esas cosas... y peor que no las respete en cambios de version...

La verdad que me llama mucho la antención, soy usuario de ubuntu y de debian hace ya bastante tiempo y siempre busque una respuesta a esto y nadie me la pudo dar... espero que alguien de la comunidad me la pueda responder...

Saludos!!!!

---

### Post by ksennin on 2008-06-06
Quieres que te copie tu post a ingles en este mismo thread para ver si hay respuesta de nuestros compañeros de habla inglesa?

---

### Post by matutetandil on 2008-06-06
> **ksennin said:**
> Quieres que te copie tu post a ingles en este mismo thread para ver si hay respuesta de nuestros compañeros de habla inglesa?
dale... si te copa no hay drama...

---

### Post by faktorqm on 2008-06-06
No podés por que en este foro sólo se habla Español, el idioma de Argentina, país al cual pertenece este sub-foro.

Lo del trash y la papelera, para mi carece de importancia. En cambio lo del resolv.conf me parece GRAVISIMO. Estas seguro que no esta mas? Cuando llego a casa me fijo...

---

### Post by Mister X on 2008-06-06
Las carpetas Escritorio, Documentos, Musica, Imagenes y Video, dependen del lenguaje de c/usuario, si cambias tu perfil de usuario para idioma ingles, cuando inicias sesion te va a preguntar si queres cambiar de nombre esas carpetas, eso lo maneja el programa (o script, no sé) xdg-user-dirs que se ejecuta al inicio de sesion.

La carpeta .Trash no tiene importancia porque el funcionamiento es transparente al usuario.

el tema del resolv.conf si es importante, es una lastima que se vaya perdiendo cierta compatibilidad en la configuracion con Debian.

---

### Post by Kantier on 2008-06-06
erm... yo tengo un fresh install de 8.04 (en inglés) y tengo el **/etc/resolv.conf** O.o

también tengo un directorio **/etc/reslvconf** , pero no se qué onda eso...

---

### Post by matutetandil on 2008-06-07
Bueno... aparentemente ahora esta el archivo /etc/resolv.conf, no se porque antes no estaba, o no me aparecía... pero ahora esta...
por lo demás lo que dicen de que la papelera no es tan importante saber donde esta se equibocan... más de una vez me ha pasado, de borrar un archivo con sudo y este quedo en mi papelera, y despues la papelera no se vacía porque no hay permisos para borrar ese archivo... lo que hay que hacer es borrarlo como superusuario... y para eso es necesario saber donde esta...

Bueno... sigo igual con la duda... aparentemente l archivo apareció... pero juro que antes no estaba... jajajaja

Nos vemos!!!!

---

