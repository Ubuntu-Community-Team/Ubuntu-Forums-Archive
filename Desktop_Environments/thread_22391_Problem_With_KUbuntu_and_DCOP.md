---
title: "Problem With KUbuntu and DCOP"
date: 2005-03-27
forum: Desktop Environments
---

### Post by silent82 on 2005-03-27
Hello everyone!

I have a big problem with KDE. This is just one problem but it comes up for two reasons:

1) After I log in I can use KDE without any problem, after a while (random time), I start getting errors "KLauncher could not be reached via DCOP".

2) As soon as I log in if I open Konsole and run kcontrol I get this error:
```

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/silent82/.DCOPserver_port0__20
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
WARNING: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ERROR: KUniqueApplication: Can't setup DCOP communication.

```
and I start getting this error: "KLauncher could not be reached via DCOP" when I click on an icon on the desktop, and I can't start any application in the Kmenu.

After 1) and 2) I can't use KDE anymore because I can't start any application.

I tried to delete all .DCOPserver_port0_* files in my home, but nothing happens.
Also tried to delete /var/tmp/kdecache-* and restart but nothing happens.

Can someone help me?

Tanks!

---

### Post by LarsFischer on 2005-05-05
[QUOTE=silent82]Hello everyone!

After 1) and 2) I can't use KDE anymore because I can't start any application.

I tried to delete all .DCOPserver_port0_* files in my home, but nothing happens.
Also tried to delete /var/tmp/kdecache-* and restart but nothing happens.

Can someone help me?

Tanks![/QUOTE]

Are you using a firewall like firestarter? Try disabling the firewall for a while. I believe this is a problem with the firewall. As soon as I disable firestarter, the problem does not occur anymore. 

Unfortunately I have no idea how to configure firestarter to cooperate with this kde/dcop thing.

---

### Post by LarsFischer on 2005-05-06
Today the problem occured even with deactivated firewall.

---

### Post by LarsFischer on 2005-05-14
Hi,

yesterday, I remembered the thing, I did, when the dcop-problem arose:
I read about fork-bombing and how to prevent it (set limits using 
/etc/security/limits.conf).

Now I have change the limits to its original state (which is: no limits (every single line begins with #)) and I rebooted. At the moment the PC runs for 8 hours and the problem didnot occur during this time.

Regards, 
Lars

---

### Post by LarsFischer on 2005-05-15
Hi,

the problem occured again after 12 hours and the next day within 15 minutes after login. 

In oder to make KDE useable after the Problem occurs I do the following:

rm -rf /tmp/kde-$USER
rm -rf /var/tmp/kdecache-$USER

rm -f ~/.DCOP*

killall kicker

The I restart kicker via the Alt-F2 run-dialog.

Lars

---

### Post by LarsFischer on 2005-05-24
Hello,
during the last weeks I tried different things, to avoid the problem.

Nothing worked. 

Here is a list of things I tried:
-dcoprss: there was an update available and someone mentioned the problems has to do with dcoprss
-avoid konsole: someone mentioned that konsole caused the problem, so I used gnome-terminal
-firewall: I suspected my firewall, because the first error message of a programm (when run in a terminal) is: cannot open network socket
-kdebase: someone mentioned to reinstall kdebase
-ulimits: I suspected to low limits, at the moment I have no limits set
-avoid sudo: I suspected sudo, so I login as root on the text-console and, if necessary, start a second X-Server for administrative tasks. By the way the first thing after installing Ubuntu, was to activate the root account.
-deleting files: everytime when the problem occurs and I don't want to log out and in again, I do the following:
  rm -rf /tmp/kde-$USER
  rm -rf /var/tmp/kdecache-$USER
  rm -f ~/.DCOP*
  killall kicker
  killall kdesktop

  In a running terminal : kicker & and kdesktop& 

-screensaver: I suspected the screensaver, so I deaktivated it
-Lock: I suspected the screen-locking of the screensave, so I deactivated it
-compile from source: I did compile kdebase and its dependencies from source

Nothing worked. Has anybody moore ideas?

Lars

---

### Post by countrybob on 2005-06-25
I just had the same problem. When starting konqueror from xterm, I got a message that .ICEauthority had no access. Upon checking it was owned by root. I changed it, and I stoped getting the error.

---

### Post by LarsFischer on 2005-07-07
Hello,

@countrybob: I deleted the ICEauthority file several times, the problem did not disappear.

Meanwhile I tried Debian 3.1: the problem was there, too.

At the moment I am using SuSE 9.3. It seems that the problem does not occur with this distribution. 

What is the difference between SuSE and Debian/Ubuntu concerning this problem?

Lars

---

### Post by LarsFischer on 2006-03-20
Hello everybody,

I am using Ubuntu 5.10 since february and the problem occured only one or two times. It did not occur regularly.

Lars

---

