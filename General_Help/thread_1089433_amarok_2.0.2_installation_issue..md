---
title: "amarok 2.0.2 installation issue."
date: 2009-03-07
forum: General Help
---

### Post by Hellbike on 2009-03-07
I got ubuntu, and wanted to upgrade amarok from 1.4 to 2.0.2.

I dont have kubuntu, so i had to compile source.

I was fallowing those instructions :

[http://amarok.kde.org/wiki/Compiling:2.0](http://amarok.kde.org/wiki/Compiling:2.0)

but installation didn't worked :

> [ 85%] Built target amarok_afttagger
Generating contentfetcher.moc
Generating DaapCollection.moc
Generating Reader.moc
Scanning dependencies of target amarok_collection-daapcollection
[ 85%] Building CXX object src/collection/daap/CMakeFiles/amarok_collection-daapcollection.dir/amarok_collection-daapcollection_automoc.o
[ 85%] Building CXX object src/collection/daap/CMakeFiles/amarok_collection-daapcollection.dir/DaapMeta.o
[ 85%] Building CXX object src/collection/daap/CMakeFiles/amarok_collection-daapcollection.dir/DaapCollection.o
[ 85%] Building CXX object src/collection/daap/CMakeFiles/amarok_collection-daapcollection.dir/daapreader/Reader.o
[ 85%] Building CXX object src/collection/daap/CMakeFiles/amarok_collection-daapcollection.dir/daapreader/authentication/contentfetcher.o
[ 85%] Building C object src/collection/daap/CMakeFiles/amarok_collection-daapcollection.dir/daapreader/authentication/hasher.o
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c: In function ‘GenerateStatic_42’:
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:51: warning: pointer targets in initialization differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:62: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:64: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:67: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:69: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:72: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:74: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:77: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:79: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:82: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:84: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:87: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:89: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:92: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:94: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:97: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:99: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:102: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Final’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:103: warning: pointer targets in passing argument 1 of ‘DigestToString’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:103: warning: pointer targets in passing argument 2 of ‘DigestToString’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c: In function ‘GenerateStatic_45’:
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:111: warning: pointer targets in initialization differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:122: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:124: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:127: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:129: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:132: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:134: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:137: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:139: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:142: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:144: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:147: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:149: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:152: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:154: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:157: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:159: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:163: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Final’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:164: warning: pointer targets in passing argument 1 of ‘DigestToString’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:164: warning: pointer targets in passing argument 2 of ‘DigestToString’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c: In function ‘GenerateHash’:
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:189: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:190: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:192: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:198: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Update’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:201: warning: pointer targets in passing argument 2 of ‘OpenDaap_MD5Final’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:202: warning: pointer targets in passing argument 1 of ‘DigestToString’ differ in signedness
/home/hellbike/amarok-2.0.2/src/collection/daap/daapreader/authentication/hasher.c:202: warning: pointer targets in passing argument 2 of ‘DigestToString’ differ in signedness
[ 85%] Building C object src/collection/daap/CMakeFiles/amarok_collection-daapcollection.dir/daapreader/authentication/md5.o
Linking CXX shared module ../../../lib/libamarok_collection-daapcollection.so
[ 85%] Built target amarok_collection-daapcollection
[ 85%] Generating SqlCollectionAdaptor.cpp, SqlCollectionAdaptor.h
[ 85%] Generating SqlCollectionAdaptor.moc
Generating SqlCollection.moc
Generating sqlmeta.moc
Generating ScanResultProcessor.moc
Generating SqlQueryMaker.moc
Generating XesamCollectionBuilder.moc
Generating MySqlEmbeddedCollection.moc
Generating SqlRegistry.moc
Generating ScanManager.moc
Generating SqlCollectionLocation.moc
Generating SqlCollectionDBusHandler.moc
Generating XesamDbus.moc
Generating moc_OrganizeCollectionDialog.cpp
[ 85%] Generating ui_OrganizeCollectionDialogBase.h
Scanning dependencies of target amarok_collection-sqlcollection
[ 85%] Building CXX object src/collection/sqlcollection/CMakeFiles/amarok_collection-sqlcollection.dir/amarok_collection-sqlcollection_automoc.o
[ 85%] Building CXX object src/collection/sqlcollection/CMakeFiles/amarok_collection-sqlcollection.dir/DatabaseUpdater.o
[ 85%] Building CXX object src/collection/sqlcollection/CMakeFiles/amarok_collection-sqlcollection.dir/OrganizeCollectionDialog.o
[ 86%] Building CXX object src/collection/sqlcollection/CMakeFiles/amarok_collection-sqlcollection.dir/ScanManager.o
[ 86%] Building CXX object src/collection/sqlcollection/CMakeFiles/amarok_collection-sqlcollection.dir/ScanResultProcessor.o
[ 86%] Building CXX object src/collection/sqlcollection/CMakeFiles/amarok_collection-sqlcollection.dir/SqlCollection.o
In file included from /home/hellbike/amarok-2.0.2/src/collection/sqlcollection/XesamCollectionBuilder.h:22,
                 from /home/hellbike/amarok-2.0.2/src/collection/sqlcollection/SqlCollection.cpp:37:
/home/hellbike/amarok-2.0.2/src/collection/sqlcollection/XesamDbus.h:22:39: error: strigi/qtdbus/strigitypes.h: No such file or directory
In file included from /home/hellbike/amarok-2.0.2/src/collection/sqlcollection/SqlCollection.cpp:308:
/usr/include/qt4/QtCore/qmetatype.h: In static member function ‘static int QMetaTypeId2<T>::qt_metatype_id() [with T = QList<int>]’:
/usr/include/qt4/QtCore/qmetatype.h:195:   instantiated from ‘int qMetaTypeId(T*) [with T = QList<int>]’
/usr/include/qt4/QtCore/qvariant.h:427:   instantiated from ‘QVariant qVariantFromValue(const T&) [with T = QList<int>]’
/home/hellbike/amarok-2.0.2/src/collection/sqlcollection/XesamDbus.h:89:   instantiated from here
/usr/include/qt4/QtCore/qmetatype.h:185: error: ‘qt_metatype_id’ is not a member of ‘QMetaTypeId<QList<int> >’
/usr/include/qt4/QtCore/qmetatype.h: In static member function ‘static int QMetaTypeId2<T>::qt_metatype_id() [with T = QVector<QList<QVariant> >]’:
/usr/include/qt4/QtCore/qmetatype.h:195:   instantiated from ‘int qMetaTypeId(T*) [with T = QVector<QList<QVariant> >]’
/usr/include/qt4/QtDBus/qdbusreply.h:68:   instantiated from ‘QDBusReply<T>& QDBusReply<T>::operator=(const QDBusMessage&) [with T = QVector<QList<QVariant> >]’
/usr/include/qt4/QtDBus/qdbusreply.h:64:   instantiated from ‘QDBusReply<T>::QDBusReply(const QDBusMessage&) [with T = QVector<QList<QVariant> >]’
/home/hellbike/amarok-2.0.2/src/collection/sqlcollection/XesamDbus.h:90:   instantiated from here
/usr/include/qt4/QtCore/qmetatype.h:185: error: ‘qt_metatype_id’ is not a member of ‘QMetaTypeId<QVector<QList<QVariant> > >’
make[2]: *** [src/collection/sqlcollection/CMakeFiles/amarok_collection-sqlcollection.dir/SqlCollection.o] B&#322;&#261;d 1
make[1]: *** [src/collection/sqlcollection/CMakeFiles/amarok_collection-sqlcollection.dir/all] B&#322;&#261;d 2
make: *** [all] B&#322;&#261;d 2
 ("b&#322;ad" means error)

when i try to run amarok-2.0.2-build/scr/amarok, it's return error:

> Amarok could not find any collection plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca4 --noincremental
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

---

### Post by Hellbike on 2009-03-07
i installed kde and kubuntu-desktop, logon kde session, autoremoved amarok and installed using adept-installer.

It shows i got 2.1.4 version installed, but when i run program, it's still 1.4

amarok->help->about kde shows i got kde 3.5

but i got newest version.

---

