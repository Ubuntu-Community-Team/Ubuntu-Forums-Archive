---
title: "Ubuntu me odia"
date: 2008-05-28
forum: Comunidad
---

### Post by madelaki on 2008-05-28
Sepan disculpar el titulo poco descriptivo, pero es la verdad. No me gusto la cantidad de errores y problemas de rendimiento que estaba viendo ultimamente asi que con mas conocimientos y espacio en el HD decidi reinstalar Ubuntu. Como era de esperar, primer booteo se me **** de risa en la cara :) Se queda en "Activating swapfile swap...", alguna idea?

---

### Post by User21 on 2008-05-28
Probaste la instalación desde el **cd alternate** de Ubuntu?

---

### Post by madelaki on 2008-05-28
Es la unica solucion? No es muy divertido descargar 700MB a 30kbps

---

### Post by santiagoward2000 on 2008-05-28
Hola!
Una pregunta: ¿instalaste Ubuntu normalmente en una particion aparte o usaste Wubi? Encontré este [thread]("http://ubuntuforums.org/showthread.php?t=551976"). En este caso les pasaba lo mismo usando Wubi. Ellos lo "arreglaron" tocando Ctrl+Alt+Del cuado les aparecia el **"Activating Swapfile Swap"**.

---

### Post by valucha on 2008-05-28
[COLOR="DarkOrchid"]Podés:
1) Pedirlo por [Shipit]("https://shipit.ubuntu.com/")
2) Bajarlo por un [torrent]("http://www.torrentz.com/a56e4a5ff669f0fe478599b0a034246247a72e7a") 
4) [Comprarlo]("http://www.linuxcd.org/view_distro.php?lst=&id_cate=22&id_distro=196&PHPSESSID=96535b83bd069720aac2054fa30b7b21") muy barato
3) Pedirmelo (o pedirselo a alguien con mayor conexión) y te lo bajo y te lo grabo si no podés hacer nada de eso, y te lo doy en algún momento[/COLOR]

---

### Post by juanman on 2008-05-29
Te iba a decir que:
1) Pruebes iniciando Ubuntu en recovery mode (failsafe, modo a prueba de fallos o como se llame) a ver si arranca. Tal vez no arranque pero te tire un error mas específico del problema... Si arranca saltá al paso 3.
2) Si no arranca, y te tira alguna info más, posteala acá. Igual, podés iniciar desde el live cd de ubuntu. Abri una terminal y escribi:
```
sudo chroot /media/sdan
``` Donde sdan es el nombre del dispositivo de la particion donde tenes instalado al ubuntu. Por ej: sda3, hda2. Fijate desde el nautilus cual es...
3) El problema está cuando intenta montar la particion swap, entonces vamos a poner q no la monte automaticamente. Para esto hay q editar el archivo /etc/fstab de la particion de ubuntu. Se puede hacer desde consola con: ```
sudo nano /etc/fstab
```(si estas en el modo recovery no es necesario poner el sudo)
Ahora buscas la linea donde dice algo de swap en la 3er columna. Por ej, algo asi:
```
/dev/sda6       none            swap    sw              0       0
```
Y le agregas un ,noauto despues del sw. O sea te queda algo asi:
```
/dev/sda6       none            swap    sw,noauto              0       0
```
4) Ctrl + o para guardar y ctrl + x para salir
5) escribis exit, enter y reinicias (con ctrl alt del en el recovery)
6) Ahora deberia arrancar bien el sistema, pero ojo! no vas a tener swap, q es util cuando estas usando muchas aplicaciones y se acaba la memoria ram disponible. Una vez q arranque podes intentar montarla con:
```
sudo swapon /dev/sda6
``` donde sda6 es el nombre del dispositivo de la particion swap, el q figuraba en el fstab...
Y ver si te tira error ahora...


Pero en realidad todo esto q te escribi tiene poco sentido despues de leer e interpretar el comentario de valucha:
> 4) Comprarlo muy barato
3) Pedirmelo (o pedirselo a alguien con mayor conexión) y te lo bajo y te lo grabo si no podés hacer nada de eso, y te lo doy en algún momento
Primero, no entiendo xq está antes el 4) q el 3). Tal vez no me enteré y la presi atrasó un número para consumir menos energía (??)

Pero lo importante es la segunda parte: se puede interpretar q la chica te está invitando a su casa "para q vayas a buscar el cd" ;) ;) (guño guiño) :D

Bue, preguntá todo lo q no entendiste del trabalenguas ese q puse arriba...

Saludos

---

### Post by valucha on 2008-05-29
> **juanman said:**
> 
Pero en realidad todo esto q te escribi tiene poco sentido despues de leer e interpretar el comentario de valucha:

Primero, no entiendo xq está antes el 4) q el 3). Tal vez no me enteré y la presi atrasó un número para consumir menos energía (??)

Pero lo importante es la segunda parte: se puede interpretar q la chica te está invitando a su casa "para q vayas a buscar el cd" ;) ;) (guño guiño) :D

Bue, preguntá todo lo q no entendiste del trabalenguas ese q puse arriba...

Saludos

[COLOR="DarkOrchid"]Jajaja es que me parece que yo no entedí el comentario de bajar 700m a 30kb/s...
Por eso le di las opciones para que no tenga que bajarlo.
Lo del 3 y el 4 es porque había puesto 3 opciones y se me ocurrió una más y no sé, no me fijé en esa nimiedad.
Y sobre el comentario de que venga a casa ¬¬, como quieren que las chicas usen Linux o sepan de computación si nos tratan o de terribles nerds antisociales, o interpretan nuestros comentarios con 20mil sentidos eróticos.
[/COLOR]

---

### Post by faktorqm on 2008-05-29
> **valucha said:**
> [COLOR="DarkOrchid"]
como quieren que las chicas usen Linux o sepan de computación si nos tratan o de terribles nerds antisociales, o interpretan nuestros comentarios con 20mil sentidos eróticos.
[/COLOR]

Yo creo que en todos lados pasa eso, no es que en el ámbito informatico ocurre, aparte vos tiraste la primera piedra con lo del camisoncito de ubuntu-ar, asi que ahora bancatela :D 
Mas alla de eso, vos y Natalia son las dos únicas mujeres en la comunidad, (andreasant lei que se enojo y borro ubuntu, y athnea cuando configure su conexion no creo que vuelva :P) asi que bueno, un poco tienen que entender ustedes y recibir los chistes con un poco mas de predisponibilidad, sino van a ser consideradas como nerds antisociales en potencia. jajajajaj :lolflag:

volviendo al post: madelaki: no tenes ningun amigo/conocido que te lo baje "de onda"? o sino en un cyber por $5 mangos te lo bajan & graban, no creo que sean tan mala onda de cobrarte mas... sino te lo baja val y te lo manda por correo, nada d ir a la casa... JAJAJAJAJ :lolflag:

---

### Post by madelaki on 2008-05-29
Lo de C+A+D funciona pero lo que hace es matar procesos, asi que no esta ni cerca de ser una solucion definitiva. Juanman, Wubi. No tengo el fstab.

---

