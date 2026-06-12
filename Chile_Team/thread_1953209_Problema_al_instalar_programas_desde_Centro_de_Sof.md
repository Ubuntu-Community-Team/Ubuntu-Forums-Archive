---
title: "Problema al instalar programas desde Centro de Software"
date: 2012-04-05
forum: Chile Team
---

### Post by Deathster on 2012-04-05
¡Hola!, me dirijo a uds. pues he tenido problemas de frecuencia intermitente con el Centro de Software, cabe mencionar que uso la versión 11.10 de este SO.

Resulta que hace unos días quise instalar VirtualBox y para hacerla corta, fui al Centro de Software, busqué y le dí instalar, sin embargo, y sin esperar mucho me arrojó un error de este tipo:
[IMG]http://i43.tinypic.com/zm0dms.png[/IMG]

Error que es medio raro, pues mi conexión WiFi está de lo mejor (si no no podría estar escribiendo este post).

Pero no es lo único, una vez clickado el botón "Aceptar", me tira esto:
[IMG]http://i41.tinypic.com/2ut6b9x.png[/IMG]

Para tratar de arreglar el problema, bajé directamente el .deb de la página de VirtualBox y cuando lo abro vía Centro de Software, se "aprieta" el botón de instalación y no pasa nada. Cuando lo trato de instalar por consola me tira esto:

> dpkg: acerca de virtualbox-4.1_4.1.12-77245~Ubuntu~oneiric_i386.deb que contiene virtualbox-4.1:
 virtualbox-guest-additions-iso entra en conflicto con virtualbox-4.1
  virtualbox-4.1 (versión 4.1.12-77245~Ubuntu~oneiric) va a ser instalado.
dpkg: error al procesar virtualbox-4.1_4.1.12-77245~Ubuntu~oneiric_i386.deb (--install):
 paquetes en conflicto - no se instalará virtualbox-4.1
Se encontraron errores al procesar:
 virtualbox-4.1_4.1.12-77245~Ubuntu~oneiric_i386.deb


Bueno, además me pasa con otros programas, ¿alguna idea? ¿alguna ayuda?.

¡MUCHAS GRACIAS!.

---

### Post by waltercool on 2012-04-09
Me parece que es un problema con el sistema de paquetes.

Intenta ejecutar esto en un terminal:

[I]sudo apt-get update
sudo apt-get upgrade[/I]

Avisame como te va.

Saludos!

---

