---
title: "E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para cor"
date: 2010-03-18
forum: Ecuador Team
---

### Post by sol03 on 2010-03-18
Saludos,
 Es mi primera experiencia con Ubuntu y no puedo instalar programas ni  abrir el Gestor de Paquetes Synaptip con el siguiente error:
 E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg  --configure -a» para corregir el problema.
E: _cache->open() failed, please report.
 Gracias de antemano por su ayuda

---

### Post by lisati on 2010-03-18
> **sol03 said:**
> Saludos,
 Es mi primera experiencia con Ubuntu y no puedo instalar programas ni  abrir el Gestor de Paquetes Synaptip con el siguiente error:
 E: dpkg se interrumpió, debe ejecutar manualmente «[COLOR="Red"]sudo dpkg  --configure -a[/COLOR]» para corregir el problema.
E: _cache->open() failed, please report.
 Gracias de antemano por su ayuda
Arrepentido para la traducción hecha por [www.freetranslation.com](www.freetranslation.com) - yo no sé mucho español. Usted debe correr la orden siguiente en la línea de orden: 
```
sudo dpkg --configure -a
```

---

### Post by EdiOswaldo on 2010-07-21
Hola es verdad ... lisati tiene razon debes ejecutar ese comando en una terminal (consola-bash, como sea jajaja:D)

Presiona CTRL+ALT+T ó vas al menu Aplicaciones/Accesorios/ y clic en Terminal 

Alli escribes
[COLOR=Red]sudo dpkg  --configure -a[/COLOR]
y das enter

es casi probable que te pida la contraseña de root, pones la contraseña, es la misma que pusiste al instalar tu Ubuntu
y listo se ejecuta la linea y puedes solucionar tu problema.

Sino es que estas mas salado que calzoncillo de pescador jajaja

Suerte y espero haberte ayudado en algo...

---

