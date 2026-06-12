---
title: "Reprository problem (error on backports)"
date: 2005-10-18
forum: Desktop Environments
---

### Post by kurtkraut on 2005-10-18
When I do a **sudo aptitude update** I get this error in bold:

Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Lendo informações extendidas de estado
Inicializando estados de pacotes... Pronto
Obter:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Obter:2 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy Release.gpg [189B]
Obter:3 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports Release.gpg
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy Release
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-updates Release
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports Release
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy/main Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy/restricted Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy/main Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy/restricted Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy/universe Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy/universe Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-updates/main Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-updates/restricted Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-updates/main Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/multiverse Sources
[b]Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 82.211.81.151 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 82.211.81.151 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 82.211.81.151 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 82.211.81.151 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found [IP: 82.211.81.151 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found [IP: 82.211.81.151 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found [IP: 82.211.81.151 80]
Err [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found [IP: 82.211.81.151 80][/b]
Baixados 3B em 3s (1B/s)
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Lendo informações extendidas de estado
Inicializando estados de pacotes... Pronto
ktk@ktk4:~$

I've just uncommented the standard repositories in sources.list. Houw should I fix it ?

Thanks

---

### Post by zenodaddy on 2005-10-18
I have had the same problem with the backports, I had to remove the backports and use only the standard repositories. Each time I tried to sync the backports I recieved the same error.. any ideas? :eek:

---

### Post by leaber on 2005-10-18
i'm pretty sure the backports arent available yet....

---

### Post by Murgle on 2005-10-18
the backports will be available when development on dapper drake has begun.  they are listed default in the install so that when they exist they will be easy to access.  they should be commented out though

---

