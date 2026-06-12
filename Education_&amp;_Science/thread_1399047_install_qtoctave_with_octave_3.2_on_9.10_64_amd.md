---
title: "install qtoctave with octave 3.2 on 9.10_64 amd"
date: 2010-02-05
forum: Education &amp; Science
---

### Post by gerion on 2010-02-05
hey everyone, I have a problem installing qtoctave 0.8.2 on Ubuntu64 9.10, amd, with octave 3.2. I have to install from source as the package manager links qtoctave to octave 3.0.

The following error occured during the make process:

Scanning dependencies of target easy_plot
[ 43%] Building CXX object easy_plot/src/CMakeFiles/easy_plot.dir/gnuplot_connection.o
/home/christian/Desktop/qtoctave-0.8.2/easy_plot/src/gnuplot_connection.cpp: In member function ‘void GnuplotConnection::standardOutputReady()’:
/home/christian/Desktop/qtoctave-0.8.2/easy_plot/src/gnuplot_connection.cpp:143: error: ‘printf’ was not declared in this scope
make[2]: *** [easy_plot/src/CMakeFiles/easy_plot.dir/gnuplot_connection.o] Error 1
make[1]: *** [easy_plot/src/CMakeFiles/easy_plot.dir/all] Error 2
make: *** [all] Error 2

a similar problem occurred trying to install easy plot (not sure if that would fix the first problem):

[ 53%] Building CXX object src/CMakeFiles/easy_plot.dir/gnuplot_connection.o
cd /home/christian/Desktop/easy_plot/src && /usr/bin/c++   -DQT_DLL -DQT_SVG_LIB -DQT_GUI_LIB -DQT_XML_LIB -DQT_CORE_LIB -DQT_NO_DEBUG -O3 -DNDEBUG -I/usr/include/qt4 -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtCore   -o CMakeFiles/easy_plot.dir/gnuplot_connection.o -c /home/christian/Desktop/easy_plot/src/gnuplot_connection.cpp
/home/christian/Desktop/easy_plot/src/gnuplot_connection.cpp: In member function ‘void GnuplotConnection::standardOutputReady()’:
/home/christian/Desktop/easy_plot/src/gnuplot_connection.cpp:143: error: ‘printf’ was not declared in this scope
make[2]: *** [src/CMakeFiles/easy_plot.dir/gnuplot_connection.o] Error 1
make[2]: Leaving directory `/home/christian/Desktop/easy_plot'
make[1]: *** [src/CMakeFiles/easy_plot.dir/all] Error 2
make[1]: Leaving directory `/home/christian/Desktop/easy_plot'
make: *** [all] Error 2

What I found on the web is
[http://osdir.com/ml/debian-bugs-closed/2009-10/msg01388.html](http://osdir.com/ml/debian-bugs-closed/2009-10/msg01388.html)
which didn't really help.

The deb package they refer to on [http://web.zcu.cz/ftp/mirrors/debian/pool/main/q/qtoctave/](http://web.zcu.cz/ftp/mirrors/debian/pool/main/q/qtoctave/) doesn't work, message: 
Error: Dependency is not satisfiable: libqt4-network (>= 4:4.5.2)
although the Package manager says that version "4.5.3really4.5.2-0ubuntu1" is installed.

File are taken from [http://forja.rediris.es/frs/?group_id=60](http://forja.rediris.es/frs/?group_id=60)
Happy for any suggestions. Thanks

---

### Post by gerion on 2010-02-05
Addition: what does work, is to install octave 3.2 and qtoctave with octave 3.0 from the repository, then set the octave path to 3.2 in the qtoctave configuration.

---

### Post by Amurko on 2010-02-11
Is there any way I can install octave 3.2 with qtoctave AND not have octave 3.0 lying around on my HD?  Maybe force the removal of 3.0 once qtoctave is installed.  Or is there a feature in qtoctave that MUST depend on octave 3.0 being installed and not 3.2?

---

### Post by gerion on 2010-02-11
you can install qtoctave from source, available at [http://qtoctave.wordpress.com/download/](http://qtoctave.wordpress.com/download/)

However, you might have to use the repository version, see last post at the aforementioned link

---

### Post by Amurko on 2010-02-12
I just need Synaptic to somehow recognise that QtOctave can work just as fine with octave 3.2 installed instead of octave 3.0.  Is there any place I can report "bugged" dependencies like this to the Ubuntu devs?

---

### Post by gerion on 2010-02-14
no idea how to report outdated dependencies, but I'd assume it'll be updated with a future Ubuntu release. 

Don't think the dependencies can be adjusted manually, but pls post it if you find out how.

---

### Post by jsampaio57 on 2010-02-18
I managed to successfully compile qtoctave under ubuntu 9.10 and using octave-3.4.2. I had to make 2 changes:
After downloading qtoctave-0.8.2 and extracting it (tar -xzf qtoctave...)
I added the line...

#include <stdio.h>

to the top of the following files:

.../qtoctave-0.8.2/easy_plot/src/gnuplot_connection.cpp
and
.../qtoctave-0.8.2/qtoctave/src/search_dialog.cpp

After this, and under the folder .../qtoctave-0.8.2 I did:
cmake .   
make
sudo make install

then I got an operational qtoctave with octave-3.4.2

(This is a great GUI!)

Cheers...
Jorge

---

### Post by edantes on 2010-03-19
> **gerion said:**
> hey everyone, I have a problem installing qtoctave 0.8.2 on Ubuntu64 9.10, amd, with octave 3.2. I have to install from source as the package manager links qtoctave to octave 3.0.

The deb package they refer to on [http://web.zcu.cz/ftp/mirrors/debian/pool/main/q/qtoctave/](http://web.zcu.cz/ftp/mirrors/debian/pool/main/q/qtoctave/) doesn't work, message: 
Error: Dependency is not satisfiable: libqt4-network (>= 4:4.5.2)
although the Package manager says that version "4.5.3really4.5.2-0ubuntu1" is installed.

File are taken from [http://forja.rediris.es/frs/?group_id=60](http://forja.rediris.es/frs/?group_id=60)
Happy for any suggestions. Thanks

The Debian sid package works if you ignore the dependencies during instalation.

I had Octave 3.2 already installed and  downloaded the QTOctave 0.8.2 package from here: 

[http://packages.debian.org/sid/amd64/qtoctave/download](http://packages.debian.org/sid/amd64/qtoctave/download)

Then, installed it by brute force:

sudo dpkg --ignore-depends=libqt4-network,libqt4-script,libqt4-sql,libqt4-svg,libqt4-xml,libqtcore4,libqtgui4 -i qtoctave_0.8.2+dfsg-2_amd64.deb

The problem is that the package is declared "broken" by synaptic.

Is there any way out of this?  The dependencies are actually fine, but the version name for the QT lib packages is not numeric: "4.5.3really4.5.2-0ubuntu1" and doesn't satisfy the requirement (>= 4:4.5.2).  

How can I get synaptic/apt from complaining and attempting to "fix" the broken (not really) package?

---

