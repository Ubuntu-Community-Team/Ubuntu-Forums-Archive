---
title: "help needed with Bambus error..grommit error"
date: 2011-03-18
forum: Education &amp; Science
---

### Post by roshanbernard on 2011-03-18
hi ,

i am working on ubuntu 10.10..and i am not able to install bambus programme(gene assemble software)

when i give command 'make all' it gives me this message


if [ ! -d /usr/home/bambus-2.33 ] ;then mkdir /usr/home/bambus-2.33 ;fi
if [ ! -d /usr/home/bambus-2.33/bin/ ] ;then mkdir /usr/home/bambus-2.33/bin ;fi
if [ ! -d /usr/home/bambus-2.33/lib/ ] ;then mkdir /usr/home/bambus-2.33/lib ;fi
if [ ! -d /usr/home/bambus-2.33/doc/ ] ;then mkdir /usr/home/bambus-2.33/doc ;fi
for i in src doc ;do cd $i ; make install; cd .. ;done
make[1]: Entering directory `/home/rosh/bambus-2.33/src'
for i in goBambus.pl; do /bin/sed "s,^\#!/usr/local/bin/perl,\#!/usr/local/bin/perl," $i | /bin/sed "s,^\(my\)*[ ]*\$BAMBUS_BASE.*,\1 \$BAMBUS_BASE = \"/usr/home/bambus-2.33\";," > /usr/home/bambus-2.33/bin/`expr $i : '\(.*\)\.pl$'`; done
for i in IO DotLib TIGR_Foundation_CC grommit ;do cd $i ; make install; cd .. ;done
make[2]: Entering directory `/home/rosh/bambus-2.33/src/IO'
for i in bacEnd.pl detective.pl printScaff.pl xml2grommit.pl catXML.pl untangle.pl; do /bin/sed "s,^\#!/usr/local/bin/perl,\#!/usr/local/bin/perl," $i | /bin/sed "s/^\(use DBI.*\)/\#\1/" | /bin/sed "s,^\(my\)*[ ]*\$BAMBUS_BASE.*,\1 \$BAMBUS_BASE = \"/usr/home/bambus-2.33\";," > /usr/home/bambus-2.33/bin/`expr $i : '\(.*\)\.pl$'`; done
make[2]: Leaving directory `/home/rosh/bambus-2.33/src/IO'
make[2]: Entering directory `/home/rosh/bambus-2.33/src/DotLib'
cp DotLib.pm /usr/home/bambus-2.33/lib/
make[2]: Leaving directory `/home/rosh/bambus-2.33/src/DotLib'
make[2]: Entering directory `/home/rosh/bambus-2.33/src/TIGR_Foundation_CC'
g++ -D_HAS_GETOPT -c -o FileSystem.o FileSystem.cc
FileSystem.cc: In static member function ‘static bool FileSystem::isCreatableFile(const char*)’:
FileSystem.cc:58: error: invalid conversion from ‘const char*’ to ‘char*’
make[2]: *** [FileSystem.o] Error 1
make[2]: Leaving directory `/home/rosh/bambus-2.33/src/TIGR_Foundation_CC'
make[2]: Entering directory `/home/rosh/bambus-2.33/src/grommit'
g++ -Wl -L../TIGR_Foundation_CC/ -o grommit grommit.o -L. -lgraph -lTigrFoundation
/usr/bin/ld: cannot find -lTigrFoundation
collect2: ld returned 1 exit status
make[2]: *** [grommit] Error 1
make[2]: Leaving directory `/home/rosh/bambus-2.33/src/grommit'
make[1]: Leaving directory `/home/rosh/bambus-2.33/src'
make[1]: Entering directory `/home/rosh/bambus-2.33/doc'
cp BAMBUS.README /usr/home/bambus-2.33/doc
cp Manual.html /usr/home/bambus-2.33/doc
cp xml2grommit.README /usr/home/bambus-2.33/doc
cp scaffold.dtd /usr/home/bambus-2.33/doc
cp evidence.dtd /usr/home/bambus-2.33/doc
cp -r Manual_files /usr/home/bambus-2.33/doc
make[1]: Leaving directory `/home/rosh/bambus-2.33/doc'
cp -r lib/* /usr/home/bambus-2.33/lib
chmod -R a+rx /usr/home/bambus-2.33/bin




can anyone tell me what is grommit error,

i have taked care of all the information given in the site, about editing the path and fixing the bug


regards

roshan

---

