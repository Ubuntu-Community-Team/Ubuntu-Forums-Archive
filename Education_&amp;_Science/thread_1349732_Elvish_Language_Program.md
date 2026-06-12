---
title: "Elvish Language Program"
date: 2009-12-08
forum: Education &amp; Science
---

### Post by rudeboyskunk on 2009-12-08
I have been trying to install an Elvish Language Program called "Dragon Flame" on Karmic.  The makers haven't updated it since July 2004.  It comes in a bz2 tarball.  I do the ./install.sh thing, and then it tells me I can just go to the folder in which it installs and find the executable in the bin folder, but there isn't anything in there.  I saw some errors during the make process, but I didn't really understand them.  Anybody here?

```
kimbop@kimchi:~/Downloads/dragonflame_2-0_gnulinux$ ./install.sh 

This will compile and install Dragon Flame 2.0 for GNU/Linux
Press ENTER to continue and see license... (q when ok)


Do you agree with it ?

y(Yes) - Default
n(No)
s(See again)
>y

Compile?

y(Yes) - Default
n(No)
q(Quit)
>y
WARNING: Operator=(TEMPLATE) clears variables previously set: dragonflame.pro:2
-k -C . -f ./Makefile
make: Entering directory `/home/kimbop/Downloads/dragonflame_2-0_gnulinux'
cd src && qmake src.pro -Wall -o Makefile
WARNING: Operator=(TEMPLATE) clears variables previously set: src.pro:6
cd src && make -f Makefile
make[1]: Entering directory `/home/kimbop/Downloads/dragonflame_2-0_gnulinux/src'
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o about.o about.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o centralwidget.o centralwidget.cpp
In file included from downloadbar.h:25,
                 from dfstatusbar.h:26,
                 from centralwidget.cpp:34:
/usr/include/qt3/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
In file included from centralwidget.cpp:36:
centralwidget.h: At global scope:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o dfstatusbar.o dfstatusbar.cpp
In file included from downloadbar.h:25,
                 from dfstatusbar.h:26,
                 from dfstatusbar.cpp:20:
/usr/include/qt3/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o Dico.o Dico.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o dictOnline.o dictOnline.cpp
In file included from dictOnline.h:29,
                 from dictOnline.cpp:28:
dictProtocol.h:32: error: extra qualification &#8216;DICTClient::&#8217; on member &#8216;define&#8217;
In file included from downloadbar.h:25,
                 from dictOnline.h:30,
                 from dictOnline.cpp:28:
/usr/include/qt3/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
make[1]: *** [dictOnline.o] Error 1
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o dictProtocol.o dictProtocol.cpp
In file included from dictProtocol.cpp:31:
dictProtocol.h:32: error: extra qualification &#8216;DICTClient::&#8217; on member &#8216;define&#8217;
make[1]: *** [dictProtocol.o] Error 1
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o downloadbar.o downloadbar.cpp
In file included from downloadbar.h:25,
                 from downloadbar.cpp:19:
/usr/include/qt3/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o entry.o entry.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o helpwindow.o helpwindow.cpp
In file included from helpwindow.cpp:22:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o httpCore.o httpCore.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o httpSynchronizer.o httpSynchronizer.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o listboxmanager.o listboxmanager.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o main.o main.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o mainwindow.o mainwindow.cpp
In file included from mainwindow.cpp:23:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
In file included from dictOnline.h:29,
                 from mainwindow.cpp:26:
dictProtocol.h:32: error: extra qualification &#8216;DICTClient::&#8217; on member &#8216;define&#8217;
In file included from downloadbar.h:25,
                 from dictOnline.h:30,
                 from mainwindow.cpp:26:
/usr/include/qt3/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
make[1]: *** [mainwindow.o] Error 1
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o mybrowser.o mybrowser.cpp
In file included from mybrowser.h:22,
                 from mybrowser.cpp:19:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o page.o page.cpp
In file included from page.cpp:20:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
page.cpp: In member function &#8216;void Page::goodPosition()&#8217;:
page.cpp:233: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o preferences.o preferences.cpp
preferences.cpp: In member function &#8216;void Preferences::readData()&#8217;:
preferences.cpp:141: warning: format not a string literal and no format arguments
preferences.cpp:152: warning: format not a string literal and no format arguments
preferences.cpp:164: warning: format not a string literal and no format arguments
preferences.cpp:171: warning: format not a string literal and no format arguments
preferences.cpp: In member function &#8216;void Preferences::writeData()&#8217;:
preferences.cpp:236: warning: format not a string literal and no format arguments
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o searchfield.o searchfield.cpp
In file included from searchfield.cpp:20:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o searchinterface.o searchinterface.cpp
In file included from searchinterface.cpp:20:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o sentenceline.o sentenceline.cpp
In file included from sentenceline.h:22,
                 from sentenceline.cpp:19:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o splashwindow.o splashwindow.cpp
In file included from splashwindow.cpp:22:
/usr/include/qt3/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o teng_exception.o teng_exception.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o teng_mylist.o teng_mylist.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o teng_transcription.o teng_transcription.cpp
teng_transcription.cpp: In member function &#8216;const char* CTranscription::Roman2Tengwar(const char*)&#8217;:
teng_transcription.cpp:626: error: &#8216;strlen&#8217; was not declared in this scope
teng_transcription.cpp:752: warning: suggest explicit braces to avoid ambiguous &#8216;else&#8217;
teng_transcription.cpp: In member function &#8216;const char* CTranscription::Tengwar2Roman(const char*)&#8217;:
teng_transcription.cpp:799: error: &#8216;strlen&#8217; was not declared in this scope
teng_transcription.cpp:906: warning: suggest explicit braces to avoid ambiguous &#8216;else&#8217;
teng_transcription.cpp: In member function &#8216;void CTranscription::LoadMode(const char*)&#8217;:
teng_transcription.cpp:959: warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result
make[1]: *** [teng_transcription.o] Error 1
/usr/share/qt3/bin/moc about.h -o moc_about.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_about.o moc_about.cpp
/usr/share/qt3/bin/moc centralwidget.h -o moc_centralwidget.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_centralwidget.o moc_centralwidget.cpp
In file included from moc_centralwidget.cpp:11:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
/usr/share/qt3/bin/moc dictOnline.h -o moc_dictOnline.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_dictOnline.o moc_dictOnline.cpp
In file included from dictOnline.h:29,
                 from moc_dictOnline.cpp:11:
dictProtocol.h:32: error: extra qualification &#8216;DICTClient::&#8217; on member &#8216;define&#8217;
In file included from downloadbar.h:25,
                 from dictOnline.h:30,
                 from moc_dictOnline.cpp:11:
/usr/include/qt3/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
make[1]: *** [moc_dictOnline.o] Error 1
/usr/share/qt3/bin/moc downloadbar.h -o moc_downloadbar.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_downloadbar.o moc_downloadbar.cpp
In file included from downloadbar.h:25,
                 from moc_downloadbar.cpp:11:
/usr/include/qt3/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/include/qt3/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
/usr/share/qt3/bin/moc helpwindow.h -o moc_helpwindow.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_helpwindow.o moc_helpwindow.cpp
/usr/share/qt3/bin/moc mainwindow.h -o moc_mainwindow.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_mainwindow.o moc_mainwindow.cpp
/usr/share/qt3/bin/moc page.h -o moc_page.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_page.o moc_page.cpp
/usr/share/qt3/bin/moc searchfield.h -o moc_searchfield.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_searchfield.o moc_searchfield.cpp
/usr/share/qt3/bin/moc searchinterface.h -o moc_searchinterface.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_searchinterface.o moc_searchinterface.cpp
/usr/share/qt3/bin/moc sentenceline.h -o moc_sentenceline.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o moc_sentenceline.o moc_sentenceline.cpp
In file included from sentenceline.h:22,
                 from moc_sentenceline.cpp:11:
centralwidget.h:88: warning: unused parameter &#8216;built&#8217;
make[1]: Target `first' not remade because of errors.
make[1]: Leaving directory `/home/kimbop/Downloads/dragonflame_2-0_gnulinux/src'
make: *** [sub-src] Error 2
make: Target `first' not remade because of errors.
make: Leaving directory `/home/kimbop/Downloads/dragonflame_2-0_gnulinux'

Clean?

y(Yes) - Default
n(No)
q(Quit)
>y
make: Entering directory `/home/kimbop/Downloads/dragonflame_2-0_gnulinux'
( [ -d src ] && cd src ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d src ] && cd src ; make -f Makefile clean; ) || true
make[1]: Entering directory `/home/kimbop/Downloads/dragonflame_2-0_gnulinux/src'
rm -f moc_about.o moc_centralwidget.o moc_dictOnline.o moc_downloadbar.o moc_helpwindow.o moc_mainwindow.o moc_page.o moc_searchfield.o moc_searchinterface.o moc_sentenceline.o
rm -f moc_about.cpp moc_centralwidget.cpp moc_dictOnline.cpp moc_downloadbar.cpp moc_helpwindow.cpp moc_mainwindow.cpp moc_page.cpp moc_searchfield.cpp moc_searchinterface.cpp moc_sentenceline.cpp
rm -f about.o centralwidget.o dfstatusbar.o Dico.o dictOnline.o dictProtocol.o downloadbar.o entry.o helpwindow.o httpCore.o httpSynchronizer.o listboxmanager.o main.o mainwindow.o mybrowser.o page.o preferences.o searchfield.o searchinterface.o sentenceline.o splashwindow.o teng_exception.o teng_mylist.o teng_transcription.o
rm -f *~ core *.core
make[1]: Leaving directory `/home/kimbop/Downloads/dragonflame_2-0_gnulinux/src'
make: Leaving directory `/home/kimbop/Downloads/dragonflame_2-0_gnulinux'

Install in ...?

(/usr/local)
nothing - End
>/home/kimbop/sindarin
`./COPYING' -> `/home/kimbop/sindarin/dragonflame/COPYING'
`./Makefile' -> `/home/kimbop/sindarin/dragonflame/Makefile'
`./README' -> `/home/kimbop/sindarin/dragonflame/README'
`./bin' -> `/home/kimbop/sindarin/dragonflame/bin'
`./config' -> `/home/kimbop/sindarin/dragonflame/config'
`./config/df.xml' -> `/home/kimbop/sindarin/dragonflame/config/df.xml'
`./dicos' -> `/home/kimbop/sindarin/dragonflame/dicos'
`./dicos/sindarin.html.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/sindarin.html.dat'
`./dicos/goblyg.png' -> `/home/kimbop/sindarin/dragonflame/dicos/goblyg.png'
`./dicos/sindarin.ini' -> `/home/kimbop/sindarin/dragonflame/dicos/sindarin.ini'
`./dicos/draco.png' -> `/home/kimbop/sindarin/dragonflame/dicos/draco.png'
`./dicos/sindarin.002' -> `/home/kimbop/sindarin/dragonflame/dicos/sindarin.002'
`./dicos/sindarin.001' -> `/home/kimbop/sindarin/dragonflame/dicos/sindarin.001'
`./dicos/tuilinn.html' -> `/home/kimbop/sindarin/dragonflame/dicos/tuilinn.html'
`./dicos/tuilinn.ini.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/tuilinn.ini.dat'
`./dicos/tuilinn.001.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/tuilinn.001.dat'
`./dicos/sindarin.html' -> `/home/kimbop/sindarin/dragonflame/dicos/sindarin.html'
`./dicos/sindarin.002.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/sindarin.002.dat'
`./dicos/tuilinn.001' -> `/home/kimbop/sindarin/dragonflame/dicos/tuilinn.001'
`./dicos/sindcorpus.ini' -> `/home/kimbop/sindarin/dragonflame/dicos/sindcorpus.ini'
`./dicos/tuilinn.ini' -> `/home/kimbop/sindarin/dragonflame/dicos/tuilinn.ini'
`./dicos/sindcorpus.html' -> `/home/kimbop/sindarin/dragonflame/dicos/sindcorpus.html'
`./dicos/sindcorpus.ini.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/sindcorpus.ini.dat'
`./dicos/sindarin.001.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/sindarin.001.dat'
`./dicos/sindcorpus.001' -> `/home/kimbop/sindarin/dragonflame/dicos/sindcorpus.001'
`./dicos/tuilinn.002' -> `/home/kimbop/sindarin/dragonflame/dicos/tuilinn.002'
`./dicos/sindcorpus.001.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/sindcorpus.001.dat'
`./dicos/tuilinn.html.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/tuilinn.html.dat'
`./dicos/sindcorpus.html.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/sindcorpus.html.dat'
`./dicos/sindarin.ini.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/sindarin.ini.dat'
`./dicos/draco.png.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/draco.png.dat'
`./dicos/tuilinn.002.dat' -> `/home/kimbop/sindarin/dragonflame/dicos/tuilinn.002.dat'
`./doc' -> `/home/kimbop/sindarin/dragonflame/doc'
`./doc/searchss.png' -> `/home/kimbop/sindarin/dragonflame/doc/searchss.png'
`./doc/dfdoc.html' -> `/home/kimbop/sindarin/dragonflame/doc/dfdoc.html'
`./dragonflame.pro' -> `/home/kimbop/sindarin/dragonflame/dragonflame.pro'
`./images' -> `/home/kimbop/sindarin/dragonflame/images'
`./images/backtrans.png' -> `/home/kimbop/sindarin/dragonflame/images/backtrans.png'
`./images/about.png' -> `/home/kimbop/sindarin/dragonflame/images/about.png'
`./images/dict.png' -> `/home/kimbop/sindarin/dragonflame/images/dict.png'
`./images/smbkred.png' -> `/home/kimbop/sindarin/dragonflame/images/smbkred.png'
`./images/smbkblue.png' -> `/home/kimbop/sindarin/dragonflame/images/smbkblue.png'
`./images/forward.png' -> `/home/kimbop/sindarin/dragonflame/images/forward.png'
`./images/backward.png' -> `/home/kimbop/sindarin/dragonflame/images/backward.png'
`./images/forwtrans.png' -> `/home/kimbop/sindarin/dragonflame/images/forwtrans.png'
`./images/paper.png' -> `/home/kimbop/sindarin/dragonflame/images/paper.png'
`./images/tile.png' -> `/home/kimbop/sindarin/dragonflame/images/tile.png'
`./images/splash.png' -> `/home/kimbop/sindarin/dragonflame/images/splash.png'
`./images/Dragon Flame.ico' -> `/home/kimbop/sindarin/dragonflame/images/Dragon Flame.ico'
`./images/download.png' -> `/home/kimbop/sindarin/dragonflame/images/download.png'
`./install.sh' -> `/home/kimbop/sindarin/dragonflame/install.sh'
`./modes' -> `/home/kimbop/sindarin/dragonflame/modes'
`./modes/Sindarin Classic.mod' -> `/home/kimbop/sindarin/dragonflame/modes/Sindarin Classic.mod'
`./modes/Black Speech.mod' -> `/home/kimbop/sindarin/dragonflame/modes/Black Speech.mod'
`./modes/Sindarin.mod' -> `/home/kimbop/sindarin/dragonflame/modes/Sindarin.mod'
`./modes/English.mod' -> `/home/kimbop/sindarin/dragonflame/modes/English.mod'
`./modes/Quenya.mod' -> `/home/kimbop/sindarin/dragonflame/modes/Quenya.mod'
`./sounds' -> `/home/kimbop/sindarin/dragonflame/sounds'
`./sounds/beep.wav' -> `/home/kimbop/sindarin/dragonflame/sounds/beep.wav'
`./sounds/bdragon1.wav' -> `/home/kimbop/sindarin/dragonflame/sounds/bdragon1.wav'
`./sounds/bdragon2.wav' -> `/home/kimbop/sindarin/dragonflame/sounds/bdragon2.wav'
`./src' -> `/home/kimbop/sindarin/dragonflame/src'
`./src/preferences.cpp' -> `/home/kimbop/sindarin/dragonflame/src/preferences.cpp'
`./src/teng_transcription.cpp' -> `/home/kimbop/sindarin/dragonflame/src/teng_transcription.cpp'
`./src/httpCore.cpp' -> `/home/kimbop/sindarin/dragonflame/src/httpCore.cpp'
`./src/splashwindow.cpp' -> `/home/kimbop/sindarin/dragonflame/src/splashwindow.cpp'
`./src/dfstatusbar.h' -> `/home/kimbop/sindarin/dragonflame/src/dfstatusbar.h'
`./src/ioapi.h' -> `/home/kimbop/sindarin/dragonflame/src/ioapi.h'
`./src/httpSynchronizer.h' -> `/home/kimbop/sindarin/dragonflame/src/httpSynchronizer.h'
`./src/entry.cpp' -> `/home/kimbop/sindarin/dragonflame/src/entry.cpp'
`./src/about.h' -> `/home/kimbop/sindarin/dragonflame/src/about.h'
`./src/searchinterface.h' -> `/home/kimbop/sindarin/dragonflame/src/searchinterface.h'
`./src/resource.h' -> `/home/kimbop/sindarin/dragonflame/src/resource.h'
`./src/listboxmanager.cpp' -> `/home/kimbop/sindarin/dragonflame/src/listboxmanager.cpp'
`./src/dictProtocol.cpp' -> `/home/kimbop/sindarin/dragonflame/src/dictProtocol.cpp'
`./src/helpwindow.cpp' -> `/home/kimbop/sindarin/dragonflame/src/helpwindow.cpp'
`./src/dictOnline.h' -> `/home/kimbop/sindarin/dragonflame/src/dictOnline.h'
`./src/page.cpp' -> `/home/kimbop/sindarin/dragonflame/src/page.cpp'
`./src/Dico.cpp' -> `/home/kimbop/sindarin/dragonflame/src/Dico.cpp'
`./src/teng_exception.h' -> `/home/kimbop/sindarin/dragonflame/src/teng_exception.h'
`./src/mainwindow.cpp' -> `/home/kimbop/sindarin/dragonflame/src/mainwindow.cpp'
`./src/main.cpp' -> `/home/kimbop/sindarin/dragonflame/src/main.cpp'
`./src/mainwindow.h' -> `/home/kimbop/sindarin/dragonflame/src/mainwindow.h'
`./src/helpwindow.h' -> `/home/kimbop/sindarin/dragonflame/src/helpwindow.h'
`./src/downloadbar.cpp' -> `/home/kimbop/sindarin/dragonflame/src/downloadbar.cpp'
`./src/preferences.h' -> `/home/kimbop/sindarin/dragonflame/src/preferences.h'
`./src/teng_mylist.cpp' -> `/home/kimbop/sindarin/dragonflame/src/teng_mylist.cpp'
`./src/dictProtocol.h' -> `/home/kimbop/sindarin/dragonflame/src/dictProtocol.h'
`./src/unzip.h' -> `/home/kimbop/sindarin/dragonflame/src/unzip.h'
`./src/about.cpp' -> `/home/kimbop/sindarin/dragonflame/src/about.cpp'
`./src/centralwidget.h' -> `/home/kimbop/sindarin/dragonflame/src/centralwidget.h'
`./src/teng_mylist.h' -> `/home/kimbop/sindarin/dragonflame/src/teng_mylist.h'
`./src/zlib.h' -> `/home/kimbop/sindarin/dragonflame/src/zlib.h'
`./src/speciallistbox.h' -> `/home/kimbop/sindarin/dragonflame/src/speciallistbox.h'
`./src/teng_exception.cpp' -> `/home/kimbop/sindarin/dragonflame/src/teng_exception.cpp'
`./src/mybrowser.h' -> `/home/kimbop/sindarin/dragonflame/src/mybrowser.h'
`./src/dictOnline.cpp' -> `/home/kimbop/sindarin/dragonflame/src/dictOnline.cpp'
`./src/listboxmanager.h' -> `/home/kimbop/sindarin/dragonflame/src/listboxmanager.h'
`./src/zconf.h' -> `/home/kimbop/sindarin/dragonflame/src/zconf.h'
`./src/searchfield.cpp' -> `/home/kimbop/sindarin/dragonflame/src/searchfield.cpp'
`./src/mybrowser.cpp' -> `/home/kimbop/sindarin/dragonflame/src/mybrowser.cpp'
`./src/searchfield.h' -> `/home/kimbop/sindarin/dragonflame/src/searchfield.h'
`./src/downloadbar.h' -> `/home/kimbop/sindarin/dragonflame/src/downloadbar.h'
`./src/page.h' -> `/home/kimbop/sindarin/dragonflame/src/page.h'
`./src/sentenceline.cpp' -> `/home/kimbop/sindarin/dragonflame/src/sentenceline.cpp'
`./src/Dico.h' -> `/home/kimbop/sindarin/dragonflame/src/Dico.h'
`./src/sentenceline.h' -> `/home/kimbop/sindarin/dragonflame/src/sentenceline.h'
`./src/splashwindow.h' -> `/home/kimbop/sindarin/dragonflame/src/splashwindow.h'
`./src/src.pro' -> `/home/kimbop/sindarin/dragonflame/src/src.pro'
`./src/centralwidget.cpp' -> `/home/kimbop/sindarin/dragonflame/src/centralwidget.cpp'
`./src/httpSynchronizer.cpp' -> `/home/kimbop/sindarin/dragonflame/src/httpSynchronizer.cpp'
`./src/Makefile' -> `/home/kimbop/sindarin/dragonflame/src/Makefile'
`./src/searchinterface.cpp' -> `/home/kimbop/sindarin/dragonflame/src/searchinterface.cpp'
`./src/teng_transcription.h' -> `/home/kimbop/sindarin/dragonflame/src/teng_transcription.h'
`./src/entry.h' -> `/home/kimbop/sindarin/dragonflame/src/entry.h'
`./src/dfstatusbar.cpp' -> `/home/kimbop/sindarin/dragonflame/src/dfstatusbar.cpp'
kimbop@kimchi:~/Downloads/dragonflame_2-0_gnulinux$ 

```

EDIT: You can find the program [here]("http://www.jrrvf.com/hisweloke/sindar/archive.html").

---

### Post by slaanco on 2009-12-09
try sudo ./install.sh 

you are installing into the /usr/something normal user does not have privileges to write there. or am i missing something? :)

---

