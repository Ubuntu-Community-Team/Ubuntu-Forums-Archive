---
title: "Gromacs GUI installation"
date: 2008-02-27
forum: Education &amp; Science
---

### Post by jlawrence on 2008-02-27
Hi,

I tried to install Gromacs GUI, however I am not sure how to do it correctly since the prerequisites part made me confused.

[http://www.kde-apps.org/content/show.php/Gromacs+GUI+?content=47665](http://www.kde-apps.org/content/show.php/Gromacs+GUI+?content=47665)

Can someone who has installed this program guide me ? I am using Gnome, and would like to install Gromacs GUI with plotting version.(included in the tar file)

Here is the instruction:
--------------------------------
Prerequisites
=============
You should have "Qt 4.3.x" (both lib and devel packages) and "Qwt 5.0.2" (both lib and devel packages) installed. You can use your linux distribution online repositories to find these packages. In OpenSuse, these packages can be easily downloaded and installed through Yast or Smart or Zypper.


How to Compile
==============
1) Open grogui.pro and edit options based on your system. Normally you only have to make sure that path to Qwt files is correct:
 -- in DEPENDPATH and INCLUDEPATH edit "/usr/include/qwt" to point to the directory containing header files of Qwt.
 -- if the Qwt lib (.so file) has been installed in a directory which is not in your search path, you can point to that directory with: LIBS += L/path/to/qwtlibdirectory/
2) qmake
3) make
4) ./grogui


Thank you in advance,

---

### Post by ahmatti on 2008-02-28
> **jlawrence said:**
> Hi,

--------------------------------
Prerequisites
=============
You should have "Qt 4.3.x" (both lib and devel packages) and "Qwt 5.0.2" (both lib and devel packages) installed. You can use your linux distribution online repositories to find these packages. In OpenSuse, these packages can be easily downloaded and installed through Yast or Smart or Zypper.



I haven't used Gromacs, but you can find the prerequisites from the ubuntu repos. Just run:

sudo apt-get install libqt4-core libqt4-dev libqwt5-qt4 libqwt-qt4-dev

Or install same packages with synaptic. Hope this helps!

---

### Post by Tarto on 2009-07-09
Dear All

Firstly let me introduce my self, my name is Tarto and I am very new in using linux. I have problem when installing gromacs GUI. I couldn't execute make and I got error (last line):

Makefile:512: warning: overriding commands for target `qrc_main.cpp'
Makefile:416: warning: ignoring old commands for target `qrc_main.cpp'
Makefile:530: warning: overriding commands for target `qrc_mdi.cpp'
Makefile:434: warning: ignoring old commands for target `qrc_mdi.cpp'
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -Iui -I/usr/include/qwt-qt4 -I. -I. -o plotwidget.o src/plotwidget.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -Iui -I/usr/include/qwt-qt4 -I. -I. -o finddialog.o src/finddialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -Iui -I/usr/include/qwt-qt4 -I. -I. -o iconprovider.o src/iconprovider.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -Iui -I/usr/include/qwt-qt4 -I. -I. -o aboutgrogui.o src/aboutgrogui.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -Iui -I/usr/include/qwt-qt4 -I. -I. -o addpopupitem.o src/addpopupitem.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -Iui -I/usr/include/qwt-qt4 -I. -I. -o commands.o src/commands.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -Iui -I/usr/include/qwt-qt4 -I. -I. -o dirbrowser.o src/dirbrowser.cpp
src/dirbrowser.cpp:158: warning: unused parameter &#8216;point&#8217;
src/dirbrowser.cpp: In member function &#8216;QModelIndex DirBrowser::indexAt(const QPoint&) const&#8217;:
src/dirbrowser.cpp:161: warning: control reaches end of non-void function
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -Iui -I/usr/include/qwt-qt4 -I. -I. -o editor.o src/editor.cpp
src/editor.cpp: In member function &#8216;void Editor::updateMenus()&#8217;:
src/editor.cpp:156: error: &#8216;class MdiChild&#8217; has no member named &#8216;isUndoAvailable&#8217;
src/editor.cpp:157: error: &#8216;class MdiChild&#8217; has no member named &#8216;isRedoAvailable&#8217;
make: *** [editor.o] Error 1

I can't run ./grogui. Anyone can help me, please? 
Thank you very much for any kinds of help.

Best regards
Tarto

---

