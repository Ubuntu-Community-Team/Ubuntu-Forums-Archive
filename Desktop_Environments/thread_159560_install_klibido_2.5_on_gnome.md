---
title: "install klibido 2.5 on gnome ?"
date: 2006-04-13
forum: Desktop Environments
---

### Post by djpate on 2006-04-13
hello all,

I tryed to update my klibido Version from 2.3 to 2.5 so i updated my repo with the one given on klibido web site.it does find the 2.5 but he is missing 3 packets to install it.
```

djpate@pepette:~/Desktop/klibido-0.2.5$ sudo apt-get install klibido
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.

Puisque vous n'avez demandé qu'une seule opération, le paquet n'est
probablement pas installable et vous devriez envoyer un rapport de bogue.
L'information suivante devrait vous aider à résoudre la situation :

Les paquets suivants contiennent des dépendances non satisfaites :
  klibido: Dépend: kdelibs4 (>= 4:3.3.2-6.2) mais il n'est pas installable
           Dépend: libdb4.3++ mais il n'est pas installable
           Dépend: libqt3c102-mt (>= 3:3.3.4) mais il n'est pas installable
E: Paquets défectueux
djpate@pepette:~/Desktop/klibido-0.2.5$

```
how can i install this since i'm on gnome and not kde ?
thanks for your help

---

### Post by Sef on 2006-04-13
> how can i install this since i'm on gnome and not kde ?

The back end is the same for Gnome and KDE.  I'd google to try to find them.  [www.google.com/lunux](www.google.com/lunux)

---

### Post by bsmith1051 on 2006-04-25
the website says that the package doesn't work on Ubuntu,
  [http://klibido.sourceforge.net/#_download](http://klibido.sourceforge.net/#_download)

Instead it tells you to build the package.  I've been unable to do this in the past (I'm probably just missing the compiler?).  I emailed the guy listed as the maintainer of the 0.2.3 package, asking him if he could update it to 0.2.5.

---

