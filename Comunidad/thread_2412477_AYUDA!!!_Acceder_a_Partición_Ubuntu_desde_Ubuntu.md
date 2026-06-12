---
title: "AYUDA!!! Acceder a Partición Ubuntu desde Ubuntu"
date: 2019-02-13
forum: Comunidad
---

### Post by jessiquita89 on 2019-02-13
Hola Comunidad!

Ayer estaba actualizando mi versión de ubuntu mediante comandos y en mitad de proceso mi marido apagó el PC.

Al encender de nuevo en ordenador el Sistema parecía roto, quedando la  pantalla en negro con una numerosa lista de palabras en blanco que no  llego a entender (aparecía la palabra* kernel* por doquier).

Desde un USB con Ubuntu he podido iniciar una versión LIVE pero no hay forma de montar la unidad rota, en ella tengo[B] varios archivos importantes que no quisiera perder.



[/B]He decidido particionar para instalar Ubuntu en una nueva partición quedando así:

/dev/sda1        2048    1050623    1048576   512M EFI System
/dev/sda2     1050624  586988123  585937500 279.4G Linux filesystem
/dev/sda3  1946339328 1953523711    7184384   3.4G Linux swap
/dev/sda4   586989568 1946339327 1359349760 648.2G Linux filesystem


He intentado copiar a una carpeta con:

sudo mkdir /particion

y después:

sudo mount -t ntfs-3g -o ro /dev/sda2 particion/

Pero me salta este error:

Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.






Mi pregunta es cómo puedo ahora acceder a la partición sda2 desde la  nueva instalación en sda4, a fin de poder recuperar los archivos.

Perdonad mi torpeza, soy una pardilla en esto.

Gracias de* antebrazo* a tod@s!!!

:grin:

---

### Post by aromo2 on 2019-02-13
Hola Jessiquita, puedes montar la particion en /mnt:
```
sudo mount /dev/sda2 /mnt
```
Y trata de arreglar con tu marido, que no apague el ordenador sin antes consultarte o tu pon un letrero de "NO APAGAR" cuando estes haciendo algo critico y tengas que dejar el ordenador desatendido. ;-)

---

### Post by howefield on 2019-02-13
Post #2 moved to correct thread.

---

