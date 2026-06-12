---
title: "error activar clamav-daemon.service"
date: 2020-07-14
forum: Centroamerica Team
---

### Post by franvalles on 2020-07-14
Hola, tengo un error a la hora de activar el servicio.
Por lo que he podido leer el problema esta en que no descarga el fichero daily.cvd
He querido entender que algno lo descarga a mano y lo incluye en la carpeta del error.

¿Alguien puede ayudarme?
Utilizo Lubuntu VERSION="18.04.4 LTS (Bionic Beaver) 32bits porque es un portatil de 12 años y con lubuntu funciona aun mas o menos bien.

gracias!!

```
 clamav-daemon.service - Clam AntiVirus userspace daemon
   Loaded: loaded (/lib/systemd/system/clamav-daemon.service; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/clamav-daemon.service.d
           &#9492;&#9472;extend.conf
   Active: inactive (dead)
Condition: start condition failed at Tue 2020-07-14 16:13:38 CEST; 1min 33s ago
           &#9492;&#9472; ConditionPathExistsGlob=/var/lib/clamav/daily.{c[vl]d,inc} was not met
     Docs: man:clamd(8)
           man:clamd.conf(5)
           [https://www.clamav.net/documents/](https://www.clamav.net/documents/)

```

---

### Post by SeijiSensei on 2020-07-14
You're missing the database of virus signatures.  Run
```
sudo freshclam
```

---

### Post by franvalles on 2020-08-11
No pude responder porque no vi notificación.
Gracias

sudo freshclam ya lo he probado varias veces. Incluso a desinstalar todo y reinstalar otra vez.

> clamav-daemon.service - Clam AntiVirus userspace daemon
   Loaded: loaded (/lib/systemd/system/clamav-daemon.service; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/clamav-daemon.service.d
           &#9492;&#9472;extend.conf
   Active: inactive (dead)
Condition: start condition failed at Tue 2020-08-11 17:15:59 CEST; 7s ago
           &#9492;&#9472; ConditionPathExistsGlob=/var/lib/clamav/daily.{c[vl]d,inc} was not met
     Docs: man:clamd(8)
           man:clamd.conf(5)



Creo que el problema es este
> ConditionPathExistsGlob=/var/lib/clamav/daily.{c[vl]d,inc} was not met
pero no se solucionarlo.

Gracias

---

### Post by franvalles on 2020-08-11
SOLUCIONADO
Descargue daily.cvd y main.cvd tal y como dice esta pagina y lo metí en la carpeta que indica el error.
[URL="https://www.enmimaquinafunciona.com/pregunta/154576/como-importar-manualmente-el-archivo-de-definicion-de-virus-de-clamav"]
https://www.enmimaquinafunciona.com/pregunta/154576/como-importar-manualmente-el-archivo-de-definicion-de-virus-de-clamav[/URL]

---

