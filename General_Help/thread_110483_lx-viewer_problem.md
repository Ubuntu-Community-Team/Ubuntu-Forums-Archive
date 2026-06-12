---
title: "lx-viewer problem"
date: 2005-12-30
forum: General Help
---

### Post by swregulator on 2005-12-30
I tried to install lx-viewer, a program for reading CAD files (dwg files in particular).  I realize this is a specialized question, but perhaps someone will recognize the error I received and be able to comment.  The error was as follows:

g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -Imoc_files/ -o object_files/3Dview.o 3Dview.cpp
make: g++: Command not found
make: *** [object_files/3Dview.o] Error 127

Any thoughts?
Thanks

---

### Post by sciurus on 2005-12-31
Is build-essential installed?

[http://ubuntuforums.org/showthread.php?t=53856](http://ubuntuforums.org/showthread.php?t=53856)

---

### Post by swregulator on 2005-12-31
Thanks for the reply.  I installed g++.  This cured the error I posted earlier.  But now I get a new error:

:~/LXInstall$ sudo make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -Imoc_files/ -o object_files/main.o main.cpp
/usr/include/qt3/qnetworkprotocol.h:58: warning: ‘class QNetworkProtocolFactoryBase’ has virtual functions but non-virtual destructor
/usr/include/qt3/qfiledialog.h:78: warning: ‘class QFilePreview’ has virtual functions but non-virtual destructor
main.cpp: In function ‘int main(int, char**)’:
main.cpp:117: error: expected type-specifier before ‘QWindowsStyle’
main.cpp:117: error: expected `)' before ‘QWindowsStyle’
main.cpp:117: error: no matching function for call to ‘QApplication::setStyle(int*)’
/usr/include/qt3/qapplication.h:89: note: candidates are: static void QApplication::setStyle(QStyle*)
/usr/include/qt3/qapplication.h:90: note:                 static QStyle* QApplication::setStyle(const QString&)
make: *** [object_files/main.o] Error 1

Any help appreciated.

---

