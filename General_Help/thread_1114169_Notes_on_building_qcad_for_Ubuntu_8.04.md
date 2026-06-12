---
title: "Notes on building qcad for Ubuntu 8.04"
date: 2009-04-02
forum: General Help
---

### Post by dananarama on 2009-04-02
Just dropping some notes here on my build of qcad in Ubuntu 8.04.



- Needed to install packages:
[I]apt-get install qt3-dev-tools
apt-get install qt3-apps-dev
[/I]

- Needed to add env variables:
[I]QTDIR="/usr/share/qt3"
QMAKESPEC="$QTDIR/mkspecs/linux-g++-32"
[/I]
     -for this I used:
     [I]gedit /etc/environment
     source /etc/environment
     export QTDIR=$QTDIR
     export QMAKESPEC=$QMAKESPEC[/I]

- Downloaded qcad source from:
[http://ribbonsoft.com/archives/qcad/qcad-2.0.5.0-1-community.src.tar.gz](http://ribbonsoft.com/archives/qcad/qcad-2.0.5.0-1-community.src.tar.gz)

- Removed '-pedantic' from all files in source project.  
Compilation failed without this.  See this thread:
[http://www.mail-archive.com/gnhlug-discuss@mail.gnhlug.org/msg21946.html](http://www.mail-archive.com/gnhlug-discuss@mail.gnhlug.org/msg21946.html)

- Compiled by executing:
* ./scripts/build_qcad.sh *


Note that build of other languages failed.


- Installed into /usr/bin:
[I]cp -R qcad /usr/bin/qcad_comm_ed
ln -s /usr/bin/qcad_comm_ed/qcad /usr/bin/qcad[/I]

- Pointed application configuration to new paths:
*qcad*
Edit->Application Preferences->Paths
*/usr/bin/qcad_comm_ed/patterns*

Do the same for fonts, scripts, library.






Hope this helps someone,


Dan

---

