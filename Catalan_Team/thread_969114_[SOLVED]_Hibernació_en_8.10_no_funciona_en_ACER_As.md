---
title: "[SOLVED] Hibernació en 8.10 no funciona en ACER Aspire"
date: 2008-11-03
forum: Catalan Team
---

### Post by Diegstroyer on 2008-11-03
Salutacions, des de la 6.10 que no aconsegueixo hibernar,el meu ordinador es un **Acer Aspire 1690 WLMi** amb una **ATI Mobility Radeon x700 PCIEx**, i ara amb la **8.10 i instal·lació neta**,volia reintentar-ho.

He seguit molt tutorials, he provat amb **uswsusp** i sempre em fa el mateix (tant amb uswusp com amb el sistema d'hibernació que ja ve preinstal·lat). En clicar a **hibernar**, el procés comença correctament, però **en el moment de apagar-se** l'ordinador, aquest **es reinicia** i torna de la hibernació ell tot solet.

Tinc 1GB de RAM i 2GB de swap.

El cat **/etc/uswsusp.conf** dona el següent: 

[B]# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda2
splash = n
compress = y
early writeout = y
RSA key file = /etc/uswsusp.key
shutdown method = platform[/B]

He modificat el **/etc/default/acpi-support** com diuen en molts tutorials i res de res. Fa sempre el mateix.

Aconsegueixo hibernar si quan s'està reiniciant premo el botó d'apagat i la hibernació funciona.

Com a dades: **tinc la swap a /dev/sda2 i completament activa** i la suspensió em funciona correctament. La ordre **s2both em mata l'ordinador** i l'haig d'apagar (suposo que és per que no tinc partició both activa en reiniciar), l'ordre **s2didk** fa el que esmento a dalt (reinicia després de crear la imatge de hibernació).

Salutacions.

---

### Post by PatrickVogeli on 2008-11-03
has probat a posar shutdown alla on hi posa platform?

salut

---

### Post by Diegstroyer on 2008-11-03
Solucionat,just el que comentes.

Ara he editat l'arxiu: **/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux**, canviant el contingut per:

#!/bin/sh
/sbin/s2disk

Ara,de tant en tant, a l'hibernar posa una pantalla estranya mentre genera la imatge d'hibernació, però al menys hiberna correctament.

---

### Post by PatrickVogeli on 2008-11-04
Per una altra vegada, no cal que facis això, hi ha maneres millors d'arreglar-ho. A l'arxiu /usr/lib/pm-utils/defaults hi trobaras la linea # SLEEP_MODULE="kernel". Per configurar l'us d'uswsusp nomes calia editar aquella linia i deixar-la de la següent manera: SLEEP_MODULES="uswsusp".

salut

EDITO: si has solucionat el problema, marca el fil com a resolt, si us plau.

---

