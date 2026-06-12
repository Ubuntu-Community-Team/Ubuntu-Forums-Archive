---
title: "[SOLVED] Correu-e/Calendari/Contactes de Google a Thunderbird"
date: 2008-02-13
forum: Catalan Team
---

### Post by jcampos on 2008-02-13
[COLOR="DarkOrange"]**Avantatges**[/COLOR]
[LIST]
[*]Accés a les dades personals des de qualsevol '''**punt web**'''
[*]Accés a les dades personals amb un '''**client local**''' (normalment tenen '''**més possibilitats**''' i són més '''**ràpids**''')
[*]Accés a les dades personals '''**sense connexió a la xarxa**''' (tot es duplica localment)
[*]Podeu fer '''**còpies de seguretat**''' de les vostres dades personals en xarxa
[*]Podeu usar més d'un client local, i accedir sense connexió (ex. '''**accés des d'un portàtil sense internet**''')
[/LIST]


[COLOR="DarkOrange"]**Client GMail: Thunderbird (lectura/escriptura)**[/COLOR]

**Configuració**

sudo aptitude install thunderbird

thunderbird

[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)

sortiu del thunderbird, i torneu a entrar ;)

[http://dogmafobia.com/2007/11/02/accede-a-gmail-desde-thunderbird-mediante-el-protocolo-imap/](http://dogmafobia.com/2007/11/02/accede-a-gmail-desde-thunderbird-mediante-el-protocolo-imap/)
* Más configuración de Thunderbird


**Sense xarxa**

[LIST]
[*]Menu / Editar / Comptes
[LIST]
[*] del vostre compte, secció Sense connexió
[*] Escolliu quines carpetes voleu replicar localment
[/LIST]
[/LIST]


**Còpia de seguretat**

els vostres missatges estan a ~/.mozilla-thunderbird/<code>/ImapMail/...

**[COLOR="DarkOrange"]GCalendar des de Thunderbird (lectura/escriptura)[/COLOR]**

**Configuració**

[http://gcaldaemon.sourceforge.net](http://gcaldaemon.sourceforge.net)

sudo aptitude install lightning-extension lightning-extension-locale-ca

> wget -O /tmp/gcaldaemon-linux-1.0-beta16.zip [http://kent.dl.sourceforge.net/sourceforge/gcaldaemon/gcaldaemon-linux-1.0-beta16.zip](http://kent.dl.sourceforge.net/sourceforge/gcaldaemon/gcaldaemon-linux-1.0-beta16.zip)
cd /usr/local/sbin
sudo unzip /tmp/gcaldaemon-linux-1.0-beta16.zip
sudo addgroup gcaldaemon
sudo vi /etc/group
  gcaldaemon:x:1004:jcampos,...
sudo chgrp -R gcaldaemon /usr/local/sbin/GCALDaemon
sudo chmod -R g+w /usr/local/sbin/GCALDaemon
sudo chmod 755 /usr/local/sbin/GCALDaemon/bin/*.sh
xhost +
su - <vostre usuari>         # per assegurar que esteu dins el grup gcaldaemon
export DISPLAY=:0.0
/usr/local/sbin/GCALDaemon/bin/config-editor.sh
  HTTP Sync
    Google Account
      New account
        Verify
        OK
    Choose account
  Save and Exit

sudo /usr/local/sbin/GCALDaemon/bin/standalone-start.sh

thunderbird

[http://gcaldaemon.sourceforge.net/usage.html#online](http://gcaldaemon.sourceforge.net/usage.html#online)

pareu el procés standalone-start.sh que havieu engegat, anem a instal·lar-lo al sistema "init"

sudo vi /etc/init.d/gcaldaemon 
>  #!/bin/sh
 
 GCAL_PATH=/usr/local/sbin/GCALDaemon/bin/
 GCAL_CMD=standalone-start.sh
 
 case $1 in
 
   start)
 
      $GCAL_PATH/$GCAL_CMD &
   ;;
 
   stop)
 
      GCAL_PID=`ps ax | grep 'org.gcaldaemon.standalone.Main' | grep -v grep | awk '{ print $1; }'`
      kill -9 $GCAL_PID
 
   ;;
 
   restart|reload)
 
      $0 stop
      $0 start
 
   ;;
 
 esac



sudo chmod a+x /etc/init.d/gcaldaemon

sudo update-rc.d gcaldaemon multiuser

sudo invoke-rc.d gcaldaemon restart


sudo vi /usr/local/sbin/GCALDaemon/conf/gcal-daemon.cfg

  http.allowed.addresses=127.0.0.1

sudo invoke-rc.d gcaldaemon restart



**Sense connexió**

El GCalDaemon local ja dóna aquets servei.


**Còpies de seguretat**

es guarden a: /usr/local/sbin/GCALDaemon/work/backup

**[COLOR="DarkOrange"]GContacts des del Thunderbird (lectura)[/COLOR]**

**Configuració**

NOTE: No m'ha funcionat amb icedtea-java7-jre; he hagut d'instal·lar el sun-java6-jre.

[http://gcaldaemon.sourceforge.net/usage4.html](http://gcaldaemon.sourceforge.net/usage4.html)

sudo /usr/local/sbin/GCALDaemon/bin/password-encoder.sh

afegeix la clau al següent fitxer:

sudo vi /usr/local/sbin/GCALDaemon/conf/gcal-daemon.cfg

  ldap.enabled=true
  ldap.google.username=(el de gmail)
  ldap.google.password=(la que acabeu de generar)
  ldap.vcard.version=3.0
  ldap.allowed.hostnames=localhost

sudo invoke-rc.d gcaldaemon restart

thunderbird

Menu / Preferències / Redacció / Adreçament / Cercar a un directori / GMail

potser us va bé això per importar les vostres dades: [http://labs.brotherli.ch/vcfconvert/](http://labs.brotherli.ch/vcfconvert/)



**Sense connexió**

El GCalDaemon local ja dóna aquesta funcionalitat.

Tanmateix, també podeu:

# Des del gestor de contactes de Thunderbird:
#* importar els vostres contactes a la "Llibreta local" (els contactes els teniu a /usr/local/sbin/GCALDaemon/work/vcard/contacts.*)
# al menú Edició / Preferències / Redacció / Adreçament 
#* marqueu també la "LLibreta local"

**Còpies de seguretat**

podeu copiar els fitxers que teniu a: /usr/local/sbin/GCALDaemon/work/vcard/contacts.*

---

### Post by CarlesOriol on 2008-02-13
Eps.... has entrat a sac!!!!

El missatge que escrius vol respondre a l'altre consulta que hi ha del correu?

Au passa pel fil de benvinguda i explica'ns qui ets i on amagaves tota aquesta energia. :-)

---

### Post by SiscoGarcia on 2008-02-13
Jo també anava a preguntar alguna cosa semblant al Carles. No sé si té a veure amb el [fil del correu]("http://ubuntuforums.org/showthread.php?t=695081") o què, però ho trobo potser més adient per penjar al [wiki ]("https://wiki.ubuntu.com/CatalanTeam/Recursos")com una guia, no?

---

### Post by jcampos on 2008-02-17
Hola!

Tal i com comentàveu, ja m'he presentat:

[http://ubuntuforums.org/showpost.php?p=4347448&postcount=60](http://ubuntuforums.org/showpost.php?p=4347448&postcount=60)

Aprofito per a saludar-vos ;)


A part heu esmentat la possibilitat de posar-ho al wiki. Tan mateix, sembla que el sistema de login no és el mateix que el d'aquí els fòrums, oi? Caldria que em donés d'alta al Launchpad per a poder afegir la pàgina, és així? Tampoc no acabo de veure on afegir la pàgina exactament, jo simplement l'enllaçaria al final de la llista que hi ha amb el nom "Manuals i pàgines de referència en català al voltant del programari lliure"...

jor;)i

---

