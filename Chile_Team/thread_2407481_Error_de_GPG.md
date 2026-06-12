---
title: "Error de GPG"
date: 2018-12-04
forum: Chile Team
---

### Post by okori097 on 2018-12-04
Tengo un problema que no puedo hace muchas semanas 

codigo:

```
Ign:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty InRelease
Des:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security InRelease [65,9 kB]                 
Ign:3 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty InRelease                                      
Obj:4 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) bionic InRelease                 
Obj:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty Release                                    
Des:6 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty Release [11,9 kB]                              
Des:7 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty Release.gpg [72 B]                             
Obj:8 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) bionic InRelease                           
Ign:7 [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty Release.gpg                                    
Obj:10 [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) bionic InRelease           
Ign:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty InRelease                         
Des:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates InRelease [65,9 kB]
Obj:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports InRelease
Obj:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty Release  
Leyendo lista de paquetes... Hecho                      
W: El objetivo Sources (main/source/Sources) está configurado varias veces en /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-bionic.list:2 y /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-bionic.list:3
W: Error de GPG: [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty Release: Las siguientes firmas no fueron válidas: C47415DFF48C09645B78609416126D3A3E5C1192
E: El repositorio «[http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty Release» no está firmado.
N: No se puede actualizar de un repositorio como este de forma segura y por tanto está deshabilitado por omisión.
N: Vea la página de manual apt-secure(8) para los detalles sobre la creación de repositorios y la configuración de usuarios.
W: El objetivo Sources (main/source/Sources) está configurado varias veces en /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-bionic.list:2 y /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-bionic.list:3
```



version de kubuntu: 4.15.0-42-generic

espero su respuesta

---

