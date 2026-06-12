---
title: "Error message"
date: 2006-03-27
forum: Desktop Environments
---

### Post by eriefisher on 2006-03-27
Ever since a fresh install and loading kubuntu-destop I keep getting this error message and am at a loss on how to rectify it.

eriefisher@ubuntubox:~$ sudo kwrite /etc/apt/sources.list
Password:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-10623' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_ubuntubox__0
and start dcopserver again.
---------------------------------

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KMimeType): WARNING: KServiceType::offers : servicetype KTextEditor/Plugin not found
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_ubuntubox__0
and start dcopserver again.
---------------------------------

WARNING: Waiting for already running klauncher to exit.
WARNING: Waiting for already running klauncher to exit.
WARNING: Another instance of klauncher is already running!
kdeinit: Communication error with launcher. Exiting!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

eriefisher@ubuntubox:~$

This is beyond my knowledge and some insight would be great. I also get a window that opens up with the message "wrong mime type/octet stream" I believe it says.

eriefisher

---

### Post by incubus on 2006-03-27
You know you should be using "kdesu" instead of "sudo" there, right?
$ kdesu kwrite <...>

This is because if you use "sudo", it will overwrite your user files as a root. The result of course is a mess in your ~/.kde directory.

Can you try:
$ sudo chown -R eriefisher:eriefisher ~/.kde
(I'm assuming eriefisher is your username)

incubus

---

### Post by lupine_nickt on 2006-03-27
The problem basically comes from running something graphical from the console. For whatever reason, the program can't communicate with the X server.

A quick test on my konsole shows that if I'm in the "base"/initial shell, then I can load apps up from konsole with no problems. If I then su into another user (eg. root), any GUI applications I run fail with a similar error. 

A simple enough workaround is to use the "Run Command" option in the KDE menu... it even allows for setting the programs to run as root, which is much handier for running GUI apps, TBH. 

Alternatively, for the specific case of modifying config files, you could always "sudo apt-get install joe" - then just "sudo joe /etc/apt/sources.list" (or whatever config file you like). 

Joe is 8) ...

xF,

...Nick

---

### Post by eriefisher on 2006-03-28
Thanks all. It looks like you suggestions helped clear the error. Now I'm one more step closer to understanding the world of Linux. Thanks again.

eriefisher

---

