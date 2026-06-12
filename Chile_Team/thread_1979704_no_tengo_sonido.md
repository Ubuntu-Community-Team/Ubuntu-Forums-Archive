---
title: "no tengo sonido"
date: 2012-05-13
forum: Chile Team
---

### Post by javierfigueroa on 2012-05-13
no puedo escuchar nada en ubuntu. ni radios, youtube, no reproduce ningún sonido.

---

### Post by papibe on 2012-05-14
Hola Javier.

Prueba si usando 'alsamixer' puedes identificar una salida de sonido que está muteada. Revisa esta [página]("http://www.patheticcockroach.com/mpam4/index.php?p=62") para ver como se hace.

Si eso no funciona, puedes postear el resultado de este comando?
```
sudo lshw -C multimedia
```
Saludos.

---

