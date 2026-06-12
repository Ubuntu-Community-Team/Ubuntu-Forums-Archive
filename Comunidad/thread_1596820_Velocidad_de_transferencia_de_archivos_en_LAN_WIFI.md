---
title: "Velocidad de transferencia de archivos en LAN WIFI"
date: 2010-10-14
forum: Comunidad
---

### Post by spongebobp2m on 2010-10-14
Hola Foro!,

escribo este post porque estuve buscando sobre el tema y la verdad es que no logro pescarle la vuelta..

me pasa lo siguiente:
tengo armada una LAN hogareña con 2 PCs de escritorio, una netbook (todas corriendo Ubuntu 10.04) y una PS3, todo conectado por wifi. 
Hasta ahora, no se me ha dado por compartir archivos entre las PCs, pero resulta que el otro día instalé el mediatomb en una, para que sirva los videos al PS3 (más que nada), y noté que "lagea" demasiado.. (los videos no se ven fluidos, mas bien se traban cada 15 seg.)
De allí que me puse a jugar con el router y las configuraciones de wifi de las PCs, pero no he llegado a nada bueno.
Instalé en todas las PCs y netbook el servidor SAMBA, para hacer pruebas de velocidad de transferencia de archivos, y obtengo lo siguiente:
Cuando paso archivos de una PC a otra, la velocidad media ronda los 200Kbps (bajísima)
Todas las conexiones al router informan estar a 48Mbs o 54Mbs.
Cuando descargo datos de internet, la velocidad promedio de descarga es de 354 Kbps (mucho mayor que la de transferencia de datos entre PCs de la misma red!!!)
alguien puede sugerirme que tocar para arreglar esto?
existe en SAMBA algun limitador de velocidad (subida o bajada) que este afectando?

gracias!...

---

### Post by juancarlospaco on 2010-10-14
Son todas Linux?, Samba es un poco lento de por si, yo usaria NFS o SSHFS.
Es segura tu red o alguien puede estar "colgado" sin que sepas?

---

### Post by biale on 2010-10-14
En principio no uso Samba, solo SSHFS...

De todas maneras la velocidad de una red WIFI depende de unas cuantas cosas, mas de las que me gustarían. El equipamiento, el soporte al mismo, la potencia de la señal, mas la relación señal/ruido (interferencias), el HW mas lento y etc.

Por lo menos fijate con el monitor del sistema que tan estable es la transmisión. Y una simple prueba con cable cruzado puede llegar a desafectar a Samba.

Y por las dudas: atención de no confundir Kbps con KBps.

---

### Post by z37a on 2010-10-17
WiFi norma G son 54Mbps, si sacamos las cuentas serian 54/8=6.75MBps, a eso le sumamos que por lo general no tienen MIMO, lo cual hace que 6.75MBps se divide pro la cantidad de equipos conectados(es topología de bus) que en este caso son 2 lo cual nos da 3,375MBps, a lo cual luego le tenemos que restar los encabezados de los paquetes y demás dejándonos con aprox 3MBps de velocidad de transferencia.

Definitivamente el WiFi es Lento! Pero para poder evitar esto podes utilizar Router mas placas WiFi N(300 Mbps, creo, o draft N que es mas lento, 150Mbps) junto con MIMO(que permite tener 2 o mas conexiones con topología estrella y no BUS!

Ahora el problema puede ser que no es tan exacta la división, si la PS3 pide muchos paquetes bueno va a saturar el ancho de banda del WiFi.

---

### Post by biale on 2010-10-17
Incluso el encriptado de paquetes afecta a la performance.

Computadora a router WIFI y norma G recuerdo haber medido alrededor de 1,5 MBps. A su vez el otro equipo se conectaba al router por cable UTP.

Eso con un rate de transmisión bastante estable en archivos grandes pero también bastante menos de lo que uno espera.

---

