---
title: "BigLancelot Launcher"
date: 2014-09-06
forum: Desktop Environments
---

### Post by anon_private on 2014-09-06
I believe that I have installed BigLancelot using Muon Discover.
I received the message that it is installed. However, I can't find it in Add Widgets?

I removed BigLancelot and re-installed the widget, but again I cannot find it in widgets

Advice please 						

KDE 4.13.3
KUBUNTU ver 14.04

---

### Post by Rog131 on 2014-09-07
You could check the problem by launching the Muon Discover in the konsole.

The output at here: [http://pastebin.com/VP0xpEe0](http://pastebin.com/VP0xpEe0)

There are missing parts: "No metadata file in package "BigLancelot.skz""

The problem seems to be that the BigLancelot is not following the current knewstuff3/Get Hot New Stuff Specification.


**Background**

The Muon Discover is using KNewStuff3: [https://jontheechidna.wordpress.com/category/kde/](https://jontheechidna.wordpress.com/category/kde/)

The KNewStuff3 is KDE implementation of the GHNS: [http://ghns.freedesktop.org/spec/ghns-spec.html](http://ghns.freedesktop.org/spec/ghns-spec.html)

The Muon Discover is searching the plasma widget scripts from the KDE-Apps: [http://kde-apps.org/content/show.php/BigLancelot?content=112269](http://kde-apps.org/content/show.php/BigLancelot?content=112269)

The KDE-Apps is part of the OpenDesktop: [http://opendesktop.org/help/faq1.php](http://opendesktop.org/help/faq1.php)

---

### Post by anon_private on 2014-09-07
Thank you for the information, much appreciated.

This explains why I could not find the widget.

I think I'll leave this one and make a decision regarding an application launcher from the widgets that I have installed.

Best wishes.

A

Ps. A note for the future. If I try to investigate a problem using Muon Discover and using the command prompt. Is the ciorrect procedure to run this command straight after noticing a download problem. The command looks like muon-discover. Should this be an elevated command?

---

### Post by Rog131 on 2014-09-07
>  Is the ciorrect procedure to run this command straight after noticing a download problem. 

The KDE/Qt applications output the error information to the stderr. You could search the error messages from the ~/.cache/upstart/startkde.log or simply run the application from the teminal (konsole) and see the error message right away.


> The command looks like muon-discover. Should this be an elevated command?

Only if you really want to use the root/admin rights. The Muon family should ask the administrative rights when it needs them. The plasma widget scripts installed via the KNewStuff3 don't need special rights. They are downloaded and unpacked to the user's home. 

Downloaded to the /tmp/kde-<username>/.
Unpacked to the ~/.kde/share/apps/plasma/plasmoids/<plasmoidname>/  and the desktop part to the ~/.kde/share/kde4/services/.

---

### Post by anon_private on 2014-09-07
Just thought I would try to start Muon Discover from the terminal.

The programme started, but I did get a number of errors, are these errors anything to worry about.

I paste the output below (for some reason a smiley has appeared, 4th line):

andrew@andrew-Dell-DM061:~$ muon-discover
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
qrc:/qml/FeaturedModel.qml:24: SyntaxError: Unable to parse JSON string
andrew@andrew-Dell-DM061:~$ JSonScanner::yylex - error reading from io device 
qrc:/qml/FeaturedModel.qml:24: SyntaxError: Unable to parse JSON string
Couldn't find the releasechecker script 
/usr/bin/python3: can't find '__main__' module in ''
JSonScanner::yylex - error reading from io device

---

### Post by Rog131 on 2014-09-08
**Annoying but harmless ?**

Those messages are, probably, like the

> QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave. 

Annoying but harmless warning message on startup of every KUniqueApplication: [https://bugs.kde.org/show_bug.cgi?id=297020](https://bugs.kde.org/show_bug.cgi?id=297020)
and more: [https://forum.kde.org/viewtopic.php?f=66&t=102251](https://forum.kde.org/viewtopic.php?f=66&t=102251)

You could do net searches with the warning/error messges...

---

### Post by anon_private on 2014-09-08
Thank you

---

