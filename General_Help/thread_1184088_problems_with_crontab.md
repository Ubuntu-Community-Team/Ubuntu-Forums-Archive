---
title: "problems with crontab"
date: 2009-06-10
forum: General Help
---

### Post by ferrcho09 on 2009-06-10
Hello.
How can I change the amount of memory that uses crontab to run on ubuntu 8.04 server?

I´m having several problems executing  tasks that last longer than 1 hour.

---

### Post by blueridgedog on 2009-06-10
Can you post the crontab entries?  What happens when you run them manually?

If you want to free up system processing time, you can run your scheduled commands via the nice command:

```
SYNOPSIS
       nice [OPTION] [COMMAND [ARG]...]

DESCRIPTION
       Run  COMMAND  with an adjusted niceness, which affects process schedul&#8208;
       ing.  With no COMMAND, print the current  niceness.   Nicenesses  range
       from -20 (most favorable scheduling) to 19 (least favorable).

```

---

### Post by ferrcho09 on 2009-06-11
I try using AT and with this option the process are succesfull... but if I use crontab, several tasks not working

Example: 12 00  * * * /empresa/importadorS
              importadorS --> ################################## cargue de empresa########################################
#php -f /var/www/folder/***/procesos/cargaS.php root postgres database localhost > /tmp/log_S.log
#php -f /var/www/folder/***/procesos/subecodmaquinaS.php root postgres database localhost 1
echo "inicio procesos de cargue" >/tmp/log_S.log
date >> /tmp/log_S.log
psql bd -c "UPDATE  software set estado='C', estadotemp=estado where nombrebd='database';";
echo "inicio carga maestros EMPRESA" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/cargamaestro_EMP.php root postgres database localhost 1
echo "inicio carga maestros INDEPENDIENTES" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/cargamaestro_IND.php root postgres database localhost 1
echo "inicio carga maestros UPC" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/cargamaestro_UPC.php root postgres database localhost 1
echo "inicio borraindices docdeu" >>/tmp/log_S.log
date >> /tmp/log_S.log
psql database -f /database/borraindexdocdeu.sql
echo "inicio carga empleadores" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/cargaS_EMP.php root postgres database localhost
echo "inicio carga UPC subebaje" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/cargaS_UPC_subebaja.php root postgres database localhost 1
echo "inicio carga UPC" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/cargaS_UPC.php root postgres database localhost
echo "inicio carga INDEPENDIENTE subebaje" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/cargaS_INDsubebaje.php root postgres database localhost 1
echo "inicio carga INDEPENDIENTE" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/cargaS_IND.php root postgres database localhost

echo "INICIO CALCULOSS" >>/tmp/log_S.log
date >> /tmp/log_S.log
php -f /var/www/folder/***/procesos/calculoS.php root postgres database localhost

echo "inicio subida indices" >>/tmp/log_S.log
date >> /tmp/log_S.log
psql database -f /database/creaindexdocdeu.sql

---

