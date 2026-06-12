---
title: "CUPS installation failes"
date: 2007-03-05
forum: Desktop Environments
---

### Post by Whinegum on 2007-03-05
Hi. Hi hope I put my problem under the right topic.
I've got a problem with installing the cupsys-package... I removed it because of some problems before... Sorry for my bad language, but in the German forums I didn't find any solution.
First I got this error message:
```

ralf@localhost:/var/cache$ sudo apt-get install cupsys
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Vorgeschlagene Pakete:
  cupsys-driver-gutenprint cupsys-driver-gimpprint foomatic-filters-ppds
  xpdf-korean xpdf-japanese xpdf-chinese-traditional xpdf-chinese-simplified
  cups-pdf hplip
Die folgenden NEUEN Pakete werden installiert:
  cupsys
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 1463kB Archiven geholt werden.
Nach dem Auspacken werden 6521kB Plattenplatz zusätzlich benutzt.
Vorkonfiguration der Pakete ...
Wähle vormals abgewähltes Paket cupsys.
(Lese Datenbank ... 119662 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke cupsys (aus .../cupsys_1.2.4-2ubuntu3_i386.deb) ...
Richte cupsys ein (1.2.4-2ubuntu3) ...
chown: Zugriff auf &#8222;/etc/cups/cupsd.conf&#8220; nicht möglich: No such file or directory
dpkg: Fehler beim Bearbeiten von cupsys (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Then I generated an empty cupsd.conf with the following command.
```
sudo touch /etc/cups/cupsd.conf
```

But my Error message didn't disappeared. It only changed to:

```

ralf@localhost:/var/cache$ sudo apt-get install cupsys
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Vorgeschlagene Pakete:
  cupsys-driver-gutenprint cupsys-driver-gimpprint foomatic-filters-ppds xpdf-korean xpdf-japanese xpdf-chinese-traditional xpdf-chinese-simplified
  cups-pdf hplip
Die folgenden NEUEN Pakete werden installiert:
  cupsys
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 1463kB Archiven geholt werden.
Nach dem Auspacken werden 6521kB Plattenplatz zusätzlich benutzt.
Vorkonfiguration der Pakete ...
Wähle vormals abgewähltes Paket cupsys.
(Lese Datenbank ... 119652 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke cupsys (aus .../cupsys_1.2.4-2ubuntu3_i386.deb) ...
Richte cupsys ein (1.2.4-2ubuntu3) ...
 * Starting Common Unix Printing System: cupsd                                                                                                               cupsd: Child exited on signal 15!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: Fehler beim Bearbeiten von cupsys (--configure):
 Unterprozess post-installation script gab den Fehlerwert 3 zurück
Fehler traten auf beim Bearbeiten von:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
```

Does anyone know, what to do? I've got ubuntu 6.10. I upgraded from 5.06

---

### Post by blazerw on 2007-03-14
I have a very similar issue to yours, except:
I'm on Feisty (7.04) and mine exits with error code 2. Anyway, look in /var/log/cups/error_log and see if there are any meaningful messages that might help you or others diagnose this. Mine has the following error in it:
```
X [14/Mar/2007:10:57:01 -0500] Unable to load MIME database from '/usr/share/cups/mime:/etc/cups'!
```

---

### Post by floke on 2007-03-14
Ditto for the cups error on Feisty following update

---

### Post by blazerw on 2007-03-14
> **Steve.K said:**
> Ditto for the cups error on Feisty following update

A new version was posted just a bit ago that fixes the issue, you can get it here (note, link is to the i386 version):
[https://bugs.launchpad.net/ubuntu/feisty/i386/cupsys/1.2.8-0ubuntu6](https://bugs.launchpad.net/ubuntu/feisty/i386/cupsys/1.2.8-0ubuntu6)

The deb on the above page installed fine for me.  It'll probably propagate to your repository soon, so in a couple of hours you can also:
```
sudo apt-get update
sudo apt-get upgrade
```

Or, System -> Administration -> Update Manager,
Click "Check"
If it lists "cupsys", then click "install updates".

-Randy

---

