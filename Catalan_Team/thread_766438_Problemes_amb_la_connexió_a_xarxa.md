---
title: "Problemes amb la connexió a xarxa"
date: 2008-04-25
forum: Catalan Team
---

### Post by jmaspons on 2008-04-25
Hola,
He instal·lat de nou kubuntu amb kde4 i és molt maco però no aconsegueixo conectar-me a internet.

El KnetworkManager no obre l'aplicació per configurar manualment.

També he provat amb la consola però tampoc em va. He fet

```

$ sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
$ sudo route add default gw 192.168.1.1

```

També he afegit els dns a /etc/resolv.conf. Aquest fitxer no existia i l'he creat jo. És normal?

Per si serveix d'alguna cosa informo que l'ordinador està connectat a una targeta de xarxa d'un altre ordinador amb connexió compartida i windows (no se com es configura en linux). No crec que sigui problema d'aquest últim ja que abans d'aquesta nova instal·lació funcionava bé.

Algun consell?

---

