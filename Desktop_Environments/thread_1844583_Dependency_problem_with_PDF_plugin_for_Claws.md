---
title: "Dependency problem with PDF plugin for Claws"
date: 2011-09-15
forum: Desktop Environments
---

### Post by Vinkus on 2011-09-15
Hello everybody,

I wish to install the PDF plugin for Claws mail provided by [gborzi]("http://ubuntuforums.org/member.php?u=55914") in _[this thread]("http://ubuntuforums.org/showthread.php?t=1044386")_ (the amd64 version) on an ubuntu 11.04
Unfortunately, the software library tells that there is a dependency missing: **libpoppler-glib3**
```
Dépaquetage de claws-mail-pdf-viewer (à partir de claws-mail-pdf-viewer_0.9.1-1_amd64.deb) ...
dpkg : des problèmes de dépendances empêchent la configuration de claws-mail-pdf-viewer :
 claws-mail-pdf-viewer dépend de libpoppler-glib3 ; cependant :
  Le paquet libpoppler-glib3 n'est pas installé.
dpkg : erreur de traitement de claws-mail-pdf-viewer (--install) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 claws-mail-pdf-viewer
```I used apt-get, synaptic and Google to find it but nothing worked.

Can you help me please ?

Regards

---

### Post by FormatSeize on 2011-09-15
The thread you are looking at is talking about installation of the plugins on Ubuntu Hardy, which used libpoppler-glib3. [Here](https://launchpad.net/ubuntu/natty/+source/poppler) I found that Ubuntu 11.04 uses libpoppler-glib5. If the plugin you are trying to install will only use libpoppler-glib3, I'm not sure where to go from there. But you can try to install libpoppler-glib5 and see if that will satisfy the dependency.

---

### Post by Vinkus on 2011-09-15
I found in Synaptic that I use **libpoppler-glib6** so the plugin needs libpoppler-glib3.

Do you know any pdf plugin for Claws mail which work in ubuntu 11.04 ?

---

