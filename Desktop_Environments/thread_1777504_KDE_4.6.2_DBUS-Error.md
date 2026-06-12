---
title: "KDE 4.6.2 DBUS-Error"
date: 2011-06-07
forum: Desktop Environments
---

### Post by blckshadow on 2011-06-07
Hey there,
I hope I'm in the right forum this time. I'm using KDE 4.6.2 (KDE in general) for the first time in years. What I wanted to do originally was to install the Currency Converter Plasmoid, where the plasmoidviewer returned this error: ```
plasmoidviewer(5325)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0)  
```.
And the plasmoidviewer is telling me, that he couldn't find requested component.
So I dug deeper and found these errors in my .xsession-errors:
```
Xsession: X session started for cymo at Di 7. Jun 23:28:06 CEST 2011
Setting IM through im-switch for locale=de_DE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
[: 227: =: unexpected operator
startkde: Starting up...
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kbuildsycoca4 running...
X Error: BadValue (integer parameter out of range for operation) 2
  Major opcode: 102 (X_ChangeKeyboardControl)
  Resource id:  0xffffff8c
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)

Object::connect: No such signal QDBusAbstractInterface::Changed()
Invalid D-BUS member name 'idle-hint' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'is-local' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'remote-host-name' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'session-type' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'unix-user' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.5'
QDBusConnection: name 'org.freedesktop.UPower' had owner '' but we thought it was ':1.21'
OpenGL vendor string:                   ATI Technologies Inc.
OpenGL renderer string:                 ATI Mobility Radeon HD 3400 Series
OpenGL version string:                  2.1 (3.3.10665 Compatibility Profile Context)
Driver:                                 Catalyst
Driver version:                         2.1
GPU class:                              R600
OpenGL version:                         2.1
X server version:                       1.10.1
Linux kernel version:                   2.6.38
Direct rendering:                       no
Requires strict binding:                yes
GLSL shaders:                           no
Texture NPOT support:                   yes
kwin(2137): ""fsrestore1" - conversion of "0,0,0,0" to QRect failed" 
kwin(2137): ""fsrestore2" - conversion of "0,0,0,0" to QRect failed" 
kwin(2137): ""fsrestore3" - conversion of "0,0,0,0" to QRect failed" 
kwin(2137): ""fsrestore4" - conversion of "0,0,0,0" to QRect failed" 
kwin(2137): ""restore5" - conversion of "0,0,0,0" to QRect failed" 
kwin(2137): ""fsrestore5" - conversion of "0,0,0,0" to QRect failed" 
kwin(2137): ""restore6" - conversion of "0,0,0,0" to QRect failed" 
kwin(2137): ""fsrestore6" - conversion of "0,0,0,0" to QRect failed" 
kwin(2137): ""fsrestore7" - conversion of "0,0,0,0" to QRect failed" 
QDBusObjectPath: invalid path ""
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Object::connect: No such signal KWindowSystem::windowChanged(WId,unsigned long*)
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -3) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -3) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(-4, -3) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QGridLayoutEngine::addItem: Cell (1, 1) already taken
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Object::connect: No such signal QDBusAbstractInterface::Changed()
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
plasma-desktop(2148) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
Object::connect: No such slot AbstractItemView::iconSettingsChanged()
"/usr/bin/kactivitymanagerd(2141)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/kactivitymanagerd(2141)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/kactivitymanagerd(2141)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/kactivitymanagerd(2141)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/kactivitymanagerd(2141)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/kactivitymanagerd(2141)" Soprano: "QLocalSocket::connectToServer: Invalid name"
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
plasma-desktop(2148)/libakonadi Akonadi::AgentManagerPrivate::createDBusInterface: AgentManager failed to get a valid AgentManager DBus interface. Error is: 1 "org.freedesktop.DBus.Error.NameHasNoOwner" "Could not get owner of name 'org.freedesktop.Akonadi.Control': no such name" 
plasma-desktop(2148)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Invalid name" 
plasma-desktop(2148)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Invalid name" 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
search paths:  ("/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/usr/games", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Found mysql_install_db:  "/usr/bin/mysql_install_db" 
Found mysqlcheck:  "/usr/bin/mysqlcheck" 
plasma-desktop(2148)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Invalid name" 
akonadi.collectionattributetable                   OK
akonadi.collectionmimetyperelation                 OK
akonadi.collectionpimitemrelation                  OK
akonadi.collectiontable                            OK
akonadi.flagtable                                  OK
akonadi.mimetypetable                              OK
akonadi.parttable                                  OK
akonadi.pimitemflagrelation                        OK
akonadi.pimitemtable                               OK
akonadi.resourcetable                              OK
akonadi.schemaversiontable                         OK
mysql.columns_priv                                 OK
mysql.db                                           OK
mysql.event                                        OK
mysql.func                                         OK
mysql.general_log
Error    : You can't use locks with log tables.
status   : OK
mysql.help_category                                OK
mysql.help_keyword                                 OK
mysql.help_relation                                OK
mysql.help_topic                                   OK
mysql.host                                         OK
mysql.ndb_binlog_index                             OK
mysql.plugin                                       OK
mysql.proc                                         OK
mysql.procs_priv                                   OK
mysql.servers                                      OK
mysql.slow_log
Error    : You can't use locks with log tables.
status   : OK
mysql.tables_priv                                  OK
mysql.time_zone                                    OK
mysql.time_zone_leap_second                        OK
mysql.time_zone_name                               OK
mysql.time_zone_transition                         OK
mysql.time_zone_transition_type                    OK
mysql.user                                         OK
Database "akonadi" opened using driver "QMYSQL" 
DbInitializer::run() 
checking table  "SchemaVersionTable" 
checking table  "ResourceTable" 
checking table  "CollectionTable" 
checking table  "MimeTypeTable" 
checking table  "PimItemTable" 
checking table  "FlagTable" 
checking table  "PartTable" 
checking table  "CollectionAttributeTable" 
checking relation  "PimItemFlagRelation" 
checking relation  "CollectionMimeTypeRelation" 
checking relation  "CollectionPimItemRelation" 
DbInitializer::run() done 
skipping update 2 
skipping update 3 
skipping update 4 
skipping update 8 
skipping update 10 
skipping update 12 
skipping update 13 
skipping update 14 
skipping update 15 
skipping update 16 
skipping update 17 
skipping update 18 
skipping update 19 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Nepomuk Query Server not available 
DataStore::unhideAllPimItems() 
PLUGINS:  "/usr/share/akonadi/agents" 
PLUGINS:  ("birthdaysresource.desktop", "contactsresource.desktop", "icalresource.desktop", "imapresource.desktop", "kabcresource.desktop", "kcalresource.desktop", "knutresource.desktop", "kolabproxyresource.desktop", "localbookmarksresource.desktop", "maildirresource.desktop", "maildispatcheragent.desktop", "mboxresource.desktop", "microblog.desktop", "mtdummyresource.desktop", "nepomukcalendarfeeder.desktop", "nepomukcontactfeeder.desktop", "nepomuktagresource.desktop", "nntpresource.desktop", "notesresource.desktop", "pop3resource.desktop", "vcarddirresource.desktop", "vcardresource.desktop") 
search paths:  ("/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/usr/games") 
PLUGINS inserting:  "akonadi_birthdays_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_contacts_resource" 9 ("Resource") 
PLUGINS inserting:  "akonadi_ical_resource" 2 ("Resource") 
PLUGINS inserting:  "akonadi_imap_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_kabc_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_kcal_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_knut_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_kolabproxy_resource" 0 ("Resource", "Unique", "NoConfig") 
PLUGINS inserting:  "akonadi_localbookmarks_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_maildir_resource" 1 ("Resource") 
PLUGINS inserting:  "akonadi_maildispatcher_agent" 0 ("Unique", "Autostart", "NoConfig") 
PLUGINS inserting:  "akonadi_mbox_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_microblog_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_mailtransport_dummy_resource" 0 ("Resource", "MailTransport") 
PLUGINS inserting:  "akonadi_nepomuk_calendar_feeder" 0 ("Unique", "NoConfig") 
PLUGINS inserting:  "akonadi_nepomuk_contact_feeder" 0 ("Unique", "Autostart", "NoConfig") 
PLUGINS inserting:  "akonadi_nepomuktag_resource" 0 ("Resource", "Virtual", "Unique", "NoConfig") 
PLUGINS inserting:  "akonadi_nntp_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_notes_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_pop3_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_vcarddir_resource" 0 ("Resource") 
PLUGINS inserting:  "akonadi_vcard_resource" 1 ("Resource") 
Akonadi server is now operational. 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Known subscriber "akonadi_maildispatcher_agent" subscribes again 
Database "akonadi" opened using driver "QMYSQL" 
Known subscriber "akonadi_maildispatcher_agent" subscribes again 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
unnamed app(2290) main: Migrator instance already running for type  "contact" 
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "QLocalSocket::connectToServer: Invalid name"
QSqlDatabasePrivate::removeDatabase: connection 'qt_sql_default_connection' is still in use, all queries will cease to work.
QSqlDatabasePrivate::addDatabase: duplicate connection name 'qt_sql_default_connection', old connection removed.
I/O warning : failed to load external entity "/home/cymo/.qalculate/eurofxref-daily.xml"
I/O warning : failed to load external entity "/home/cymo/.qalculate/eurofxref-daily.xml"
[/usr/bin/nepomukservicestub] Using Virtuoso Version: "6.1.2.3127-pthreads" 
Using Virtuoso Version: "6.1.2.3127-pthreads" 
void Soprano::VirtuosoController::writeConfigFile(const QString&, const Soprano::BackendSettings&) "/tmp/virtuoso_hX2199.ini" 
Starting Virtuoso server: "/usr/bin/virtuoso-t" ("+foreground", "+configfile", "/tmp/virtuoso_hX2199.ini", "+wait")
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "QLocalSocket::connectToServer: Invalid name"
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "QLocalSocket::connectToServer: Invalid name"
Database "akonadi" opened using driver "QMYSQL" 
krunner(2195)/libplasma Plasma::Package::isValid: Could not find required file mainscript 
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/nepomukservicestub] "
"
[/usr/bin/nepomukservicestub] "        Tue Jun 07 2011
"
[/usr/bin/nepomukservicestub] "23:28:39 OpenLink Virtuoso Universal Server
"
[/usr/bin/nepomukservicestub] "23:28:39 Version 06.01.3127-pthreads for Linux as of Aug  3 2010
"
[/usr/bin/nepomukservicestub] "23:28:39 uses parts of OpenSSL, PCRE, Html Tidy
"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "Unsupported operation (2)": "Invalid model"
[/usr/bin/nepomukservicestub] "23:28:39 Database version 3126
"
QPixmap::scaled: Pixmap is a null pixmap
[/usr/bin/nepomukservicestub] "23:28:40 Entering Lite Mode
"
[/usr/bin/nepomukservicestub] "23:28:40 SQL Optimizer enabled (max 1000 layouts)
"
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "Invalid iterator."
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "Invalid iterator."
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "Invalid iterator."
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2280)" Soprano: "Invalid iterator."
[/usr/bin/nepomukservicestub] "23:28:41 Compiler unit is timed at 0.002815 msec
"
[/usr/bin/nepomukservicestub] "23:28:42 Roll forward started
"
[/usr/bin/nepomukservicestub] "23:28:42     2 transactions, 87 bytes replayed (100 %)
"
[/usr/bin/nepomukservicestub] "23:28:42 Roll forward complete
"
[/usr/bin/nepomukservicestub] "23:28:42 Checkpoint started
"
[/usr/bin/nepomukservicestub] "23:28:42 Checkpoint finished, log reused
"
[/usr/bin/nepomukservicestub] "23:28:44 Server online at 1111 (pid 2373)
"
[/usr/bin/nepomukservicestub] Virtuoso started: 2373
[/usr/bin/nepomukservicestub] Soprano::ODBC::ConnectionPool::ConnectionPool(const QString&, const QStringList&, QObject*) "host=localhost:1111;uid=dba;pwd=dba;driver=/usr/lib/odbc/virtodbc_r.so"
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() QThread(0x905a800)
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2199)" Soprano: "SQLGetData for data length failed (iODBC Error: [OpenLink][Virtuoso iODBC Driver]CL056: Bookmarks not enable for statement)"
[/usr/bin/nepomukservicestub] bool Soprano::Virtuoso::DatabaseConfigurator::updateFulltextIndexRules(bool) empty rule name!
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() QThread(0x905a800)
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() QThread(0x905a800)
"/usr/bin/akonadi_nepomuk_contact_feeder(2231)" Soprano: "org.freedesktop.DBus.Error.UnknownObject - No such object path '/org/soprano/Server'"
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() QThread(0x91ebb38) 
QObject::setParent: Cannot set parent, new parent is in a different thread
virtual void Soprano::Server::LocalServer::incomingConnection(quintptr) 
void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 1 
virtual void Soprano::Server::LocalServer::incomingConnection(quintptr) 
void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 2
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb42010e0)
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() QThread(0x91ebb38)
Akonadi::NepomukSearchEngine(0x93ef6d0) QDBusServiceWatcher(0x93eb390) 
New PolkitAgentListener  0x8587a50 
Adding new listener  PolkitQt1::Agent::Listener(0x861e488) for  0x8587a50 

(knotify4:2145): GStreamer-CRITICAL **: gst_debug_add_log_function: assertion `func != NULL' failed
kmix(2268) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2268) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(2060)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2268) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(2060)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QGraphicsLinearLayout::removeAt: invalid index 1
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(2148)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
kmix(2268) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(2060)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
plasma-desktop(2148)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
plasma-desktop(2148)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
Database "akonadi" opened using driver "QMYSQL" 
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::DBusController(0xb42004a8) 
virtual void Soprano::Server::LocalServer::incomingConnection(quintptr) 
void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 3 
virtual void Soprano::Server::LocalServer::incomingConnection(quintptr) 
void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 4

(firefox-bin:2393): GLib-CRITICAL **: g_hash_table_insert_internal: assertion `hash_table != NULL' failed
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr) 
void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 5 
virtual void Soprano::Server::LocalServer::incomingConnection(quintptr) 
void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 6 
Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb4205088) 
virtual void Soprano::Server::ServerConnection::run() thread done. 
virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0xb4205088) 
void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 5

(firefox-bin:2393): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
kcmshell(2456)/Network Management (ui) WirelessPreferences::WirelessPreferences: Could not find deviceUni or AP UNI in args: (QVariant(QString, "{42d5e382-9d5a-49aa-9b3a-ff076df5a5a7}") )  
kwalletd(2066) KWalletD::setupDialog: Application ' "KDE-Kontrollmodul" ' using kwallet without parent window! 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xe00019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5600019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5600019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5600019
Object::disconnect: No such slot QObject::dataUpdated(QString,Plasma::DataEngine::Data)
Object::disconnect:  (sender name:   'Battery0')
Object::disconnect: No such slot QObject::dataUpdated(QString,Plasma::DataEngine::Data)
Object::disconnect:  (sender name:   'AC Adapter')
Object::disconnect: No such slot QObject::dataUpdated(QString,Plasma::DataEngine::Data)
Object::disconnect:  (sender name:   'PowerDevil')
Object::disconnect: No such slot QObject::dataUpdated(QString,Plasma::DataEngine::Data)
Object::disconnect:  (sender name:   'Battery')
Object::disconnect: No such slot QObject::dataUpdated(QString,Plasma::DataEngine::Data)
Object::disconnect:  (sender name:   'events:2011-05-30:2011-07-10')
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 6
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb4205088)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 7
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb4205008)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0xb4205088)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 6
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x932d8c8)
void Akonadi::NotificationSource::serviceUnregistered(const QString&) Notification source "plasma-desktop" now serving: () 
void Akonadi::NotificationSource::unsubscribe() "plasma-desktop" 
klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 7
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb4205088)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0xb4205088)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 6
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

kbuildsycoca4 running...
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 7
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb4205088)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0xb4205088)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished()
[/usr/bin/nepomukservicestub] virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 6
void Akonadi::NotificationSource::serviceUnregistered(const QString&) Notification source "plasma-desktop" now serving: () 
void Akonadi::NotificationSource::unsubscribe() "plasma-desktop" 
klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 7
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb42051e0)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0xb42051e0)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 6
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
QClipboard::setData: Cannot set X11 selection owner for PRIMARY
QClipboard::setData: Cannot set X11 selection owner for PRIMARY
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa3641d8)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa3641d8)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa3641d8)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa3641d8)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa4302c0)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa4302c0)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa4302c0)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa4302c0)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xae90d438)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xae90d438)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xae90d438)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xae90d438)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xae90d438)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xae90d438)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xae90d438)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xae90d438)
krunner(2195)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 87) 
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa3c0ff0)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3d94a8), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa3c0ff0)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa3c0ff0)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::UDisks::UDisksDevice(0xa3dcdd0), parent's thread is QThread(0xa044078), current thread is ThreadWeaver::Thread(0xa3c0ff0)

(firefox-bin:3177): GLib-CRITICAL **: g_hash_table_insert_internal: assertion `hash_table != NULL' failed
klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

kbuildsycoca4 running...
void Akonadi::NotificationSource::serviceUnregistered(const QString&) Notification source "plasma-desktop" now serving: () 
void Akonadi::NotificationSource::unsubscribe() "plasma-desktop" 
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 7
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb42051e0)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0xb42051e0)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 6
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 7
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0xb4206de8)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0xb4206de8)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 6
Database "akonadi" opened using driver "QMYSQL" 
Database "akonadi" opened using driver "QMYSQL" 
klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2058)/kio (KLauncher): SlavePool: No communication with slave. 

QClipboard::setData: Cannot set X11 selection owner for PRIMARY
QClipboard::setData: Cannot set X11 selection owner for PRIMARY

```When I launch application I got the following error on the console ```
plasma-desktop(5159)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 

```
The thing is, that it is a nearly fresh installation of Kubuntu 11.04.
What have I tried until now is a installation of kde-full, which didn't solve the problem and I googled a lot, but didn't found a helpful post.

I'm on to this topic since hours. I hope you may have an idea!

Greetings, blckshadow

---

