---
title: "Kcontrol problem report"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Olflo on 2005-06-09
If you start the Control Center from the K menu, it is owned by the user who started it. This means that some of the relevant funcztions are inaccesible. There is a button offering the Administrator Mode but when you push it and enter your password, nothing happens exept you are thrown back to kcontrol's start screen. I think something goes wrong here with the way the password is handled internally. Maybe its to do with the fact that there is no root account in Ubuntu, I dont know. At any rate, it all adds up to the effect that you cannot use the Control center to fine-tune your system, which was the whole idea behind it for users who are not so experienced with the command line.

I have found a workaround by typing sudo kcontrol in a terminal window to start the Control Center. This will bring a bunch of error messages: 

Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kcontrol, it probably crashed.
olflo@ubuntu:~$ Error: "/tmp/ksocket-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"

but finally launch an instance of kcontrol owned by root. Here all the (or, at least, more) options to fine-tune the system are available.

It would be nice if someone would try to fix or report that problem with kcontrol, for that is beyond my capacities. I was only able to find the workaround (with the help of the forum, that is). In the meantime, it would be good to know how I can change the K Menu entry for kcontrol so as to start kcontrol owned by root not the other, impotent one.


For more, see also this thread:
[URL]http://www.ubuntuforums.org/showthread.php?t=40118
[/URL]

---

### Post by paulvandenberg on 2005-06-09
[QUOTE=Olflo]If you start the Control Center from the K menu, it is owned by the user who started it. This means that some of the relevant funcztions are inaccesible. There is a button offering the Administrator Mode but when you push it and enter your password, nothing happens exept you are thrown back to kcontrol's start screen. I think something goes wrong here with the way the password is handled internally. Maybe its to do with the fact that there is no root account in Ubuntu, I dont know. At any rate, it all adds up to the effect that you cannot use the Control center to fine-tune your system, which was the whole idea behind it for users who are not so experienced with the command line.

I have found a workaround by typing sudo kcontrol in a terminal window to start the Control Center. This will bring a bunch of error messages: 

Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kcontrol, it probably crashed.
olflo@ubuntu:~$ Error: "/tmp/ksocket-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-olflo" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"

but finally launch an instance of kcontrol owned by root. Here all the (or, at least, more) options to fine-tune the system are available.

It would be nice if someone would try to fix or report that problem with kcontrol, for that is beyond my capacities. I was only able to find the workaround (with the help of the forum, that is). In the meantime, it would be good to know how I can change the K Menu entry for kcontrol so as to start kcontrol owned by root not the other, impotent one.


For more, see also this thread:
[URL]http://www.ubuntuforums.org/showthread.php?t=40118
[/URL][/QUOTE]
 Go to [http://www.kubuntu.org](http://www.kubuntu.org) and follow the instructions under the news item for upgrading to KDE 3.4.1. The problem with Admin access in KControl is a bug in KDE 3.4.0.

---

### Post by Olflo on 2005-06-12
Hello paulvandenberg,
thank you for the idea of upgrading to KDE 3.4.1.
I am experiencing problems doing this, though.
I have entered the corresponding sources to my etc/apt/sources.list:

deb [http://download.kde.org/stable/3.4.1/kubuntu](http://download.kde.org/stable/3.4.1/kubuntu) hoary-updates main

but in Synaptic Packcage manager I have no access to these. There is a message saying:

W: Kann nicht auf die Liste [http://download.kde.org](http://download.kde.org) hoary-updates/main Packages (/var/lib/apt/lists/download.kde.org_stable_3.4.1_kubuntu_dists_hoary-updates_main_binary-amd64_Packages) der Quellpakete zugreifen. - stat (2 Datei oder Verzeichnis nicht gefunden)

(sorry for the German, it basically says "cannot acces these repositories")

Do you have an idea? I'm not such a command line expert, let alone with apt-get, so I need to do it via Synaptic. One specific question: are these sources or binaries? maybe thtas part of the problem?

help appreciated.

---

### Post by vanaedium on 2005-06-12
i have upgraded to 3.4.1 and the problem with kcontrol is back!!!!
I've solved in 3.4.0 but now after an update............... ](*,)

---

### Post by Gezzer on 2005-06-12
i used gedit via sudo to add the repository to the source file as kate didn't want to play

as of no access to kcontrol admin via the user account i consider that a safe guard
i can still have full access via sudo kcontrol which means no one can play with the settings

that's IMHO & MHO only ...

---

### Post by kubuntuuser on 2005-06-15
Upgrading to kde3.4.1 will not fix this problem. 

See the KDE change log here

[http://www.kde.org/announcements/changelogs/changelog3_4to3_4_1.php](http://www.kde.org/announcements/changelogs/changelog3_4to3_4_1.php)

---

