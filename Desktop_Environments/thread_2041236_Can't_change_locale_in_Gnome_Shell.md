---
title: "Can't change locale in Gnome Shell"
date: 2012-08-12
forum: Desktop Environments
---

### Post by Sish on 2012-08-12
Hi! I've been using the latest Gnome Shell on my Ubuntu 12.04 for some time now and everything has worked perfectly. However, the other day I used localepurge to remove languages I don't use (all except from English and Spanish) and I don't know if I purged the "es" locale by accident :-? 

Thing is that after reinstalling English and Spanish from the gnome language selector, the system and all the programs are in Spanish, but I can't get the shell to change its actual language, so right now I have some sort of "dual-language" system :roll:

I'd really appreciate some help on this, because I have tried everything I could think of with no result so far.

Thanks in advance.

---

### Post by Sish on 2012-08-15
Sorry for the double post.

So I tried running the reinstall_debs.sh script located in /usr/share/doc/localepurge. Apt prints:
```
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 74 reinstalados, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0 B/157 MB de archivos.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
Segmentation fault (core dumped)

```

And, of course, does not (re)install anything.

---

