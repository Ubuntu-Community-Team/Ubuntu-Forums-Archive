---
title: "Trouble when Updating."
date: 2009-05-14
forum: General Help
---

### Post by emacbri on 2009-05-14
Hi,

My computer recently lost power when updating. When  I restarted it it gave me this error:

[U][I]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I][/U]

When I ran "*sudo dpkg --configure -a*" I got this:
(Sorry this is very long)

```
dpkg: dependency problems prevent configuration of libqt4-gui:
 libqt4-gui depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-gui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql:
 libqt4-sql depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-sql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-svg depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-network:
 libqt4-network depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-network (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql-mysql:
 libqt4-sql-mysql depends on libqt4-sql (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-sql is not configured yet.
 libqt4-sql-mysql depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-sql-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:
 libqt4-script depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-script (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-dbus:
 libqt4-dbus depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:
 libqt4-opengl depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-opengl depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-opengl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqt4-script (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-script is not configured yet.
 libqt4-designer depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-designer depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qt4-qtconfig:
 qt4-qtconfig depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 qt4-qtconfig depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing qt4-qtconfig (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-core:
 libqt4-core depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-core depends on libqt4-network (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-network is not configured yet.
 libqt4-core depends on libqt4-script (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-script is not configured yet.
 libqt4-core depends on libqt4-dbus (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-dbus is not configured yet.
dpkg: error processing libqt4-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-designer is not configured yet.
 libqt4-qt3support depends on libqt4-network (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-network is not configured yet.
 libqt4-qt3support depends on libqt4-sql (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-sql is not configured yet.
 libqt4-qt3support depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-qt3support depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xml:
 libqt4-xml depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-xml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-test:
 libqt4-test depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-test (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-assistant:
 libqt4-assistant depends on libqt4-network (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-network is not configured yet.
 libqt4-assistant depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-assistant (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-gui
 libqt4-sql
 libqt4-svg
 libqt4-network
 libqt4-sql-mysql
 libqt4-script
 libqt4-dbus
 libqt4-opengl
 libqt4-designer
 qt4-qtconfig
 libqt4-core
 libqt4-qt3support
 libqt4-xml
 libqt4-test
 libqt4-assistant
```Please help me!

---

### Post by alexandari on 2009-05-14
how about ```
sudo apt-get install -f
```

---

### Post by AlexsAntidote on 2009-05-14
> **emacbri said:**
> Hi,

My computer recently lost power when updating. When  I restarted it it gave me this error:

[U][I]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I][/U]

When I ran "*sudo dpkg --configure -a*" I got this:
(Sorry this is very long)
```

dpkg: dependency problems prevent configuration of libqt4-gui:
 libqt4-gui depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-gui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql:
 libqt4-sql depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-sql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-svg depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-network:
 libqt4-network depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-network (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql-mysql:
 libqt4-sql-mysql depends on libqt4-sql (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-sql is not configured yet.
 libqt4-sql-mysql depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-sql-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:
 libqt4-script depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-script (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-dbus:
 libqt4-dbus depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-opengl:
 libqt4-opengl depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-opengl depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-opengl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqt4-script (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-script is not configured yet.
 libqt4-designer depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-designer depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qt4-qtconfig:
 qt4-qtconfig depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 qt4-qtconfig depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing qt4-qtconfig (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-core:
 libqt4-core depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-core depends on libqt4-network (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-network is not configured yet.
 libqt4-core depends on libqt4-script (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-script is not configured yet.
 libqt4-core depends on libqt4-dbus (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-dbus is not configured yet.
dpkg: error processing libqt4-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-designer is not configured yet.
 libqt4-qt3support depends on libqt4-network (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-network is not configured yet.
 libqt4-qt3support depends on libqt4-sql (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-sql is not configured yet.
 libqt4-qt3support depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
 libqt4-qt3support depends on libqtgui4 (= 4.5.0-0ubuntu4.1); however:
  Package libqtgui4 is not installed.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xml:
 libqt4-xml depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-xml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-test:
 libqt4-test depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-test (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-assistant:
 libqt4-assistant depends on libqt4-network (= 4.5.0-0ubuntu4.1); however:
  Package libqt4-network is not configured yet.
 libqt4-assistant depends on libqtcore4 (= 4.5.0-0ubuntu4.1); however:
  Version of libqtcore4 on system is 4.5.0-0ubuntu4.
dpkg: error processing libqt4-assistant (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-gui
 libqt4-sql
 libqt4-svg
 libqt4-network
 libqt4-sql-mysql
 libqt4-script
 libqt4-dbus
 libqt4-opengl
 libqt4-designer
 qt4-qtconfig
 libqt4-core
 libqt4-qt3support
 libqt4-xml
 libqt4-test
 libqt4-assistant

```

Please help me!

if you enclose your output in code tags it makes the length a bit more manageable ;)

Yeah that looks like a nasty file, but did you try the command suggested by alexandari?

---

### Post by emacbri on 2009-05-14
I tried that and I got this message:
[U][I]
E: Sub-process /usr/bin/dpkg returned an error code (2)[/I][/U]

---

### Post by emacbri on 2009-05-14
I also get this error when checking for updates:
[U][I]
You have 15 broken packages on your system!
Use the "Broken" filter to locate them.[/I][/U]

---

### Post by AlexsAntidote on 2009-05-14
> **emacbri said:**
> I also get this error when checking for updates:
[U][I]
You have 15 broken packages on your system!
Use the "Broken" filter to locate them.[/I][/U]

check this out: [http://ubuntuforums.org/showthread.php?t=749400&highlight=broken+package](http://ubuntuforums.org/showthread.php?t=749400&highlight=broken+package)

---

### Post by emacbri on 2009-05-14
I looked, but that was about Hardy, I am running Jaunty.

---

### Post by emacbri on 2009-05-14
Please help, I would like to add software but I can't.

---

### Post by alexandari on 2009-05-15
well the link AlexsAntidote gave you might solve your problem. Doesn`t matter if it is about Hardy or Jaunty. Synaptic is on both of them :)

---

### Post by emacbri on 2009-05-15
The thread AlexsAntidote linked to deals with a different problem than I am having, It wasn't very helpful.:mad:

---

### Post by emacbri on 2009-05-15
I would very much like some help, I would like to download Screem for a project due on Monday.

---

### Post by Intrepid Ibex on 2009-05-15
maybe you should fix the broken packages? also you might wanna try changing the download server by Software Sources.

---

### Post by emacbri on 2009-05-15
I've tried to fix the broken packages inside of synaptic, but every time I try, it seems to do nothing. I use the command in the menu. When I try, I get the same error.

---

### Post by AlexsAntidote on 2009-05-15
> **emacbri said:**
> I've tried to fix the broken packages inside of synaptic, but every time I try, it seems to do nothing. I use the command in the menu. When I try, I get the same error.

Would you mind listing the steps you are taking when you try to fix it in Synaptic, that may help us help you.

---

### Post by emacbri on 2009-05-15
Sorry, I ran out of time, I reinstalled Ubuntu. I am no longer having problems. Thanks for all your help anyway (no sarcasm here). If I have the same problem again, I will try again later. Thanks!:)

---

### Post by Corvair on 2009-07-06
I also have an update problem. The following comes up when I try updating from terminal and same with Synaptic. 
This also prevents me from updating from 9.04 to 9.10.

How can I correct this problem?


W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.gz](http://ftp.iitm.ac.in/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.gz)  404 Not Found

---

