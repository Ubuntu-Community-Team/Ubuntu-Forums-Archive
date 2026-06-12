---
title: "No puedo instalar PHP en Ubuntu 20.04"
date: 2022-06-04
forum: Centroamerica Team
---

### Post by tradov75 on 2022-06-04
Buenos dias,

Soy nuevo en el uso de SO Linux y me encuentro el siguiente problema. Al intentar instalar PHP en Ubuntu 20.04 me aparece el siguiente error<

```
root@vmi:~# sudo apt install php8.1 libapache2-mod-php8.1
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libapache2-mod-php8.1 : Depends: php8.1-cli but it is not going to be installed
                         Depends: libpcre2-8-0 (>= 10.38) but 10.34-7 is to be installed
N: Ignoring file 'mariadb.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to correct problems, you have held broken packages.
```


Agradeceria cualquier consejo para solucionar el problema.

Saludos.

---

