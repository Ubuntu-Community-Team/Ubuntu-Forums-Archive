---
title: "como instalo un mouse serial a ubunto7.10"
date: 2008-08-26
forum: Centroamerica Team
---

### Post by gidi75 on 2008-08-26
pues si hombre  estoy barado porque tengo una serie de computadores pc con mouse serial y necesito abilitarle el puerto com1 para que me reciba mouse pero no he podido saber como lo hago please ayuda  "poseo problemas

---

### Post by joes7 on 2009-12-09
Vamos a ver.. este si es un problema, sin embargo es facil de arreglar. Hay un reporte de bug sobre esto mismo en el Bug Squad de Ubuntu, aqui te dejo el extracto
[QUOTE=https://bugs.launchpad.net/ubuntu/+source/casper/+bug/9068]
When the X server is automatically configured, users with serial mice must perform additional manual configuration, specifically:
 1. [only for releases prior to 6.06/Dapper] Install the 'joystick' package (don't ask)
 2. Run 'inputattach --help' and find the appropriate protocol option to match your mouse
 3. Run 'inputattach <protocol option> /dev/ttyS0'. This command must be run at system startup in order for this configuration to be permanent; in Dapper, it may be added to /etc/rc.local

[/QUOTE]

Por si no lo entendiste, tienes que instalar el paquete Joystick. Corre 'inputattach--help' y encuentra tu mouse

Corre 'inputattach <protocol option> /dev/ttyS0'. Esto debe ser ejecutado cuando el equipo se encienda; para que sea permanente, se puede poner en /etc/rc.local

Eso es todo. Si no quedo claro, mandame un PM

---

