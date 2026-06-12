---
title: "Pokemon Online"
date: 2011-06-22
forum: Gaming &amp; Leisure
---

### Post by brainard52 on 2011-06-22
I followed all the instructions found [HERE]("http://pokemon-online.eu/forums/showthread.php?509-How-to-install-Pokemon-Online-%28completely-step-by-step%29-linux"), but when I started the binary, it did absolutely nothing. no response from me even clicking the icon. any ideas?

---

### Post by Perfect Storm on 2011-06-22
> **brainard52 said:**
> I followed all the instructions found [HERE]("http://pokemon-online.eu/forums/showthread.php?509-How-to-install-Pokemon-Online-%28completely-step-by-step%29-linux"), but when I started the binary, it did absolutely nothing. no response from me even clicking the icon. any ideas?

Launch it from the terminal and see what it says.

---

### Post by brainard52 on 2011-06-22
well, i tried a different route... I decided to compile the source, which is what the people in the forums recommended. I am using the instructions found [HERE]("http://pokemon-online.eu/forums/showthread.php?6953-How-to-install-Pokemon-Online-to-Linux-Ubuntu"), and there was a problem with building the teambuilder file in QT creator. Here's the compile output i get when i try to build it. 
```
 p, li { white-space: pre-wrap; } Running build steps for project Teambuilder...
 [COLOR=#0000ff]Configuration unchanged, skipping QMake step.[/COLOR]
 [COLOR=#0000ff]Starting: /usr/bin/make -w[/COLOR] 
 make: Entering directory `/home/landon/pogeymon-online/src/Teambuilder'
 g++ -c -pipe -g -Wall -W -D_REENTRANT -DQT_PHONON_LIB -DQT_XML_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4/phonon -I/usr/include/qt4 -I/usr/include/qt4/phonon_compat -I. -I. -o client.o client.cpp
 [COLOR=#ff0000]In file included from battlewindow.h:7,[/COLOR]
 [COLOR=#ff0000]from client.cpp:5:[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:8:32: error: phonon/mediaobject.h: No such file or directory[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:9:32: error: phonon/audiooutput.h: No such file or directory[/COLOR]
 [COLOR=#ff0000]In file included from battlewindow.h:7,[/COLOR]
 [COLOR=#ff0000]from client.cpp:5:[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:248: error: ‘Phonon’ has not been declared[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:248: error: expected ‘,’ or ‘...’ before ‘newState’[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:268: error: ‘Phonon’ has not been declared[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:268: error: ISO C++ forbids declaration of ‘AudioOutput’ with no type[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:268: error: expected ‘;’ before ‘*’ token[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:270: error: ‘Phonon’ has not been declared[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:270: error: ISO C++ forbids declaration of ‘MediaObject’ with no type[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:270: error: expected ‘;’ before ‘*’ token[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:274: error: ‘Phonon’ has not been declared[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:274: error: ISO C++ forbids declaration of ‘AudioOutput’ with no type[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:274: error: expected ‘;’ before ‘*’ token[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:276: error: ‘Phonon’ has not been declared[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:276: error: ISO C++ forbids declaration of ‘MediaObject’ with no type[/COLOR]
 [COLOR=#ff0000]basebattlewindow.h:276: error: expected ‘;’ before ‘*’ token[/COLOR]
 make: Leaving directory `/home/landon/pogeymon-online/src/Teambuilder'
 [COLOR=#ff0000]make: *** [client.o] Error 1[/COLOR]
 [COLOR=#ff0000]Exited with code 2.[/COLOR]
 [COLOR=#ff0000]Error while building project Teambuilder[/COLOR]
 [COLOR=#ff0000]When executing build step 'Make'[/COLOR]

```[HERE]("http://sourceforge.net/projects/pogeymon-online/develop")'s the site to get the git command really quickly.

---

### Post by Perfect Storm on 2011-06-22
>  basebattlewindow.h:8:32: error: phonon/mediaobject.h: No such file or directory

requires libphonon-dev

---

### Post by brainard52 on 2011-06-22
alrighty,i thought i installed it, but apparently not.

EDIT

Well, I got qtphonon-dev4, but when i started building again, i got this for teambuilder

```
 p, li { white-space: pre-wrap; } Running build steps for project Teambuilder...
 [COLOR=#0000ff]Configuration unchanged, skipping QMake step.[/COLOR]
 [COLOR=#0000ff]Starting: /usr/bin/make -w[/COLOR] 
 make: Entering directory `/home/landon/pogeymon-online/src/Teambuilder'
 g++ -o ../../bin/Pokemon-Online main.o teambuilder.o advanced.o menu.o mainwindow.o network.o dockinterface.o client.o analyze.o serverchoice.o challenge.o battlewindow.o pmwindow.o controlpanel.o basebattlewindow.o box.o ranking.o pokedex.o pluginmanager.o channel.o tierstruct.o theme.o rearrangewindow.o moc_teambuilder.o moc_advanced.o moc_menu.o moc_mainwindow.o moc_otherwidgets.o moc_network.o moc_dockinterface.o moc_client.o moc_analyze.o moc_serverchoice.o moc_challenge.o moc_battlewindow.o moc_pmwindow.o moc_controlpanel.o moc_basebattlewindow.o moc_box.o moc_ranking.o moc_pokedex.o moc_pluginmanager.o moc_channel.o -L/usr/lib -L../../bin -lpokemonlib -lutilities -lphonon -lQtXml -lQtGui -lQtNetwork -lQtCore -lpthread
 [COLOR=#ff0000]/usr/bin/ld: cannot find -lpokemonlib[/COLOR]
 [COLOR=#ff0000]collect2: ld returned 1 exit status[/COLOR]
 [COLOR=#ff0000]make: *** [../../bin/Pokemon-Online] Error 1[/COLOR]
 make: Leaving directory `/home/landon/pogeymon-online/src/Teambuilder'
 [COLOR=#ff0000]Exited with code 2.[/COLOR]
 [COLOR=#ff0000]Error while building project Teambuilder[/COLOR]
 [COLOR=#ff0000]When executing build step 'Make'[/COLOR]

```


and this for pokemoninfo
```

p, li { white-space: pre-wrap; }
Running build steps for project PokemonInfo...
 [COLOR=#0000ff]Configuration unchanged, skipping QMake step.[/COLOR]
 [COLOR=#0000ff]Starting: /usr/bin/make -w[/COLOR] 
 make: Entering directory `/home/landon/pogeymon-online/src/PokemonInfo'
 rm -f libpokemonlib.so.1.0.0 libpokemonlib.so libpokemonlib.so.1 libpokemonlib.so.1.0
 g++ -shared -Wl,-soname,libpokemonlib.so.1 -o libpokemonlib.so.1.0.0 pokemonstructs.o pokemoninfo.o networkstructs.o movesetchecker.o battlestructs.o teamsaver.o moc_teamsaver.o -L/usr/lib -L../../bin -lutilities -lzip -lQtXml -lQtGui -lQtCore -lpthread
 [COLOR=#ff0000]/usr/bin/ld: cannot find -lzip[/COLOR]
 [COLOR=#ff0000]collect2: ld returned 1 exit status[/COLOR]
 make: Leaving directory `/home/landon/pogeymon-online/src/PokemonInfo'
 [COLOR=#ff0000]make: *** [../../bin/libpokemonlib.so.1.0.0] Error 1[/COLOR]
 [COLOR=#ff0000]Exited with code 2.[/COLOR]
 [COLOR=#ff0000]Error while building project PokemonInfo[/COLOR]
 [COLOR=#ff0000]When executing build step 'Make'[/COLOR]

```[COLOR=#ff0000]


[/COLOR]I think the teambuilder error is because of pokemoninfo not building correctly. what is -lzip?

---

### Post by Perfect Storm on 2011-06-22
The first one:
>  /usr/bin/ld: cannot find -lpokemonlib
It can't find a pokemon lib - so you need to compile the libs first.




>  /usr/bin/ld: cannot find -lzip

Install libzip-dev

---

### Post by brainard52 on 2011-06-22
ah, ty. it built correctly. I'm going to leave this topic open JIC something else goes wrong.

---

