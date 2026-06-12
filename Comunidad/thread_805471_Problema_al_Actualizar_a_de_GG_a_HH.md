---
title: "Problema al Actualizar a de GG a HH"
date: 2008-05-24
forum: Comunidad
---

### Post by JuaNeMe on 2008-05-24
Hola! Que tal? Como están? Espero que bien, este es mi primer posteo y tengo una duda bastante grande lo de actualizar a Hardy Heron veo el menu.lst me aparecen 2 kernels **2.6.24.16** y 2.6.24.14 yo elijo el que puse en negrita solo xq el número es mas grande (y supuse mas actualizado) es posible eliminar el otro?
Por otra parte cuando inicio sesión y clickeo sobre mi user una vez ingresado el Pass se me pone la pantalla en negro por un segundo y luego vuelve a esa misma pantalla de bienvenido, pidiendome nuevamente el password sólo que esta vez arranca de manera satisfactoria... tiene solucion?

Bueno desde ya muchas gracias. como habran visto estoy empezando con esto asi que me gustaria que me den una mano. Gracias nuevamente...

---

### Post by MeduZa on 2008-05-24
desde synaptics eliminas todos los kernels que quieras pero simpre quedate con uno de respaldo por las dudas!! recomendacion de alguien que hace siempre **** con el principal ^_^

---

### Post by JuaNeMe on 2008-05-24
Gracias, voy a probar lo que me dijiste...
Aunque... si tengo 2 Kernels y me aconsejas dejar de soporte, no tendría que borrar ninguno según vos?

**EDIT:**
Para eliminar el Kernel anterior desde la consola (ya que desde Synaptic no encontré como) puse:
> dpkg --get-selections | grep linux-image
sudo apt-get remove --purge linux-image-XXX

Unos instantes después me tira este error:
rmdir: No se pudo eliminar `/lib/modules/2.6.24-16-generic': El directorio no está vacío

Me fijé que archivos hay en la ruta que me indica y sólo me aparece una carpeta build con todo esto:
> arch    Documentation  include  Kbuild  Makefile        net      security
block   drivers        init     kernel  mm              samples  sound
crypto  fs             ipc      lib     Module.symvers  scripts  usr

Saben como puedo solucionarlo?
Porfa respondan, gracias :)

---

