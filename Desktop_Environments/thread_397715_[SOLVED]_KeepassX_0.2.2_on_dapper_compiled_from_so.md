---
title: "[SOLVED] KeepassX 0.2.2 on dapper compiled from source – works fine"
date: 2007-03-31
forum: Desktop Environments
---

### Post by be4truth on 2007-03-31
running dapper with Kubuntu 3.5.5 on an I686 &#8211; full updatet. The debian package as well as the Feisty package doesn't work on my system. I compiled KeepassX from source and it works fine.

Qt 4.1.3 from the Keepass website  [http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb](http://keepassx.sourceforge.net/download/qt4_4.1.3-2_i386.deb)

sudo dpkg -i qt4_4.1.3-2_i386.deb

I needed to install xlib-dev as it doesn't come with standard KDE-Desktop

sudo apt-get install xlib-dev 

Download the source tar ball from the Keepass website [http://prdownloads.sourceforge.net/keepassx/KeePassX-0.2.2.tar.gz?download](http://prdownloads.sourceforge.net/keepassx/KeePassX-0.2.2.tar.gz?download)

and followed this instructions [http://keepassx.sourceforge.net/howto/setup/inst_source_tar/](http://keepassx.sourceforge.net/howto/setup/inst_source_tar/)

---

