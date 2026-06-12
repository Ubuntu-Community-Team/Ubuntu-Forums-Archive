---
title: "Freemat - problems to built on ubuntu8.04"
date: 2008-06-16
forum: Education &amp; Science
---

### Post by bd@cb8be8510 on 2008-06-16
I need some advice in order to built Freemat on my computer.
After  ../configure -v --prefix=/myhomedirectory

I get the following report:
checking for gfortran... gfortran
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether gfortran accepts -g... yes
checking how to get verbose linking output from gfortran... -v
checking for Fortran 77 libraries of gfortran...  -L/usr/lib/gcc/i486-linux-gnu/4.2.3 -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../.. -lcurses -lgfortranbegin -lgfortran -lm

[B]configure: error: Qt4 is required.  If you have Qt installed see --help for more options
[/B]
I don't understand this as QT4 has been properly installed on my computer. Has anyone encountered the same problem? How can I solve this problem? Thanks for your advice!

---

### Post by aJayRoo on 2008-06-16
Since you are compiling from source you will need to install the development library:
```
sudo apt-get install libqt4-dev
```
Hope that helps.

---

### Post by bd@cb8be8510 on 2008-06-17
Thank you for the hint.
I installed yet practically almost anything that matches the query "qt4" in the synaptic package manager. It looks as if the install-file can't figure out properly that qt4 has been installed.

When I try the following command pkg-config --libs libqt4-dev

I get a message Package libqt4-dev was not found in the pkg-config search path. Perhaps you should add the directory containing 'libqt4-dev.pc' to the PKG_CONFIG_PATH environment variable.
No package 'libqt4-dev' found.

On the other hand the synpatic package manager clearly shows that libqt4-dev is installed :
4.4.0-1ubuntu5~hardy1 (hardy-backports)
4.3.4-0ubuntu3 (hardy)




In the mean time I tried to install Freemat in Wine (as a test). Freemat was installed properly but the command-line is working very slowly. So using Freemat in Wine in not an option.

---

### Post by bd@cb8be8510 on 2008-06-19
pkg-config --list-all | grep "QT*"
sqlite                   SQLite - SQL database engine
QtCore                   Qtcore - Qtcore Library
QtScript                 Qtscript - Qtscript Library
QtXmlPatterns            Qtxmlpatterns - Qtxmlpatterns Library
QtDesignerComponents     Qtdesignercomponents - Qtdesignercomponents Library
QtSql                    Qtsql - Qtsql Library
QtDBus                   Qtdbus - Qt DBus module
QtTest                   Qttest - Qt Unit Testing Library
QtSvg                    Qtsvg - Qtsvg Library
QtUiTools                Qtuitools - Qtuitools Library
QtHelp                   Qthelp - Qthelp Library
QtNetwork                Qtnetwork - Qtnetwork Library
QtAssistantClient        Qtassistantclient - Qtassistantclient Library
QtDesigner               Qtdesigner - Qtdesigner Library
QtWebKit                 Qtwebkit - Qtwebkit Library
QtXml                    Qtxml - Qtxml Library
Qt3Support               Qt3support - Qt3support Library
QtCLucene                Qtclucene - Qtclucene Library
QtGui                    Qtgui - Qtgui Library

It looks as if there are no pacakges installed having a name QT4. Is this some kind of packaging-problem? Or is it an error in the freemat-make-files?

Please return any help

---

### Post by WW on 2008-06-19
Qt4 is actually a suite of libraries, as your command shows.  I took a look at the *configure.in* script in the Freemat source code; it looks for these Qt4 components: QtCore QtGui QtOpenGL QtNetwork QtXml QtSvg.  Your list doesn't show QtOpenGL, which is strange, since it should have been provided by the package libqt4-dev.

By the way, I think the grep command that you used does something different than you expected.  The pattern "QT*" means "Q followed by zero or more T's", so it will match anything containing a Q.  Instead, try **grep "Qt"**.


EDIT:  I just noticed that you are using hardy-backports to get Qt4.  Be sure you have also installed **libqt4-opengl-dev**.

---

### Post by bd@cb8be8510 on 2008-06-19
Hi, WW! You're wonderful! I have installed the package libqt4-opengl-dev (which was not installed). Everything compiles!

---

