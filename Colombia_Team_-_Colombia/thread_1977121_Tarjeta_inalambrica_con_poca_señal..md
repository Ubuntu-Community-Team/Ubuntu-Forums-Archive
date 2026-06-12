---
title: "Tarjeta inalambrica con poca señal."
date: 2012-05-09
forum: Colombia Team - Colombia
---

### Post by memo85 on 2012-05-09
Hola a todos, de nuevo yo con mis preguntas tontas, pero esque hasta ahora entro al mundo de ubuntu y se me ha dificultado algunas cosas.

Ahora el inconveniente es que en Ubuntu 10.04, mi pc lo pongo a escanear con airodump-ng, las redes que estan a mi alrededor, y no me aparecen las mismas que le aparecen a un computador que esta al lado mio, pero con Windows 7.

He escuchado que puede ser un problema del Kernel y hay que parchearlo.
Un amigo instaló el 10.10, y le pasaba lo del canal negativo 1 (fixed channel -1), y lo que hizo fue parchear sus drivers asi:

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2)
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot


A él le funcionó y corrigió su problema, pero yo instalé el mismo 10.10, me ocurrió el mismo problema, traté de hacer los mismo pasos de él, pero no me corrigió el problema, asi que instalé el 10.04 y poblema arrelado.(instalé el 10.04 poque lei en alfun foro que esa version tania mejor compatibilidad con el hardware)

Pero he notado que la señal es muy mala y se me cae constantemente la señal.
No se mucho, pero en lo poco o mucho que he buscado dicen que puede ser problema de drivers, y he leido que los drivers de compat-wireless arreglan en algo esos problemas.

ahora bien, de esta pagina, [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/) , se pueden descargar muchisimos paquetes, el cual uno de ellos le sirvió a mi amigo, pero a mi no me sirvió, por lo que deduzco que mi tarjeta inalámbrica era distinta a la de el (eso creo, porque no le veo de otra), entonces, mi pregunta es ¿ como hago para saber, que paquete tengo que bajar de esta pagina para parchar mis drivers ? , ya que si bajo algun paquete y por equivocación no era el indicado para mi, puedo desistalar mi tarjeta, y ahí si que peor (lo digo porque ya lo hice, y fue una tortura).

Que debo hacer? Tengo que bajar los drivers directamente de la pagina del fabricante o que ?? como se haría eso ??

los datos que me arroja el comando  lspci | grep Wireless  son :
~$ lspci | grep Wireless
06:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

~$ lsmod | grep 'wl'
iwlagn                106911  0 
iwlcore               106149  1 iwlagn
mac80211              205434  2 iwlagn,iwlcore
cfg80211              126528  3 iwlagn,iwlcore,mac80211
led_class               2864  2 iwlcore,sdhci


Ubuntu 10.04 (lucid)
2.6.32-41-generic

Salu2

---

### Post by darkhole on 2012-05-13
Mi recomendacion, si tu equipo es de hace 3 años para aca, mejor actualizalo a la version 12.04, lo que menciones del kernel es en parte cierto, es quien maneja los controladores, pero tambien estan los crontroladores que se usan como modulos...

Para no cimplicar las cosas, las nuevas versiones de Linux y por ende de Ubuntu mejoran el soporte de dispositivos, por lo cua en tu caso probablemente ya corrigieron este error de señal..

Ahora, tambien esta la opcion de usar un kernel nuevo en Ubuntu 10.04 y si no funciona, instalar los ultimos controladores propietarios, aunque para mi seria mas sencillo y mejor actualizar a 12.04.

Por cierto, si nos das la salida del comando lspci en la terminal te podriamos ayudar mas.

---

### Post by memo85 on 2012-05-17
> **darkhole said:**
> Mi recomendacion, si tu equipo es de hace 3 años para aca, mejor actualizalo a la version 12.04, lo que menciones del kernel es en parte cierto, es quien maneja los controladores, pero tambien estan los crontroladores que se usan como modulos...

Para no cimplicar las cosas, las nuevas versiones de Linux y por ende de Ubuntu mejoran el soporte de dispositivos, por lo cua en tu caso probablemente ya corrigieron este error de señal..

Ahora, tambien esta la opcion de usar un kernel nuevo en Ubuntu 10.04 y si no funciona, instalar los ultimos controladores propietarios, aunque para mi seria mas sencillo y mejor actualizar a 12.04.

Por cierto, si nos das la salida del comando lspci en la terminal te podriamos ayudar mas.


gracias por responder.

Pues en algun momento instalé el 12.04, pero no me gustó la apariencia (no se si esque estaba muy acostumbrado al 10.04), en todo caso en el 12.04 tube el problema con aircrak-ng del canal negativo channel -1 (no se si lo han escuchado), problema que con 10.04 nunca tube (con la 10.10 tambien se presentaba dicho problema), y aunque se que se podia arregar, pues no me quize enchicharronar con eso y eso fue lo que me mandó de una vez de nuevo para el 10.04. 
Lo que no me gustó del 12.04 es que por ejemplo las ventanas se entremesclaban y no se distinguian de la barra principal, el menú habia cambiado demasiado y no escontraba el menú que  tenia en el viejo 10.04. (hasta ahora me enteré que en el 12.04 podia usar el viejo entorno grafico del 10.04, ya qué !!!!).

En fin, no me gustó y decidí volver al antiguo pero muy bueno (para mi) 10.04.

Con la tarjeta inalambrica, pues ya no me quejo, le he puesto los drivers compat-wireless-2010-10-16 , y pues ha resuelto en algo el problema, pero sigo con la inquietud, de cual archivo bajar de la pagina de compat, porque a mi me funcinó el compat-wireless-2010-10-16, pero se supone que uno deberia escoger el mas reciente, y me descargue un archivo del 2011 (compat-wireless-2011-x-x) y me desistaló la tarjeta, uno del 2012 (compat-wireless-2012-x-xx), y peor, y el unico que no me dañaba el sistema era el compat-wireless-2010-10-16. 

Esto es lo que me arroja el lspci:

06:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

Gracias.

.

---

