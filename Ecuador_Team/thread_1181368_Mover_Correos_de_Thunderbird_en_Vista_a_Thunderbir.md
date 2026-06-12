---
title: "Mover Correos de Thunderbird en Vista a Thunderbird en Ubuntu"
date: 2009-06-07
forum: Ecuador Team
---

### Post by icp77 on 2009-06-07
Buenas Noches,

quisiera su ayuda, quiero ver si hay posibilidad de pasar todos los correos que tengo en thunderbird en vista, a mi thunderbird en ubuntu 9.04.

Se como respaladarlos en windows vista, pero no se si habra como pasarlos a thunderbird en ubuntu..

Gracias por la ayuda..

:D

---

### Post by estebandid0 on 2009-06-08
> **icp77 said:**
> Buenas Noches,

quisiera su ayuda, quiero ver si hay posibilidad de pasar todos los correos que tengo en thunderbird en vista, a mi thunderbird en ubuntu 9.04.

Se como respaladarlos en windows vista, pero no se si habra como pasarlos a thunderbird en ubuntu..

Gracias por la ayuda..

:D

tienes que copiar la carpeta que donde estan tus archivos y los correos, ose lo puedes ver bajo cuentas donde te dice exactamente cual es la carpeta

copias la carpeta y la colocas dentro de .mozilla-thunderbird toda la carpeta y el profile .ini

luego inicias thunderbird y deberia funcionar todo bien

sino puedes indicarle cual es la carpeta que tiene la informacion detro de cuentas

---

### Post by icp77 on 2009-06-08
Gracias x responder,

debo hacerlo completamente todo, hay una carpeta llamada thunderbird dentro del app del vista, dentro esta profile y dentro los correos...

Te refieres a esa carpeta..

Gracias x la ayuda...

:p

---

### Post by estebandid0 on 2009-06-09
> **icp77 said:**
> Gracias x responder,

debo hacerlo completamente todo, hay una carpeta llamada thunderbird dentro del app del vista, dentro esta profile y dentro los correos...

Te refieres a esa carpeta..

Gracias x la ayuda...

:p

exacto generalmente tiene un nombre algo asi 54lraeg8.default ahi esta tu profile .ini y todo, copia esa carpeta dentro de 

/home/usuario/.mozilla-thunderbird

y listo, ojo no te olvides de hacer un respaldo siempre, ver que todo este bien y ahi para que lo borres de ser el caso en tu vista

---

### Post by icp77 on 2009-06-09
Gracias x responder,

ya respalde esta carpeta, que comando puedo ejecutar para poder colocar esta carpeta dentro de .mozilla-thunderbird, ya que lo hice con sudo gedit /home/fer/.mozilla-thunderbird desde la terminal con root, pero me da un error y no puedo hacerlo:

 sale un circulo rojo con un menos dentro y a lado /home/fer/.mozilla-thunderbird es un directorio.

Compruebe que ha tecleado el lugar correctamente y pruebe de nuevo.

Luego no me deja hacer nada más, gracias por su ayuda.

:D

---

### Post by estebandid0 on 2009-06-09
> **icp77 said:**
> Gracias x responder,

ya respalde esta carpeta, que comando puedo ejecutar para poder colocar esta carpeta dentro de .mozilla-thunderbird, ya que lo hice con sudo gedit /home/fer/.mozilla-thunderbird desde la terminal con root, pero me da un error y no puedo hacerlo:

 sale un circulo rojo con un menos dentro y a lado /home/fer/.mozilla-thunderbird es un directorio.

Compruebe que ha tecleado el lugar correctamente y pruebe de nuevo.

Luego no me deja hacer nada más, gracias por su ayuda.

:D

claro que te va a dar un error, sudo gedit es para editar un archivo de la configuracion 

el famoso comando que necestas es control + v osea copiar y pegar nada mas

vas a tu carpeta home donde esta el directorio fer, presionas control + h y te aparecen todos los directorios ocultos

ahi buscas el directio .mozilla-thunderbird y copias dentro de el la carpeta, y listo

---

### Post by icp77 on 2009-06-12
Gracias de nuevo, ese comando es de oro, que facil mover mis correos...

:popcorn:

---

