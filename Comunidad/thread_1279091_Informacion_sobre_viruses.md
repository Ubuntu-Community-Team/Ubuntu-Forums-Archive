---
title: "Informacion sobre viruses"
date: 2009-09-30
forum: Comunidad
---

### Post by LolaMora on 2009-09-30
Hola a todos.

Quiero lanzar una pregunta con el objetivo de: ampliar lo que ya se y enseñar a otros.

Esto va a estar dirigido a los que están mostrando un indicio de interés por GNU/Linux.

Que le contestarían Uds. a usuarios de Wind2 muy temerosos de los virus si les preguntasen lo siguiente:

1- ¿Hay virus para linux? 
   Si la respuesta es afirmativa: ¿en que afectarían a mi PC? ¿como puedo evitarlos?

2- ¿Qué pasa si me bajo algo para ejecutar con el wine y viene infectado?

3- Si la virtualBox se infecta, ¿que le pasa a mi PC?

Hasta pronto.

---

### Post by pol666 on 2009-09-30
1- ¿Hay virus para linux?
si

¿en que afectarían a mi PC? ¿como puedo evitarlos?
No afectan a usuarios promedio, son virus dirigidos a servidores por algun fín en particular y la probabilidad que te afecte es casi nula.

2- ¿Qué pasa si me bajo algo para ejecutar con el wine y viene infectado?
Wine corre en tu carpeta de usuario así que nada puede afectar al sistema, a lo sumo si el virus es eficiente dejara de funcionar wine pero nunca escuche algo así.

3- Si la virtualBox se infecta, ¿que le pasa a mi PC?
Si en el windows virtualizado se infecta, a tu linux no le pasa nada. A tu windows virtualizado depende del potencial del virus. Por cierto es divertido probar virus en una maquina virtual jaj.

---

### Post by Sleeping Beauty on 2009-09-30
Agrego un interrogante más:
Que pasa si mi máquina comparte archivos con otra que tiene Win? Así como los virus para Win no afectan a Linux los que son dirigidos a Linux afectarán a Windows? 
Son preguntas interesantes para saber que decirle a la gente que se interesa por el SL desde el lado de la seguridad. No sera ni la primera ni la ultima vez que sugiera que alguien migre a Ubuntu despues de formatear la PC y/o perder archivos valiosos por un virus

---

### Post by juancarlospaco on 2009-09-30
> **Sleeping Beauty said:**
> Agrego un interrogante más:
Que pasa si mi máquina comparte archivos con otra que tiene Win?

No pasa nada, 
probablemente los .exe de Windows no tienen permisos de ejecutables en Ubuntu,
y si los tienen tampoco pasa nada por que son binarios para windows,
y si son ejecutados con alguna capa de compatibilidad como Wine o Mono,
el que se muere es el Mono o el Wine, 
para 1 solo usuario de todos los del sistema,
que en el peor de los casos se arregla reinstalando el Wine,
pero el sistema permanece intacto por completo.

> **Sleeping Beauty said:**
> Así como los virus para Win no afectan a Linux los que son dirigidos a Linux afectarán a Windows? 


Los Virus de Linux, si es que alguna vez te encontras con uno, no van a correr en Windows,
por que no son ejecutables en Windows, no son .exe , .msi, .bat , etc.
y no pueden correr por ser para otro sistema operativo diferente.



La verdad es que en la teoria se dicen muchas cosas,
pero en la practica hace mucho que vengo buscando Virus para Linux y es mentira,
he bajado y ejecutado muchas cosas, como supuestos Virus hechos en Java,
supuestos Virus para Linux y la verdad es que no son,
muchos codigos fuente que al compilarlo supuestamente destruyen linux,
y es un codigo que no hace nada mas que fallas de segmentacion en si mismo,
como mucho son ForkBombs, que no es un Virus tampoco,
un ForkBomb es como un software que come demasiado recurso pero no un virus,
la mayoria los encontre en foros/web relacionados con windows,
y como ninguno sabe y lo prueba realmente de ahi sale el mito:

[I]"Ubuntu no tiene Virus por que tiene menos usuarios que Windows,
pero el dia que valga la pena hacer un Virus para Linux lo van a reventar"[/I]

...Y no comprenden que es por una **cuestion de Diseño**.

En Windows todo es un .exe que se ejecuta al inicio, 
el firewall por ejemplo en windows es eso, 
en cambio en Linux tiene el firewall integrado en el core,
seria muy dificil sino imposible tener un Linux sin firewall,
podes no tener grafica para monitorearlo, podes cofigurarlo mal,
podes no tener ufw, ...pero el iptables esta ahi.


Lo mismo con los AntiVirus, son un .exe al inicio,
podes tener el SuperUltraAntiVirus 2015, 
pero el Virus saca ese .exe del inicio y estas sin ninguna proteccion.
Eso le paso hace poco a un conocido...

Ademas el AntiVirus no es seguro, solo *"ve"* los archivos de sus firmas.

---

### Post by faktorqm on 2009-09-30
> **Sleeping Beauty said:**
> Agrego un interrogante más:
Que pasa si mi máquina comparte archivos con otra que tiene Win? 

Vos compartis desde un linux, a un windows, en modo solo lectura, no pasa nada. Si vos tenes permisos totales y un cliente windows accede a eso, si, te lo puede borrar si el virus se aviva. Igual creo que existe una opcion rara en el samba para que en vez de borrarlo lo mande a una papelera que el user de windows no pueda acceder, por si pasa eso, pero no recuerdo.

Los virus no son multiplataforma, y si hay en java como dijo aca alguien los tenes que ejecutar como root para que verdaderamente te puedan llegar a hacer algo. nunca lo hagan y listo.

Para las forkbombs, existe una proteccion que yo la configuro en los servidores, que establece el numero maximo de procesos por usuario, entonces le pones, no se, 120, y cuando llega a ese tope no puede hacer mas nada, entonces no te consume todos los recursos hasta el hartazgo, sino que no hace mas que "cosquillas" por asi decirlo xD

Salu2!

---

### Post by sergiom99 on 2009-09-30
> **faktorqm said:**
> 
Para las forkbombs, existe una proteccion que yo la configuro en los servidores, que establece el numero maximo de procesos por usuario, entonces le pones, no se, 120, y cuando llega a ese tope no puede hacer mas nada, entonces no te consume todos los recursos hasta el hartazgo, sino que no hace mas que "cosquillas" por asi decirlo xD

Salu2!
Martin, como es esto?
Gracias!

---

### Post by juancarlospaco on 2009-10-01
No..., yo digo que no hay, no hay Virus para Linux.

---

### Post by guillermolisi on 2009-10-01
Igual existen rootkits y otras amenzas sofisticadas que poseen mecanismos de traslacion que requieren solamente detectar paquetes IP en una red y si bien no afectan al sistema operativo directamente, la cantidad de pequeños paquetes de broadcasting que emiten afectan a la LAN.
No rompen el hardware pero a veces pueden inutilizarlo funcionalmente hablando.

---

### Post by faktorqm on 2009-10-01
> **sergiom99 said:**
> Martin, como es esto?
Gracias!

Hola Sergio! Hace mucho que nos vemos. Vas a venir a la RP no???

Tenes que tocar el archivo /etc/security/limits.conf, aca te pego el contenido del archivo.

```

# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file

```

Te doy un ejemplo rapido, para limitar el numero de procesos al usuario "faktorqm" en tu sistema, escribis en el archivo:

faktorqm hard nproc 40

y luego tenes que reiniciar (ya se que es la opcion menos feliz, pero no encontre en ningun lado como se hace sin reiniciar :( )
asi que si lo encontras te agradezco :D

si queres guias sobre hardening de servidores tengo varias, aunque si mal no recuerdo vos usas mas linea RH/CentOS verdad?

Abrazo!

---

### Post by sergiom99 on 2009-10-03
Gracias Martín!
Lo voy a tener en cuenta.
[OT]
Hace un tiempo que no voy a los eventos porque siempre me caen los fines de semana antes de las fechas de finales, y como siempre llego justo justo con el tiempo me los tengo que perder.
Me habia anotado desde el primer dia para el U-Day pero despues me tuve que borrar, a tiempo para hacerle lugar a algunos que seguramente habran desertado sin borrarse. :-)
Espero que pueda ir a esta RP.[/OT]

Saludos!

---

### Post by sartrejp on 2009-10-04
Por ahí es muy básico lo que digo, pero los virus en Windows generalmente vienen unidos o disfrazados con otro archivo o programa (ni se imaginan cuantas veces mi hermana habrá bajado wallpapers .exe) y el usuario lo ejecuta sin saberlo.
Ahora bien, en linux mientras uno revise lo que instala no hay problema, pero podría darse que alguien con mala leche subiera por ejemplo un script para cualquier cosa y le pusiera instrucciones dañinas en el medio. El que se pusiera a leer el código se daría cuenta y de seguro lo denunciaría, pero el usuario nuevo, probablemente "copie y pegue" las instrucciones, le de permiso de ejecución y lo ejecute.
No se podría hacer algo así? por medio de bash, python o perl y darle instrucciones para que se envíe a todos los contactos de evolution, o solo haga daño en la pc?

---

### Post by rubioo on 2009-10-04
Supongo que se puede hacer, pero para que pueda hacerle mas daño a tu PC tendria que ejecutarse como root.

---

