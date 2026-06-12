---
title: "El extraños caso del desbloqueo de monitor dual en Xubuntu y sus problemas"
date: 2016-06-06
forum: Chile Team
---

### Post by donmatas on 2016-06-06
Hola:

instalé hace poco Xubuntu 16.04 y me he encontrado con problemillas con la función de bloqueo de pantalla. Uno es que al desbloquear la pantalla, el cursor del ratón desaparece, aunque sigue activo ("modo fantasma"). Implementé una solución parche que [está aqui]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604/comments/109")

Básicamente se trata de hacer un lanzador con el siguiente script y ponerlo en una esquina del panel, para encontrarlo con el cursor "fantasma": ```
xset s activate
```

Ahora surge otro problema. Tengo la laptop conectada a un monitor, el cual uso como pantalla (la del laptop la mantengo apagada). Cuando desbloqueo la pantalla, la del laptop se enciende (solo con luz, pero sin contenido). Para volverlo a la normalidad, debo abrir la configuración de pantallas y hacer algún juego para volver a ponerlo en el modo que lo uso. Ahí vuelve a la normalidad. ¿Alguna idea de solución?

gracias!
M

---

### Post by donmatas on 2016-06-21
La cosa empeora. Cuando bloqueo la pantalla en modo escritorio extendido, al desbloquearla, el compu se queda colgado al más puro estilo win$hit. La solución que encontré es desinstalar el pinche light-locker que parece ser el causante de todos los problemas. En su lugar instalé el i3lock

```
sudo apt-get remove light-locker

```

Reiniciar

Luego

```
sudo apt-get install  i3lock
```

Finalmente, hice una combinación de teclado (ctrl + L) con la siguiente orden

```
i3lock -d 1
```

El "1" significa que apague la pantalla después de un minuto. 

Saludos!
M

---

