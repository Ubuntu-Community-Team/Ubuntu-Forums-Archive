---
title: "Ubuntu 18.04 sin espacio suficiente en disco."
date: 2018-06-25
forum: Centroamerica Team
---

### Post by el_eternauta on 2018-06-25
Hola comunidad, saludos, mi nombre es Raúl y este es mi primer post aquí, imagino que estoy en el lugar correcto, sino espero sepan disculparme. 
Mi problema es el siguiente: He instalado **Ubuntu 18.04LTS** en una partición de 30GB, la Home en otra de 18GB y SWAP en una de 2GB, pues con la RAM que mi equipo tiene (6GB) no creo que la vaya a usar. 
Llevo una semana usándolo y todo fue muy bien hasta anoche en que me saltó un cartel indicando que no tengo suficiente espacio en disco:

[IMG]https://scontent.ftuc1-2.fna.fbcdn.net/v/t1.0-9/36003059_10155224003136853_2480785123193126912_n.jpg?_nc_cat=0&oh=3ee5b498bb563e0c84bbad55e21128bc&oe=5BADEFF0[/IMG]

Para ser sincero, no tengo ni la más remota idea de que es lo que está ocupando tanto espacio. Yo tengo un par de carpetas en el escritorio con imágenes y algunos vídeos de baja resolución que no suman ni 2GB, y aunque sumaran mucho más no deberían intervenir en el espacio en disco de la raíz, ¿me equivoso? 
¿Acaso Ubuntu 18.04 necesita más espacio? 

[IMG]https://scontent.ftuc1-2.fna.fbcdn.net/v/t1.0-9/36199946_10155224044631853_3246458868720467968_o.jpg?_nc_cat=0&oh=9eaa5350a5eae523eb67ec32be9d776b&oe=5BABDF3B[/IMG]


Reconozco que he instalado algunos programas de edición de audio y vídeo e íconos y temas visuales, pero estos últimos están en mi carpeta personal. Estoy desconcertado y eso sumado a mi poco conocimiento hacen que hoy esté aquí preguntando por si alguno puede darme una solución.
También he instalado '**gnome-session-flashback**' y '**unity**' para poder usar compiz y esos efectos que tanto me gustan. Al iniciar sesión me da como seis opciones: Ubuntu predeterminado, Compiz, Metacity, Ubuntu en Wayland y no recuerdo que más. Creo que tengo un lío importante con eso y no quiero tener que reinstalar, pues supongo que alguna solución habrá.

*He usado algunas aplicaciones para limpiar un poco Ubuntu, como por ejemplo **Ubuntu Cleaner**, pero no se soluciona con eso.

Espero me aclaren un poco las cosas y me digan donde estoy errando. Muchas gracias por su tiempo. Saludos.

---

### Post by WHK on 2019-01-18
Hola, puedes utilizar el comando "df -h" para saber el espacio total de tus discos. Recuerda que también puedes usar el comando "du -h /directorio/" para saber la cantidad total de espacio que está usando algún directorio en particular. No te voy a recomendar que instales algunas aplicaciones gráficas para detectar el problema porque dudo que los puedas instalar si tienes problemas de espacio de disco. Saludos.

---

