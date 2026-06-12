---
title: "Steam sous Linux par Steam4linux"
date: 2007-03-24
forum: Gaming &amp; Leisure
---

### Post by arhwebmaster on 2007-03-24
Cette instruction permet d'aidera vous à installer Steam sous Linux.
Je ne suis pas un français, alors peut-être que je mal écrive, mais j'essaye.

Faire partir à télécharger Steam4linux (télécharger-le ici: [www.steam4linux.freepages.dk](www.steam4linux.freepages.dk)) . Si vous êtes un débutant de l'utilisation de Linux, vous pouvez taper ceci dans votre terminal: «wget [http://steam4linux.freepages.dk»](http://steam4linux.freepages.dk») . 

Après ça, vous déballerez l'archive de taper: «tar xvfz steam4linux.tar.gz» .

Après l'archive est déballé, vous installerez le programme de taper: «./steam4linux/configure» . 

Lorsque l'installation est finition, fait partir l'installation de Steam .
Installer comme vous faites sous Windows.

Lorsqu'elle a installé, elle fait la mise à jour . Lorsque la mise à jour atteindra 26%, ça ce bloque. 
Voici la solution à taper dans votre terminal:

WINEPREFIX=~/.steam4linux wine "C:/Program Files/Steam/steamTmp.exe" SelfUpdate "C:/Program Files/Steam/Steam.exe" "14"

Lorsque Steam a dépassé la mise à jour, alors vous vous connectez . 

Lorsque vous vous avez connecté, peut-être qu'il demande de vous voulez installer "Gecko Engine".
Juste vous choisissez oui.

Si votre carte graphique n'a pas d'OpenGL, peut-être que vous avez besoin d'une "Emulated Desktop" . 
Vous fairez partir d'aller à la configuration de Wine . 
(Vous écrirez «WINEPREFIX=~/.steam4linux winecfg» ) .
Alors vous cliquerez: «Graphics» , choisir: «Emulate a virtual desktop» et choisir un grandeur pour la fênetre . Cliquer OK . 

Si vous n'avez pas fermé Steam, alors fairez-le maintenant, et ouvir Steam encore . 
Alors il est dans un «Emulated Desktop» .

Peut-être qu'il y a des problèmes, si vous avez le Wine 0.9.33 (un des mes amis avait des problèmes) . Alors essayer la version 0.9.32 .

Si vous avez des questions ou j'ai mal écrit, alors envoyer un courrier électronique à: «french_translator@freepages.dk» , ou sur la discussion .

---

### Post by lakersforce on 2007-03-24
I did not understand a word of what you just wrote. English please!!

---

### Post by r4ik on 2007-03-24
Parlez Anglais s'il vous plait.

---

### Post by hikaricore on 2007-03-24
> **arhwebmaster said:**
> 
This instruction allows will help you to install Steam under Linux. I am not French, then perhaps that I badly write, but I test. To make leave to download Steam4linux (to download it here: [www.steam4linux.freepages.dk)](www.steam4linux.freepages.dk)). If you are initial use of Linux, you can type this in your terminal: "wget http://steam4linux.freepages.dk". After that, you will unpack the file to type: "tar xvfz steam4linux.tar.gz". After the file is unpacked, you will install the program to type: "/steam4linux/configure". When the installation is completion, makes leave the installation Steam. To install as you make under Windows. When it installed, it makes the update. When the update reaches 26%, that this blocks. Here the solution to be typed in your terminal: WINEPREFIX=~/.steam4linux wine "C:/Program Files/Steam/steamTmp.exe" SelfUpdate "C:/Program Files/Steam/Steam.exe" "14" When Steam exceeded the update, then you connect yourselves. When you connected yourselves, perhaps that it asks you want to install "Gecko Engine". Just you choose yes. If your graphics board does not have OpenGL, perhaps that you need "Emulated Desktop". You will fairez to start from going to the configuration of Wine. (You will write "WINEPREFIX=~/.steam4linux winecfg"). Then you will click: "Graphics", to choose: "Emulate has virtual desktop" and to choose a size for the fênetre. To click OK. If you did not close Steam, then will fairez maintaining it, and to still ouvir Steam. Then it is in "Emulated Desktop". Perhaps that there are problems, if you have Wine 0.9.33 (one as of the my friends had problems). Then to test version 0.9.32. If you have questions or I badly wrote, then to send an electronic mail to: "french_translator@freepages.dk", or on the discussion.


> **lakersforce said:**
> I did not understand a word of what you just wrote. English please!!

Lakersforce, this is the year 2007 don't reply if you're too lazy to translate.

[http://babelfish.altavista.com/tr](http://babelfish.altavista.com/tr)

:P

---

### Post by r4ik on 2007-03-24
Bookmarked thanks !

---

### Post by techstop on 2007-03-25
> **hikaricore said:**
> Lakersforce, this is the year 2007 don't reply if you're too lazy to translate.

[http://babelfish.altavista.com/tr](http://babelfish.altavista.com/tr)

:P

...except the forum rules clearly state that posts should be in English....

> 10.  Please strive to communicate with other users as effectively as possible:

    * Please try to write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries that visit here and English is the common language of these forums.


[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

It was an entirely reasonable request by Lakersforce. I certainly wouldn't trust a babelfish translation when installing stuff on my system.

---

### Post by hikaricore on 2007-03-25
> _Please try to write your posts in English_ unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries that visit here and English is the common language of these forums.

Doesn't exactly say they have to be in english.

Searching around the forums I've seen hundreds of non english posts by long time and still
current community members.  Based on the fact that the OP was posting info and
_not asking for help_.  I don't really see the need for nitpicking about it.

Lake was being just a litte rude imho.

---

### Post by MonkeyBoy on 2007-03-25
Merci de ces instructions. 

J'ai projeté installer la Steam mais ne l'avais pas faite. C'était facile et indolore !:)

---

### Post by arhwebmaster on 2007-03-25
I can translate, but I've made a french version here: [http://forum.swisslinux.org/viewtopic.php?id=1614](http://forum.swisslinux.org/viewtopic.php?id=1614) (a french site) , and thought I would copy it to Ubuntuforums.org . 
I'm sorry, but I haven't seen the rule that say I shall write in english . Sorry . (There are also french persons on Ubuntuforums ;) )


Et ceci est à toi qui as compris:

De rien, monsieur . :) . Peux-tu jouer aux jeux qui sont sur Steam maintenant? Après l'utilisation de Steam4linux? :)

---

