---
title: "Compartición samba WinXP - Se puede crear y borrar pero NO modificar."
date: 2013-07-05
forum: Ecuador Team
---

### Post by dariowvm on 2013-07-05
Hola


Tengo una PC con WinXP que comparte la carpeta "share19"


Esta compartición es montada en una PC con Lubuntu 12.04, agregando la siguiente línea en fstab


//192.168.19.29/share19  /home/paul/folder cifs username=win_user,password=win_pass,iocharset=utf8,mode=0777,dir_mode=07*&#8203;77 0 0


El usuario "paul" es un usuario comun, no sudoer, no nada.


Logueado como "paul" accedo bien a la compartición, puedo crear archivos y borrarlos, pero NO puedo modificarlos.


Creé una planilla de LibreOffice. Cierro la aplicación e intento re-abrir la planilla, se abre en modo Solo-Lectura.
Ocurre lo mismo desde el terminal con nano y archivos de texto plano.


Si me logueo con el usuario sudoer y ejecuto el LibreOffice o nano con sudo, no hay problema.


Desde otros PCs de la red con Ubuntu comun y Windows, tampoco hay problemas.

---

