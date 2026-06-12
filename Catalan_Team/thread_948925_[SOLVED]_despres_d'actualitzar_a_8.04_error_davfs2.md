---
title: "[SOLVED] despres d'actualitzar a 8.04_error davfs2"
date: 2008-10-15
forum: Catalan Team
---

### Post by abosch on 2008-10-15
Tenia pendent l'actualizació a 8.04 i aquesta tarda l'he feta però amb algun contratemps. M'ha quedat atrapada amb el paquet d'idioma que he pogut solucionar [amb l'ajuda]("http://ubuntuforums.org/showthread.php?t=892519&highlight=problem+en+actualitzar+versio") 

 però ha quedat un error 

> Error were encountered while processing

davfs2

No n'hi he fet cas i ara que intentava de baixar algun paquet que em falta per l'avisador de l'evolution m'ha tornat a saltar l'avís d'error.

```
abosch@abb-portatil:~$ sudo dpkg --configure -a
[sudo] password for abosch: 
S'està configurant davfs2 (1.2.1-3ubuntu1) ...
chmod: no s’ha pogut accedir a «/var/run/mount.davfs»: No such file or directory
dpkg: s'ha produït un error en processar davfs2 (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 1
S'han trobat errors en processar:
 davfs2
abosch@abb-portatil:~$ 

```



No sé per on anar, que em podrieu donar un de mà ?

gràcies

---

### Post by _DarkEagle_ on 2008-10-15
bé .. si no el fas anar (montes directoris webdav ?) pots desinstalar el paquet ...

prova a fer un:

 dpkg -P davfs2

o potser un:

apt-get remove davfs2

Salut !

---

### Post by papapep on 2008-10-15
Doncs no sembla una cosa especialment nova:

[https://bugs.launchpad.net/ubuntu/+source/davfs2/+bug/258813](https://bugs.launchpad.net/ubuntu/+source/davfs2/+bug/258813)

però, per tant, no sembla que preocupi gaire als desenvolupadors. Ni tans sols han decidit quin grau d'importància té...

Jo provaria a fer un 

```
apt-get -f install
```

i un

```
apt-get configure -a
```

a veure si sona la campana i es posa a to.

Si no va, doncs provaria a esborrar el davfs2 aquest.

---

### Post by abosch on 2008-10-15
Després de provar el ```
apt-get -f install
``` continuava donant el missatge, de manera que l'he eliminat directament.

gràcies :)

---

