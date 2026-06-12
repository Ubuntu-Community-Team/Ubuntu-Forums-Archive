---
title: "No Puedo Actualizar A Ubuntu 8.04"
date: 2008-05-24
forum: Comunidad
---

### Post by marcesneibrun on 2008-05-24
Buen día a todos, gracias por contestar siempre y tratar de ayudar.
Tengo ubuntu 7.10 quiero actualizar a 8.10 mediante el gestor de actualizaciones y me tira este error.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release) Unable to find expected entry  universedeb/binary-i386/Packages in Meta-index file (malformed Release file?)

Ya probe con varias conexiones y no puedo actualizar.
Me pueden ayudar
Desde ya muchas gracias
MARCELO

---

### Post by EnriqueK on 2008-05-24
Yo  pude pasar de la 7.04 a la 8.04 , pero no sería una actualización, sino una instalación de cero pero  de forma automatizada,  los pasos son mas o menos los siguientes, primero respalda tu carpeta de usuario y todos los datos que creas conveniente,

Seguidamente abre Synaptic en la antigua instalación y ve a Archivo -> Guardar selecciones como , marca el casillero  "Guardar el estado completo ............" le das un nombre cualquiera y se genera un documento de textos plano con todos los paquetes instalados, allí figura solo el nombre de los paquetes sin especificar la versión, ya APT se encargará de completar los "detalles" .

Luego instala Hardy desde el Live Cd , habilita todos los repositorios equivalentes a la instalación antigua y haciendo un proceso semejante con el Synaptic o sea ve a Archivo -> Leer selecciones , busca el archivo de textos creado en la instalación anterior y que debes portar a la nueva instalación , sigue los pasos y comienza la descargas e instalación de todos los paquetes que corresponderán a la nueva versión.

Este método solo instala los paquetes que hayan sido descargados e instalados desde los repositorios, los que hayas compilado o instalados de forma manual , deberás volver a instalarlos de la misma manera, lo mas importante es que todo se hace bajo control de APT en la que instala las nuevas versiones de paquetes , por eso lo mas crítico del método es el de tener repositorios equivalentes en ambas instalaciones y si hubiera un paquete que no tiene un equivalente para en los repositorios de la nueva versión, simplemente no lo toma en cuenta, por ejem si antes tenías xmms , ahora no se podrá instalar.
Recalco lo dicho al comienzo, este método es una instalación limpia o partiendo de cero, pero automatizada, la que estar bajo control de APT, tiene plena garantía de éxito, por ejemplo nunca vas atener problemas con paquetes compilados en la versión antigua por que simplemente estos paquetes no serán tomados en cuenta por no figurar en los repositorios, como sería el caso de los drivers de las tarjetas gráficas y así con otras fuentes de problemas.

---

