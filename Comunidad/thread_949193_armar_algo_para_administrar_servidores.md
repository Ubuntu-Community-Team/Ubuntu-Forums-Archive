---
title: "armar algo para administrar servidores"
date: 2008-10-15
forum: Comunidad
---

### Post by sergiom99 on 2008-10-15
Bueno, como dice el titulo, quiero armar algo para monitorear servidores, tal vez usando el logwatch, tal vez agregando mas cosas.
despues posteo bien la funcionalidad que tengo en mente, en alguna parte lo escribi alguna vez, pero los voy tanteando para ver quien se prende y me da una mano. Tengo poca idea de scripting y programacion en bash, pero mas o menos tengo claro el requerimiento de lo que pretendo.
Yo lo quiero usar en CentOS/RHEL pero lo podemos armar para un ubuntu y veo como pasarlo.
En grandisimos rasgos un ejemplo seria: un cron que me avise que se termina el espacio en disco, o que me diga que proceso uso mas del x% de CPU.

Quien se prende?

---

### Post by faktorqm on 2008-10-16
y... no es mala idea, queres hacer una especie de monitor de "cosas" variado, ajjaja 
Lo de que te quedas sin espacio en disco esta buenisimo! cada 4hs lo podes correr(dependiendo del crecimiento en volumen) o cada 8, o cada 12...

Aca hice uno que te muestra en pantalla (o el resultado lo podemos asignar a una variable) cuanto espacio LIBRE tiene una particion.

```
df -aPh | awk '/sda1/ {printf "%s\n", $4 }'
```

donde dice sda1 tranquilamente se puede reemplazar por una variable (puede ser $particion jajaja) y eso a un cron que compare con otras cosas. La verdad que mucho con centOS/RHEL no me llevo, estoy mas con debian, pero en definitiva es lo mismo con un par de cambios y nada mas. Salu2!

---

### Post by fmsismo on 2008-10-16
Te recomiendo que veas nagios.  Es una de las herramientas de monitoreo de equipos más difundida.  Es muy modular y si queres controlar algo que no este resuelto por plugins poder hacerte los tuyos a mano.

Yo te sugiero que avances por ese lado.

Saludos

---

### Post by sergiom99 on 2008-10-16
le voy a pegar una mirada. 
mi idea original es armar algo que mande (o mail o ftp) el resumen diario del equipo a otro server y poder verlo desde un "panel de control" no se si se puede ni como hacerlo, pero es mi idea.
tengo como 8-10 servers dando vueltas por ahi y seria barbaro verlos en la pantalla juntos y ver cual se fue de parametros.

---

### Post by zeroadrenaline on 2008-10-16
Jajajaja yo no puedo con uno solo y el tipo tiene 10 corriendo, un crack!!!

---

### Post by faktorqm on 2008-10-17
y pasa que es lo normal en algunos casos, tenes uno de firewall, 2 que hacen los back-up, 4 con la base de datos, 2 de redundancia (o uno), uno de mail, intranet, archivos, etc. y ya ahi tenes 9 y levantaste algo "basico", no hiciste mucha magia digamos. Salu2!

---

### Post by zeroadrenaline on 2008-10-17
Bueno, lo normal para una empresa que quiere tener todos esos servicios funcionando, si caes en una que solo le interesa un file-server, y son medio ratas (no es que este diciendo algo malo de mi trabajo...) y no te compran ni un pad, y bueno, ahi te quiero ver!!

---

### Post by sergiom99 on 2008-10-17
de la empresa (en linux) tengo 2 locales y 1 remoto. Y despues otros 8-10 desperdigados por los clientes.

lo bueno es que no necesitan tanto mantenimiento :-)

---

### Post by sergiom99 on 2008-10-17
creo que nagios se va acercando. busquemos por ese lado.
[http://www.nagios.org/about/](http://www.nagios.org/about/)

gracias!

---

### Post by sergiom99 on 2008-10-20
lo instale en nuestro entorno VMWare (Fedora/CentOS) y la verdad parece que la rompe. Esta en los repos asi que no tuve problema para instalar, pero es medio complicado configurarlo, porque tiene bocha de cosas.

alguien lo probo? alguien lo usa?

---

### Post by faktorqm on 2008-10-21
Yo lo tengo que empezar a usar, estaba buscando herramientas para monitoreo de redes sobre todo, asi que entre nagios, tkinned y snort calculo que algo tengo que armar xD
En esta semana deberia tener al menos, todo instalado! jajaj Asi que voy a ver que pasa con eso y te comento. Salu2!

---

### Post by hictio on 2008-10-21
Si tenes ganas, algo de tiempo, un servidor mas o menos potente, la mejor solucion (en mi opinion) para monitorear servidores es [Zabbix]("http://www.zabbix.com/").

Nunca lo instale en Ubuntu, ni Server, ni plain vanilla, pero en un CentOS o RHEL mas o menos actual lo podes instalar en una media hora.

Lo que tiene mucho mejor que Nagios (ademas de los graficos) son los templetas para el monitoreo de casi cualquier tipo de plataforma.

Lo que tiene en contra de Nagios es que necesitas mucha mas maquina, y tiene varios requerimientos (por ejemplo, una base de datos, y ciertas extensiones de PHP compiladas) para que funcione, pero no es chino.

Y lo mejor, los dos son gratis y open source.

---

### Post by sergiom99 on 2008-10-21
le voy a pegar una mirada!

---

### Post by hictio on 2008-10-21
La otra alternativa es [Cacti](http://www.cacti.net/), es gratis, etc, genera graficos muy llamativos (de esos que impresionan a los jefes ;) aunque no tanto como los que genera Zabbix)

El tema con Cacti es que esta mas que nada dirigido hacia el monitoreo de equipos con SNMP (routers, switches, etc)
Podes habilitar snmpd en el servidor Linux a monitorear, pero es un paso mas, ademas, si usas el Cacti para hacer poll SNMP por la red, tenes que adaptar scripts (si lo ejecutas en el propio servidor, viene con templates)

---

