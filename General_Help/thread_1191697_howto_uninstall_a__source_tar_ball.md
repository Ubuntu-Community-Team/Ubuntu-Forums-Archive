---
title: "howto uninstall a  source tar ball"
date: 2009-06-19
forum: General Help
---

### Post by lex1 on 2009-06-19
i have installed on my system a tar ball from source
with the commads

configure
make
make install

how to uninstall/delete this package

lex1

---

### Post by cyclobs on 2009-06-19
make uninstall i think it is

---

### Post by Chronon on 2009-06-19
The makefile should list all of the options if you open it in a text editor.

---

### Post by lex1 on 2009-06-19
most of the files are in the directory 
/var/dcc

biut the source tar ball i cannot find

this is what i did in the original install


cd /tmp
wget [http://www.dcc-servers.net/dcc/source/dcc-dccproc.tar.Z](http://www.dcc-servers.net/dcc/source/dcc-dccproc.tar.Z)
tar xzvf dcc-dccproc.tar.Z
cd dcc-dccproc-1.3.102
./configure --with-uid=amavis
make
make install
chown -R amavis:amavis /var/dcc
ln -s /var/dcc/libexec/dccifd /usr/local/bin/dccifd

thanks
lex1

ps I removed amavis a while back with apt-get

---

