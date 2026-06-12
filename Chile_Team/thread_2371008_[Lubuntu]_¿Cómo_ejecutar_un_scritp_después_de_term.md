---
title: "[Lubuntu] ¿Cómo ejecutar un scritp después de terminar el inicio?"
date: 2017-09-09
forum: Chile Team
---

### Post by donmatas on 2017-09-09
Hola,

estoy tratando de ejecutar un script al inicio de Lubuntu. Leyendo distintos foros, concluí que lo que debía hacer era un archivo de texto con la extensión .sh y luego agragar una instrucción en el archivo /etc/rc.local con el comando que quiero ejecutar. Lo que hice fue lo siguiente.

Con leafpad, cree un archivo que nombré dropbox.sh y le dí permisos de ejecución para cualquiera (chmod +x). El contenido del archivo es el siguiente:

[ATTACH=CONFIG]276661[/ATTACH]

```
dropbox stop && dbus-launch dropbox start
```

Si ejecuto el archivo con doble click y luego "ejecutar", el script funciona.

 Luego agregué el comando que quería en rc.local, quedando así (en negrita lo que agregué):

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**sh /home/usuario/dropbox.sh**

exit 0
```

¿Por qué no funciona? ¿Será porque debe ejectuarse al final del arranque del computador?

Se agradece cualquier orientación.

Salud!

---

