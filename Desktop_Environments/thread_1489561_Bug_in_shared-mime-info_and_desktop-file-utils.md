---
title: "Bug in shared-mime-info and desktop-file-utils"
date: 2010-05-21
forum: Desktop Environments
---

### Post by TUXIFI on 2010-05-21
hi,

I have a problem with aptitude when i want to install or update somthig, it say me 
> Des erreurs ont été rencontrées pendant l'exécution :
 desktop-file-utils
 shared-mime-info
E: Sub-process /usr/bin/dpkg returned an error code (1)
Échec de l'installation d'un paquet. Tentative de réparation :
Paramétrage de shared-mime-info (0.71-1ubuntu2) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n
dpkg : erreur de traitement de shared-mime-info (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 127
Paramétrage de desktop-file-utils (0.16-0ubuntu2) ...
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_malloc_n
dpkg : erreur de traitement de desktop-file-utils (--configure) :
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 127
Des erreurs ont été rencontrées pendant l'exécution :
 shared-mime-info
 desktop-file-utils
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Lecture de l'information d'état étendu      
Initialisation de l'état des paquets... Fait


 shared-mime-info and desktop-file-utils are broken.

How i can repair my system?

thanks

---

### Post by hopper333 on 2010-05-24
same here - shared-mime-info gives me this error which means that all my desktop & gnome/gtk stuff is broken.  it's a real PITA

started since I upgraded to 10.04 64-bit server from 8.04 64-bit server

anyone have any ideas on how to fix?  where is g_malloc0_n?

---

### Post by arngrimur on 2010-06-01
I have not verified this but I believe this related to libgtk and that a wrong a dependancy . Shared-mime-info wants libgtk-2.20.1-0ubuntu1 but the version that is installed as default is libgtk2.20.1-0ubuntu4 .
Try apt-get -f install to fix.

[Edit]
Does not solve the problem
[Edit]
Fixed by reinstallation and formating my old /usr/local wihich contained a different gtk version.

---

