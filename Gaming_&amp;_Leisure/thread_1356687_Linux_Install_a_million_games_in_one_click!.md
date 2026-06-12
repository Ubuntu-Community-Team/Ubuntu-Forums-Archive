---
title: "Linux: Install a million games in one click!"
date: 2009-12-16
forum: Gaming &amp; Leisure
---

### Post by Dedoimedo on 2009-12-16
Hi all,

Linux gamers, the holidays must have come early. Rejoice and rejoice doubly shall ye.

I've written an article about djl and GameStore, two extremely powerful yet simple game management utilities for Linux a-la Steam Valve in Windows, allowing you to search, browse and install hundreds of Linux games in a single mouse click.

You will love this. No nonsense, no command line, nothing. Click, install, play. Even my pet pirate parrot could do it, if it could operate the mouse.

I believe you'll enjoy this tremendously.

[http://www.dedoimedo.com/games/linux-million-games.html](http://www.dedoimedo.com/games/linux-million-games.html)


Cheers,
Dedoimedo

---

### Post by Chesnut on 2009-12-16
Woah, djl looks awesome! Great review!

---

### Post by jhetty on 2009-12-16
This looks great but I can not use tar files I do not know how is there a deb file?

---

### Post by Dedoimedo on 2009-12-16
Did you read my article/tutorial?
It explains there:


tar zxvf <archive-name>
cd <extracted-archive-dir>
chmod +x djl.sh
./djl.sh 


Very simple.

Cheers,
Dedoimedo

---

### Post by jhetty on 2009-12-16
Yes I read it but the problem is I do not know what this means 
tar zxvf <archive-name>
cd <extracted-archive-dir>
chmod +x djl.sh
./djl.sh 

I have know idea what to do with it

---

### Post by Surkow on 2009-12-16
> **jhetty said:**
> Yes I read it but the problem is I do not know what this means 
tar zxvf <archive-name>
cd <extracted-archive-dir>
chmod +x djl.sh
./djl.sh 

I have know idea what to do with it

It extracts the compressed file and makes the file "djl.sh" executable (with the help of the terminal). It's the same as double clicking the file and extracting it somewhere. You can make it executable by going to the preferences of the file. After that you can just start "djl.sh" by double clicking it.

---

### Post by Dedoimedo on 2009-12-16
It goes like this:

Example:

You downloaded a file called file100.tar.gz.
It's in your Downloads folder.

Open Terminal (Apps > Accessories > Terminal).
cd Downloads
tar zxvf file100.tar.gz
cd file100
chmod +x djl.sh
./djl.sh

Cheers,
Dedoimedo

---

### Post by jhetty on 2009-12-16
I still do not know how or what to paste it terminal I downloaded the tar to my desktop
sorry I'm a pain I just never learned how to use the terminal

---

### Post by Surkow on 2009-12-16
> **jhetty said:**
> I still do not know how or what to paste it terminal I downloaded the tar to my desktop
sorry I'm a pain I just never learned how to use the terminal

Open the terminal and paste each command (line of text) separately. If the file is saved on your desktop you can just change the directory to your "Desktop" folder ("cd ~/Desktop"). Use your tab key to make use of autocomplete. Press a few times to let the commandline guess the correct file name in the directory you are in at the moment after you typed a few letters.

I must add that you do not have to use the terminal to do all of this. Just try to do what I suggested in the previous post.

---

### Post by jhetty on 2009-12-16
i tried and this is what i got

lance@lance-desktop:~$ tar zxvf cd ~/Desktop
tar: cd: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /home/lance/Desktop: Not found in archive
tar: Exiting with failure status due to previous errors
lance@lance-desktop:~$

---

### Post by Perfect Storm on 2009-12-16
You need to hit <enter> after each command.

```
cd ~/Desktop
tar zxvf <file name.tar.gz>
cd <folder name>
chmod +x djl.sh
./djl.sh
```

---

### Post by jhetty on 2009-12-16
what I'm I doing wrong
lance@lance-desktop:~$ cd ~/Desktop
lance@lance-desktop:~/Desktop$ tar zxvf djl-1.2.20.tar.gz
djl/
djl/djl.sh
djl/djl/
djl/djl/Journal.txt
djl/djl/.eric4project/
djl/djl/.eric4project/project-apis.db
djl/djl/res/
djl/djl/res/b_oxygen.png
djl/djl/res/transp.png
djl/djl/res/quitter.png
djl/djl/res/modules_oxygen.png
djl/djl/res/winehq.png
djl/djl/res/configuration.png
djl/djl/res/txt_oxygen.png
djl/djl/res/irc_crystal.png
djl/djl/res/importer.png
djl/djl/res/echange_ui_oxygen.png
djl/djl/res/redemarre_oxygen.png
djl/djl/res/msg_oxygen.png
djl/djl/res/ajouter.png
djl/djl/res/maj_oxygen.png
djl/djl/res/configure_oxygen.png
djl/djl/res/a_propos.png
djl/djl/res/jeux_oxygen.png
djl/djl/res/actus.png
djl/djl/res/supprimer_oxygen.png
djl/djl/res/arg_oxygen.png
djl/djl/res/telech1.png
djl/djl/res/drapeaux/
djl/djl/res/drapeaux/italy.png
djl/djl/res/drapeaux/sweden.png
djl/djl/res/drapeaux/poland.png
djl/djl/res/drapeaux/espagne.png
djl/djl/res/drapeaux/france.png
djl/djl/res/drapeaux/galicia.png
djl/djl/res/drapeaux/portugal.png
djl/djl/res/drapeaux/hu.png
djl/djl/res/drapeaux/de.png
djl/djl/res/drapeaux/ru.png
djl/djl/res/drapeaux/en.png
djl/djl/res/information.png
djl/djl/res/retirer.png
djl/djl/res/maj.png
djl/djl/res/locale_oxygen.png
djl/djl/res/recherche_oxygen.png
djl/djl/res/irc_crystal_mp.png
djl/djl/gdep.py
djl/djl/djl_main.py
djl/djl/irc.py
djl/djl/variables.py
djl/djl/config.py
djl/djl/diff.py
djl/djl/libs/
djl/djl/libs/SOAPpy/
djl/djl/libs/SOAPpy/SOAPBuilder.py
djl/djl/libs/SOAPpy/wstools/
djl/djl/libs/SOAPpy/wstools/WSDLTools.py
djl/djl/libs/SOAPpy/wstools/c14n.py
djl/djl/libs/SOAPpy/wstools/test/
djl/djl/libs/SOAPpy/wstools/test/test_wstools.py
djl/djl/libs/SOAPpy/wstools/test/test_wsdl.py
djl/djl/libs/SOAPpy/wstools/test/__init__.py
djl/djl/libs/SOAPpy/wstools/test/test_t1.py
djl/djl/libs/SOAPpy/wstools/test/test_wstools_net.py
djl/djl/libs/SOAPpy/wstools/__init__.py
djl/djl/libs/SOAPpy/wstools/XMLSchema.py
djl/djl/libs/SOAPpy/wstools/XMLname.py
djl/djl/libs/SOAPpy/wstools/Utility.py
djl/djl/libs/SOAPpy/wstools/TimeoutSocket.py
djl/djl/libs/SOAPpy/wstools/Namespaces.py
djl/djl/libs/SOAPpy/wstools/logging.py
djl/djl/libs/SOAPpy/wstools/UserTuple.py
djl/djl/libs/SOAPpy/Server.py
djl/djl/libs/SOAPpy/ChangeLog
djl/djl/libs/SOAPpy/LICENSE
djl/djl/libs/SOAPpy/Client.py
djl/djl/libs/SOAPpy/version.py
djl/djl/libs/SOAPpy/__init__.py
djl/djl/libs/SOAPpy/fpconst/
djl/djl/libs/SOAPpy/fpconst/__init__.py
djl/djl/libs/SOAPpy/Parser.py
djl/djl/libs/SOAPpy/Types.py
djl/djl/libs/SOAPpy/SOAP.py
djl/djl/libs/SOAPpy/URLopener.py
djl/djl/libs/SOAPpy/Utilities.py
djl/djl/libs/SOAPpy/NS.py
djl/djl/libs/SOAPpy/README
djl/djl/libs/SOAPpy/WSDL.py
djl/djl/libs/SOAPpy/Config.py
djl/djl/libs/SOAPpy/GSIServer.py
djl/djl/libs/SOAPpy/Errors.py
djl/djl/libs/feedparser/
djl/djl/libs/feedparser/__init__.py
djl/djl/libs/irclib/
djl/djl/libs/irclib/__init__.py
djl/djl/libs/Fopen.py
djl/djl/libs/test_ws.py
djl/djl/rss.py
djl/djl/djl.py
djl/djl/configuration.py
djl/djl/installe.py
djl/djl/depot.py
djl/djl/image.png
djl/djl/ajout_jeu.py
djl/djl/interface.py
djl/djl/navigateur.py
djl/djl/icone.png
djl/djl/i18n/
djl/djl/i18n/sv_SE/
djl/djl/i18n/sv_SE/LC_MESSAGES/
djl/djl/i18n/sv_SE/LC_MESSAGES/messages.mo
djl/djl/i18n/sv_SE/LC_MESSAGES/djl.po
djl/djl/i18n/ru_RU/
djl/djl/i18n/ru_RU/LC_MESSAGES/
djl/djl/i18n/ru_RU/LC_MESSAGES/messages.mo
djl/djl/i18n/ru_RU/LC_MESSAGES/djl.po
djl/djl/i18n/pl_PL/
djl/djl/i18n/pl_PL/LC_MESSAGES/
djl/djl/i18n/pl_PL/LC_MESSAGES/messages.mo
djl/djl/i18n/pl_PL/LC_MESSAGES/djl.po
djl/djl/i18n/de_DE/
djl/djl/i18n/de_DE/LC_MESSAGES/
djl/djl/i18n/de_DE/LC_MESSAGES/messages.mo
djl/djl/i18n/de_DE/LC_MESSAGES/djl.po
djl/djl/i18n/pt_PT/
djl/djl/i18n/pt_PT/LC_MESSAGES/
djl/djl/i18n/pt_PT/LC_MESSAGES/messages.mo
djl/djl/i18n/pt_PT/LC_MESSAGES/djl.po
djl/djl/i18n/it_IT/
djl/djl/i18n/it_IT/LC_MESSAGES/
djl/djl/i18n/it_IT/LC_MESSAGES/messages.mo
djl/djl/i18n/it_IT/LC_MESSAGES/djl.po
djl/djl/i18n/es_ES/
djl/djl/i18n/es_ES/LC_MESSAGES/
djl/djl/i18n/es_ES/LC_MESSAGES/messages.mo
djl/djl/i18n/es_ES/LC_MESSAGES/djl.po
djl/djl/i18n/gl_ES/
djl/djl/i18n/gl_ES/LC_MESSAGES/
djl/djl/i18n/gl_ES/LC_MESSAGES/messages.mo
djl/djl/i18n/gl_ES/LC_MESSAGES/djl.po
djl/djl/i18n/fr_FR/
djl/djl/i18n/fr_FR/LC_MESSAGES/
djl/djl/i18n/fr_FR/LC_MESSAGES/messages.mo
djl/djl/i18n/fr_FR/LC_MESSAGES/djl.po
djl/djl/i18n/en_US/
djl/djl/i18n/en_US/LC_MESSAGES/
djl/djl/i18n/en_US/LC_MESSAGES/messages.mo
djl/djl/i18n/en_US/LC_MESSAGES/djl.po
djl/djl/i18n/hu_HU/
djl/djl/i18n/hu_HU/LC_MESSAGES/
djl/djl/i18n/hu_HU/LC_MESSAGES/messages.mo
djl/djl/i18n/hu_HU/LC_MESSAGES/djl.po
djl/djl/i18n.py
djl/djl/palette_irc.py
djl/djl/import_raccourcis.py
djl/djl/modules.py
djl/djl/Journal_en.txt
djl/webservice-src/
djl/webservice-src/djl.php
djl/webservice-src/djl.sql
djl/webservice-src/COPYING
djl/README
djl/LISEZMOI
djl/COPYING
djl/LIESMICH
lance@lance-desktop:~/Desktop$ cd games
bash: cd: games: No such file or directory
lance@lance-desktop:~/Desktop$ cd games
bash: cd: games: No such file or directory
lance@lance-desktop:~/Desktop$ cd games
lance@lance-desktop:~/Desktop/games$ chmod +x djl.sh
chmod: cannot access `djl.sh': No such file or directory
lance@lance-desktop:~/Desktop/games$ chmod +x djl.sh
chmod: cannot access `djl.sh': No such file or directory
lance@lance-desktop:~/Desktop/games$ ./djl.sh
bash: ./djl.sh: No such file or directory
lance@lance-desktop:~/Desktop/games$

---

### Post by Perfect Storm on 2009-12-16
```
cd djl
```

---

### Post by Seano911 on 2009-12-16
you need to type "cd djl" not "cd games" then you should be fine.

---

### Post by Chesnut on 2009-12-16
> **jhetty said:**
> what I'm I doing wrong
lance@lance-desktop:~$ cd ~/Desktop
lance@lance-desktop:~/Desktop$ tar zxvf djl-1.2.20.tar.gz
djl/
...
...
lance@lance-desktop:~/Desktop$ cd games
bash: cd: games: No such file or directory
lance@lance-desktop:~/Desktop$ cd games
bash: cd: games: No such file or directory
lance@lance-desktop:~/Desktop$ cd games
lance@lance-desktop:~/Desktop/games$ chmod +x djl.sh
chmod: cannot access `djl.sh': No such file or directory
lance@lance-desktop:~/Desktop/games$ chmod +x djl.sh
chmod: cannot access `djl.sh': No such file or directory
lance@lance-desktop:~/Desktop/games$ ./djl.sh
bash: ./djl.sh: No such file or directory
lance@lance-desktop:~/Desktop/games$

```
cd ~/Desktop/djl
chmod +x djl.sh
./djl.sh
```

---

### Post by Dedoimedo on 2009-12-16
lance, You're almost there!

You extracted the files correctly.
Now only you need to cd into the right directory.
Give the execution permissions and run it.

Go back to Terminal.

cd ~/Desktop/djl
Enter
chmod +x djl
Enter
./djl

And now you can enjoy it ...

Cheers,
Dedoimedo

---

### Post by jhetty on 2009-12-16
Ok here is where I'm at and can not find python-qt4 libraries in the syn pack or I should say which one to use

lance@lance-desktop:~/Desktop/djl$ ./djl.sh
Error: You must have python-qt4 libraries installed to run djl, you have to install them with your package manager
Erreur lors de l'import des librairies, vous devez installer le paquet python-qt4, merci de l'installer depuis votre gestionnaire de paquets
No module named PyQt4
lance@lance-desktop:~/Desktop/djl$

---

### Post by Perfect Storm on 2009-12-16
```
sudo apt-get install python-qt4
```

---

### Post by jhetty on 2009-12-16
Got it to work Thank You every one for helping out Lance

---

