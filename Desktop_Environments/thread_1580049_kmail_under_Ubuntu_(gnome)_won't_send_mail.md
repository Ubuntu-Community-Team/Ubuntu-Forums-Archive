---
title: "kmail under Ubuntu (gnome) won't send mail"
date: 2010-09-22
forum: Desktop Environments
---

### Post by cdaemon on 2010-09-22
I'm running Ubuntu 10.04 64bit on an AMD quad machine, and trying to use Kmail. I've installed the package and all dependencies, and Kmail opens and looks fine, but it crashes every time I try to send mail.

Opening Kmail and sending mail from the command line:

jsimmons@gryphon:~$ kmail
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Unable to register service as org.freedesktop.Akonadi.Control Maybe it's already running?
"[
0: /usr/bin/akonadi_control(_Z11akBacktracev+0x39) [0x416779]
1: /usr/bin/akonadi_control() [0x416cba]
2: /lib/libc.so.6(+0x33af0) [0x7f0198e5daf0]
3: /lib/libc.so.6(gsignal+0x35) [0x7f0198e5da75]
4: /lib/libc.so.6(abort+0x180) [0x7f0198e615c0]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7f019a044844]
6: /usr/bin/akonadi_control(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x417dc8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7f019a0d3417]
8: /usr/lib/libQtCore.so.4(+0x112529) [0x7f019a0e5529]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f019a0e6729]
10: /usr/bin/akonadi_control(main+0x466) [0x42bab6]
11: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f0198e48c4d]
12: /usr/bin/akonadi_control() [0x4120b9]
]
"
kmail(7065)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kmail(7065)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
jsimmons@gryphon:~$ Enchant dict for "en_US" 0x10fe530 
kmail(7065)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/jsimmons/.kde/share/apps/kabc" 
Enchant dict for "en_US" 0x14779b0 
kmail(7065)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
kmail(7065)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
kmail(7065)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
kmail(7065)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
kmail(7065)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
kmail(7065)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
kmail(7065)/libakonadi Akonadi::SessionPrivate::socketError: Socket error occurred: "QLocalSocket::connectToServer: Connection refused" 
^C

Does anyone have any idea what the problem is? Assistance highly appreciated!

--
Jeff Simmons                     jsimmons at goblin dot punk dot net

---

### Post by jcolyn on 2010-09-22
Have you tried opening Kmail by clicking the icon?

In Gnome it should be under the internet tab or maybe the office tab.

While Kmail is a fine email program evolution is better suited to Gnome and can easily handle multiple email accounts.

---

