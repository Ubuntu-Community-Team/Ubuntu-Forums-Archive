---
title: "Directorio Telefonico VoIP en Python"
date: 2011-07-04
forum: Comunidad
---

### Post by juancarlospaco on 2011-07-04
**Es un Directorio Telefonico VoIP en Python ideal para una Intranet o Pyme.**

La idea es que como sucede muchas veces en Pymes y demas, la gente empieza a hacer, 
imprimir y enviar por mail hojas de calculo para anotar la lista de internos,
que en algunos lugares pueden agregarse varios internos en poco tiempo,
lo cual no es algo muy eficiente y queda desactualizado...,
los telefonos VoIP al bootear se descargan un .XML desde el Asterisk 
con el Directorio Telefonico Actual en Uso; lo que hace este pequeño soft es
levantar una pagina web, descargar el .XML, darle formato de pagina Web elegante,
y servirlo en el Host local en que se ejecuta hacia toda la red local, 
no requiere tocar en el Asterisk, se ejecuta en otro equipo, listo para usar.
Viene con:
[LIST]
[*]1 .XML como usan los telefonos IP, de ejemplo (no requerido, podes borrarlo)
[*]1 Archivo telefonosweb.py que es el programa principal
[*]Bottle.py (el framework web, requerido)
[/LIST]

El Servidor Web sirve el directorio telefonico en la direccion Local **de Intranet **en:
[LIST]
[*]http:// direccion-ip-o-dns/tel
[*]http:// direccion-ip-o-dns/telefonos
[*]http:// direccion-ip-o-dns/telefono
[/LIST]

Uso:
telefonosweb.py y bottle.py deben estar en la misma carpeta (cualquiera)
```
sudo python telefonosweb.py
```

Entrar con el navegador a [http://127.0.0.1/tel](http://127.0.0.1/tel)
Mas adelante configurate un DNS **interno** para que apunte a: TuEmpresa.org/tel por ejemplo



Configuracion:
Usa un comando de Bash, con wget, grep y sed para parsear el .XML
para saber que linea hay que editar en el archivo telefonosweb.py hacer:

```
cat telefonosweb.py | grep phonebook.xml
```

reemplazar el cat por un wget que descargue el .XML desde tu servidor y lo parsee,
el ejemplo es bastante explicativo para cualquier Admin con conocimiento basico de Bash (no necesita saber Python).

[LIST]
[*]Bazaar: [http://bazaar.launchpad.net/~juancarlospaco/+junk/dirtel/files](http://bazaar.launchpad.net/~juancarlospaco/+junk/dirtel/files)
[/LIST]

No encontre ninguno igual tan facil, asi que lo paso por si alguien le es util, en TU empresa lucira asi:

---

### Post by guillermolisi on 2011-07-04
Juanca, te estas superando dia a dia !

Muy buena aplicacion !

Otra vez mas, gracias !

---

### Post by mama21mama on 2011-07-05
xD

---

### Post by juancarlospaco on 2011-07-05
> **mama21mama said:**
> xd

&#664;_&#664; *?*

---

### Post by mama21mama on 2011-07-05
):p

---

