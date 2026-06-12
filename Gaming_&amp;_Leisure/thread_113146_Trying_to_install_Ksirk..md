---
title: "Trying to install Ksirk."
date: 2006-01-05
forum: Gaming &amp; Leisure
---

### Post by kitpierce on 2006-01-05
I am trying to install the risk clone Ksirk.  I loved playing it on Linspire, but I cannot find it in any repositories.  I downloaded the source from KDE and cannot figure out how to compile.  I am an incredible noob, but I have read a ton - still no dice.  I have installed GCC, but it appears to require libkdegames-dev and I can't find that package anywhere.  I have tried ./configure, make, etc but get a painfully long error message and don't know where else to go.  Anyone have luck installing this or have any ideas as to where to turn next?  Or am I just out of luck with this particular game?

---

### Post by Zelut on 2006-01-05
Well I haven't installed that game but I can give you a few tips to try.

First, if you can't find them in the repositories I'd make sure that you've got them all activated.  In Synaptic > Settings > Repositories do you have 'universe' and 'multiverse' activated?  If not, do that & give a search for libkdegames-dev again.. 

Also, for compiling you'll probably want to make sure you've got the 'build-essential' package installed.  That makes sure you've got all the compiling tools you need.

After that I'm sure it's only potential dependency problems.. but those'd depend on your error messages.

(also make sure you're running ./configure as sudo...)

---

### Post by kitpierce on 2006-01-05
Thanks for the VERY quick reply; I am loving the community so far!  Sorry forgot to mention, I'm running Kubuntu 5.10 but I assumed the apt-get would be roughly the same.  I have installed the build-essential package and I ran the config with sudo and then ran make as both user and as sudo, but got errors with both.  I copied them below:

kit@kitslaptop:~/Desktop/ksirk$ sudo make
make  all-recursive
make[1]: Entering directory `/home/kit/Desktop/ksirk'
Making all in ksirk
make[2]: Entering directory `/home/kit/Desktop/ksirk/ksirk'
Making all in Dialogs
make[3]: Entering directory `/home/kit/Desktop/ksirk/ksirk/Dialogs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/Dialogs'
Making all in Sprites
make[3]: Entering directory `/home/kit/Desktop/ksirk/ksirk/Sprites'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/Sprites'
Making all in GameLogic
make[3]: Entering directory `/home/kit/Desktop/ksirk/ksirk/GameLogic'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/GameLogic'
Making all in SaveLoad
make[3]: Entering directory `/home/kit/Desktop/ksirk/ksirk/SaveLoad'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/SaveLoad'
Making all in skins
make[3]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins'
Making all in default
make[4]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/default'
Making all in Images
make[5]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Images'
Making all in sprites
make[6]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Images/sprites'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Images/sprites'
make[6]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Images'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Images'
make[5]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Images'
Making all in Sons
make[5]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Sons'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Sons'
Making all in Data
make[5]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Data'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/default/Data'
make[5]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/default'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/default'
make[4]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/default'
Making all in bubble
make[4]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble'
Making all in Images
make[5]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Images'
Making all in sprites
make[6]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Images/sprites'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Images/sprites'
make[6]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Images'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Images'
make[5]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Images'
Making all in Sons
make[5]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Sons'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Sons'
Making all in Data
make[5]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Data'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble/Data'
make[5]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble'
make[4]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins/bubble'
make[4]: Entering directory `/home/kit/Desktop/ksirk/ksirk/skins'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins'
make[3]: Leaving directory `/home/kit/Desktop/ksirk/ksirk/skins'
make[3]: Entering directory `/home/kit/Desktop/ksirk/ksirk'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../kgame-patch -I../ksirk -IDialogs -I../libkdegames -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT kgamewin.o -MD -MP -MF ".deps/kgamewin.Tpo" -c -o kgamewin.o kgamewin.cpp; \
then mv -f ".deps/kgamewin.Tpo" ".deps/kgamewin.Po"; else rm -f ".deps/kgamewin.Tpo"; exit 1; fi
/usr/share/qt3/include/qxml.h:224: warning: ‘class QXmlReader’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:407: warning: ‘class QXmlContentHandler’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:424: warning: ‘class QXmlErrorHandler’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:433: warning: ‘class QXmlDTDHandler’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:441: warning: ‘class QXmlEntityResolver’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:448: warning: ‘class QXmlLexicalHandler’ has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:461: warning: ‘class QXmlDeclHandler’ has virtual functions but non-virtual destructor
kgamewin.cpp:867: warning: unused parameter ‘shortcut’
kgamewin.cpp: In member function ‘bool Ksirk::KGameWindow::setupPlayers()’:
GameLogic/gameautomaton.h:231: error: ‘unsigned int Ksirk::GameLogic::GameAutomaton::setupPlayersNumberAndSkin(bool&, int&)’ is protected
kgamewin.cpp:926: error: within this context
kgamewin.cpp: In member function ‘bool Ksirk::KGameWindow::createWaitedPlayer(Q_UINT32)’:
GameLogic/gameautomaton.h:225: error: ‘void Ksirk::GameLogic::GameAutomaton::createIO(KPlayer*, KGameIO::IOMode)’ is protected
kgamewin.cpp:1082: error: within this context
GameLogic/gameautomaton.h:225: error: ‘void Ksirk::GameLogic::GameAutomaton::createIO(KPlayer*, KGameIO::IOMode)’ is protected
kgamewin.cpp:1090: error: within this context
kgamewin.cpp: In member function ‘void Ksirk::KGameWindow::addPlayer(const QString&, unsigned int, unsigned int, const QString&, bool, const QString&, unsigned int, unsigned int)’:
GameLogic/gameautomaton.h:225: error: ‘void Ksirk::GameLogic::GameAutomaton::createIO(KPlayer*, KGameIO::IOMode)’ is protected
kgamewin.cpp:2149: error: within this context
GameLogic/gameautomaton.h:225: error: ‘void Ksirk::GameLogic::GameAutomaton::createIO(KPlayer*, KGameIO::IOMode)’ is protected
kgamewin.cpp:2163: error: within this context
make[3]: *** [kgamewin.o] Error 1
make[3]: Leaving directory `/home/kit/Desktop/ksirk/ksirk'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kit/Desktop/ksirk/ksirk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kit/Desktop/ksirk'
make: *** [all] Error 2

If anybody has hints for what's next I would love them.  Also, I may be without internet for a couple days, but I hope to hammer this out soon.... Thanks again for the help in advance.

---

### Post by Perfect Storm on 2006-01-06
[QUOTE=kitpierce]I am trying to install the risk clone Ksirk.  I loved playing it on Linspire, but I cannot find it in any repositories.  I downloaded the source from KDE and cannot figure out how to compile.  I am an incredible noob, but I have read a ton - still no dice.  I have installed GCC, but it appears to require libkdegames-dev and I can't find that package anywhere.  I have tried ./configure, make, etc but get a painfully long error message and don't know where else to go.  Anyone have luck installing this or have any ideas as to where to turn next?  Or am I just out of luck with this particular game?[/QUOTE]

libkdegames-dev are availble, you might take a closer look, or make sure you have enable the right things in your sourcelist.

When installed. Grab also checkinstall


```
./configure
```

Please post the output of it if any errors shows up.
If not continue

```

make
sudo checkinstall

```

---

### Post by kitpierce on 2006-01-06
OK, I think I figured out what was happening.  I was trying to install a beta build, so I reverted to the earlier final build and now appear to successfully installed the app because I get the following message:

Done. The new package has been installed and saved to
/home/kit/ksirk/ksirk_ksirk-1.2-1_i386.deb
You can remove it from your system anytime using:
dpkg -r ksirk

But when I try to run the program I can't find it in the K menu nor will it run when I choose Run Command... ksirk.  I didn't get any error messages during the install, but can't figure out what happened.  Thank for all the help earlier!

---

### Post by Perfect Storm on 2006-01-07
Sorry, I should have told you. You need to install the ksirk.deb file you made.


```

sudo dpkg -i /home/kit/ksirk/ksirk_ksirk-1.2-1_i386.deb

```

---

