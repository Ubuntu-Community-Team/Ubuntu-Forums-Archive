---
title: "xorg-common error after updating"
date: 2005-10-17
forum: Desktop Environments
---

### Post by djkork on 2005-10-17
I had upgraded to Breezy from hoary 2 days ago.
Now i have received a message from updates-notifier saying that i have new updates to install. When i've tried to install the updates i've received next message...

dpkg: error processing xorg-common (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
root@nachopc:/ # Errors were encountered while processing:
 xorg-common


i get same message always that i do " apt-get -f install"

---

### Post by djkork on 2005-10-17
and if i try to do  sudo apt-get -f install --reinstall xorg-common

i get another error:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Tal vez quiera ejecutar `apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
  libpango1.0-dev: Depende: libpango1.0-0 (= 1.8.1-0ubuntu2) pero 1.10.1-0ubuntu1 va a ser instalado
  libsm6: Depende: x-common pero no va a instalarse
  libxau6: Depende: x-common pero no va a instalarse
  libxdmcp6: Depende: x-common pero no va a instalarse
  libxext-dev: Depende: libxext6 (= 6.8.2-10.1) pero 1:6.4.3-3 va a ser instalado
  libxext6: Depende: x-common pero no va a instalarse
  libxft-dev: Depende: libxft2 (= 2.1.2-6ubuntu1) pero 2.1.7-1ubuntu5 va a ser instalado
  libxi-dev: Depende: libxi6 (= 6.8.2-10.1) pero 1:1.3.0-2 va a ser instalado
  libxi6: Depende: x-common pero no va a instalarse
  libxkbfile-dev: Depende: libxkbfile1 (= 6.8.2-10.1) pero 7.0.0-3 va a ser instalado
  libxkbfile1: Depende: x-common pero no va a instalarse
  libxrender-dev: Depende: libxrender1 (= 0.9.0-0ubuntu4) pero 1:0.9.0-1 va a ser instalado
  render-dev: Depende: x11proto-render-dev pero no va a instalarse
  x-dev: Depende: x11proto-core-dev pero no va a instalarse
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especifique una solución).

---

### Post by djkork on 2005-10-19
I've solved it...
The problem was that i've added the rareware's repository to install gcdmaster.... so apt-get become mad with dependencies....
1)I've removed rareware's repository
2) removed all packages from rareware's
3) apt-get -f install
4) installed all broken/deleted packages from breezy

:razz:

---

