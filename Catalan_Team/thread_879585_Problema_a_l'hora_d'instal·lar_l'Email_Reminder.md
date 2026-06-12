---
title: "Problema a l'hora d'instal·lar l'Email Reminder"
date: 2008-08-04
forum: Catalan Team
---

### Post by lo gambusí on 2008-08-04
Salut!!

Estic instal·lant l'email reminder, que he conegut arran [este]("http://ubuntulife.wordpress.com/2008/08/04/email-reminder-recuerda-tus-citas-y-eventos-enviandote-un-correo/") article.

Em dóna, però, este missatge d'error:> Err [http://ftp.uni-muenster.de](http://ftp.uni-muenster.de) hardy/universe libnet-domain-tld-perl 1.65-2
  403 Forbidden
Err [http://ftp.uni-muenster.de](http://ftp.uni-muenster.de) hardy/main libxml-perl 0.08-1
  403 Forbidden
No s'ha pogut obtenir [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/pool/universe/libn/libnet-domain-tld-perl/libnet-domain-tld-perl_1.65-2_all.deb](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/pool/universe/libn/libnet-domain-tld-perl/libnet-domain-tld-perl_1.65-2_all.deb)  403 Forbidden
No s'ha pogut obtenir [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/pool/main/libx/libxml-perl/libxml-perl_0.08-1_all.deb](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/pool/main/libx/libxml-perl/libxml-perl_0.08-1_all.deb)  403 Forbidden
E: No es poden descarregar alguns arxius, potser executant apt-get update o intenteu-ho amb --fix-missing.


Faig l'update i això del fix missing i en l'update no fa res i en lo fix missing em diu que > Err [http://ftp.uni-muenster.de](http://ftp.uni-muenster.de) hardy/universe libnet-domain-tld-perl 1.65-2
  403 Forbidden
Err [http://ftp.uni-muenster.de](http://ftp.uni-muenster.de) hardy/main libxml-perl 0.08-1
  403 Forbidden
No s'ha pogut obtenir [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/pool/universe/libn/libnet-domain-tld-perl/libnet-domain-tld-perl_1.65-2_all.deb](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/pool/universe/libn/libnet-domain-tld-perl/libnet-domain-tld-perl_1.65-2_all.deb)  403 Forbidden
No s'ha pogut obtenir [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/pool/main/libx/libxml-perl/libxml-perl_0.08-1_all.deb](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/pool/main/libx/libxml-perl/libxml-perl_0.08-1_all.deb)  403 Forbidden
E: No es poden descarregar alguns arxius, potser executant apt-get update o intenteu-ho amb --fix-missing.


Alguna proposta?

gràcies!!

---

### Post by papapep on 2008-08-04
Torna-ho a provar al cap d'una estona, o canvia de repositoris.

---

### Post by lo gambusí on 2008-08-04
Per canviar els repositoris edito lo sources.list?

---

### Post by papapep on 2008-08-04
> Per canviar els repositoris edito lo sources.list? 

Exacte :-)

---

### Post by lo gambusí on 2008-08-05
mmm no acabo de vore-ho clar... i ans de tocar alguna cosa que no haigue de tocar, preferixo preguntar-ho.

què hauria d'editar, aquí?
> deb [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/) hardy universe restricted main multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse
deb-src [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main 

---

### Post by papapep on 2008-08-05
Doncs hauries de saber quin repositori vols posar, i canviar el [http://ftp.uni-muenster.de/pub/mirro...tu.com/ubuntu/](http://ftp.uni-muenster.de/pub/mirro...tu.com/ubuntu/) a totes les línies que surti pel que tu vulguis.

Jo tinc posat, és només un exemple, [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

Podries provar aquest.

---

### Post by lo gambusí on 2008-08-05
mmm però ara me diu que > E: No s'ha pogut trobar el paquet email-reminder
 (?!)

---

### Post by papapep on 2008-08-05
Doncs bé que hi és...: [http://packages.ubuntu.com/hardy/email-reminder](http://packages.ubuntu.com/hardy/email-reminder)

Enganxa un altre cop el sources.list, si us plau.

---

### Post by lo gambusí on 2008-08-05
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe restricted main multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse
deb-src [http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/](http://ftp.uni-muenster.de/pub/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main .

---

### Post by papapep on 2008-08-05
....l'hauria de trobar....

Ja has fet un "sudo aptitude update" després de canviar el sources.list?? no dóna cap altre error, a banda del que has posat??

Si fas un "sudo apt-cache show email-reminder" què et diu?

---

### Post by lo gambusí on 2008-08-05
aix, sóc un desastre... no havia fet l'aptitude update.

mil disculpes!!

salut, i gràcies, papapep!! :D

---

### Post by lo gambusí on 2008-08-05
sento fer-me pesat... però un cop instal·lat se'm plantegen nous dubtes.

la guia em diu > Cuando instalas la aplicacion, se va guardando un fichero .email-reminders en tu carpeta home, donde se van guardando los eventos creados. La aplicacion hace uso de cron internamente para enviar los correos (cron es un demonio para ejecutar tareas programadas). Para que se puedan enviar los correos correctamente antes como root edita este fichero:

/etc/email-reminder.conf

y dale permisos de lecturas a todos
chmod a+r email-reminder.conf

Això simplement ho faig copiant esta frase al final de l'arxiu? Perquè després em diu... > Tendras que indicar en ese fichero la IP de tu servidor de correo saliente, y el usuario y password de acceso al servidor SMTP.:?

---

### Post by papapep on 2008-08-05
> y dale permisos de lecturas a todos
chmod a+r email-reminder.conf 

el que sembla és que et digui que li donis permisos de lectura al fitxer email-reminder.conf. De ser així, et caldrà executar la ordre "tal-qual" a un terminal (i dins el directori on és el fitxer, clar..o donar-li el camí sencer a la ordre).
Torna-t'ho a llegir tres o quatre (o cinc) cops per entendre ben bé què vol dir...

En tot cas, amb el que dius després:

> Tendras que indicar en ese fichero la IP de tu servidor de correo saliente, y el usuario y password de acceso al servidor SMTP. 

El que estaràs fent és deixar el teu usuari i contrasenya del servidor smtp en clar a l'accés de qualsevol (chmod a+r)...el qual no és gens aconsellable.

---

### Post by tanreb20 on 2008-08-05
El tema és.....

On trobo jo el usuari i la password del servidor i la IP?

---

### Post by papapep on 2008-08-06
> On trobo jo el usuari i la password del servidor i la IP? 

....tu has de saber el teu usuari i contrasenya del teu compte de correu. Sinó com configures el compte als clients de correu o com hi accedeixes per web??

Respecte la ip passa el mateix. Si el teu servidor és, p. ex. smtp.google.com, fent-li un ping veuràs la seva ip. 

```
papapep@awacs:~$ ping smtp.google.com
PING smtp1.google.com (**209.85.237.25**) 56(84) bytes of data.

```



Però és molt probable que ficant el [FQDN]("http://es.wikipedia.org/wiki/FQDN") (smtp.google.com), ja que els servidors de DNS en faran la conversió.

---

