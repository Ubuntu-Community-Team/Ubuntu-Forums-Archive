---
title: "Dell Mini clavier QWERTY AZERTY"
date: 2009-03-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wattcast on 2009-03-21
:(Bonjour, Sur mon DeLL MINI aprés avoir effectué la derniére mise à jour de ubuntu le clavier est en QWERTY. Malgré la modification de configuration du clavier en AZERTY aprés reboot du Dell le clavier est denouveau en QWERTY. Je perds le Nord. Merci de votre aide pour resoudre l'un de mes problèmes sur Ubuntu. Je ne vois de fonction restore!!! Domage. 

Merci

---

### Post by wattcast on 2009-03-22
Merci a Lise pour les explications [http://www.paperblog.fr/1469627/](http://www.paperblog.fr/1469627/)
Modifier le fichier xorg.conf

    Attention, cette étape utilise le compte root ; celui-ci peut tout faire, donc aussi casser son système ! Agir avec prudence !

Pour accéder au fichier xorg.conf :

    * lancer un terminal via Applications > Accessoires > Terminal ;
    * saisir "gksudo nautilus", puis son mot de passe d'administration, une nouvelle fenêtre du gestionnaire de fichiers s'ouvre, on est alors dans le répertoire "root" ;
    * cliquer dans la barre latérale sur Système de fichiers puis aller dans etc > X11 ;
    * ouvrir le fichier xorg.conf. 

Mon fichier indiquait bien un clavier US :

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Il faut juste remplacer "us" par "fr". Et le clavier retrouve de nouveau sa langue !

Daniel
[Wattcast tele et radio live]("http://www.wattcast.com/")

---

