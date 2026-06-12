---
title: "Nuevo en Linux/Ubuntu"
date: 2012-07-30
forum: Comunidad
---

### Post by levazz on 2012-07-30
Buenos dias, mi nombre es Lucas.
Instale Ubuntu 12.04 en una notebook, nunca antes lo habia usado, pero todo bien por suerte.
Me surgieron varias preguntas, algunas ya las evacue.
Las que me quedaron son las siguientes:
-¿Como bloquear puertos USB?
-Como accedo a CREAR/ADMINISTRAR grupos de usuario.
-(Basandome en Windows) ¿Donde encuentro el administrador de dispositivos? Si es que existe.
Y por ahora eso..

Desde ya, muchas gracias.

---

### Post by albandy on 2012-07-30
> **levazz said:**
> Buenos dias, mi nombre es Lucas.
Instale Ubuntu 12.04 en una notebook, nunca antes lo habia usado, pero todo bien por suerte.
Me surgieron varias preguntas, algunas ya las evacue.
Las que me quedaron son las siguientes:
-¿Como bloquear puertos USB?
-Como accedo a CREAR/ADMINISTRAR grupos de usuario.
-(Basandome en Windows) ¿Donde encuentro el administrador de dispositivos? Si es que existe.
Y por ahora eso..

Desde ya, muchas gracias.


-¿Como bloquear puertos USB?
Mientras el usuario no pertenezca a los grupos plugdev y fuse no puede usarlo.
- ¿Como accedo a CREAR/ADMINISTRAR grupos de usuario?
Yo soy más de consola, ya que te permite hacer las mil y una, pero puedes administrar los usuarios y los grupos en el panel de configuración del sistema (suele estar en el botón de más a la derecha de la barra superior).
- El tema de los dispositivos es completamente diferente. Funciona mediante módulos del kernel (nucleo del sistema). En principio es totalmente transparente y no necesitas tocar nada, pero puedes buscar información sobre HAL (Hardware Abstraction Layer) y los drivers del kernel.

---

### Post by levazz on 2012-07-30
No veo la parte de administracion de Grupos, veo lo de los usuarios si pero de grupos nada...ah buenisimo lo de los USB entonces.
Mil gracias.

---

### Post by levazz on 2012-07-30
Bien, cree un usuario nuevo que en teoria es un usuario sin privilegios.
Puse un USB y lo tomo lo mas bien.
Cual seria el/los comando/s para poder bloquearlos/desbloquearlos?
Muchas gracias.

---

### Post by albandy on 2012-07-31
> **levazz said:**
> Bien, cree un usuario nuevo que en teoria es un usuario sin privilegios.
Puse un USB y lo tomo lo mas bien.
Cual seria el/los comando/s para poder bloquearlos/desbloquearlos?
Muchas gracias.

Es posible que si has añadido el usuario por el asistente gráfico te haya añadido a los grupos más usuales.

En una sesión con ese usuario abre una consola y escribe id, luego pon aquí el resultado.

De todas formas, siempre puedes bloquear el acceso a los dispositivos usb añadiendo el módulo del usb-storage al blacklist:

```

sudo -s
echo blacklist usb-storage >> /etc/modprobe.d/blacklist
exit

```

---

### Post by levazz on 2012-08-01
Mmmm nose la verdad, ya probe de todo y nada funciona, probe por el blacklist y tampoco...
Nose que estare haciendo mal.

---

### Post by madjr on 2012-08-01
quisas esto ayude?

[http://ubunlog.com/deshabilitar-el-uso-de-discos-usb-para-un-usuario-en-linux/](http://ubunlog.com/deshabilitar-el-uso-de-discos-usb-para-un-usuario-en-linux/)

[http://hotfixed.net/2011/06/27/deshabilitar-el-almacenamiento-en-dispositivos-usb-linux/](http://hotfixed.net/2011/06/27/deshabilitar-el-almacenamiento-en-dispositivos-usb-linux/)

---

### Post by levazz on 2012-08-01
Gracias madjr, pero ya las probe esas soluciones.
Nose, debo ser yo que estoy haciendo algo mal.
Gracias igual.

---

