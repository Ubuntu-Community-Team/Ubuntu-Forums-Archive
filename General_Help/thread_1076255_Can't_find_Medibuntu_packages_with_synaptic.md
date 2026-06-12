---
title: "Can't find Medibuntu packages with synaptic"
date: 2009-02-21
forum: General Help
---

### Post by groundnut on 2009-02-21
I've added medibuntu to the third party software sources.
I would like to install skype and adobe/acrobat reader with synaptic.
However these packages are not displayed when I search for them.

Medibuntu is activated in the sofware souces. I also reloaded synaptic.

Why can't I find these packages with synaptic?

---

### Post by taurus on 2009-02-21
How did you add Medibuntu to your repos exactly?  Did you add it to /etc/apt/sources.list or /etc/apt/sources.list.d?

---

### Post by philinux on 2009-02-21
Click the medibuntu link below and follow all instructions.

---

### Post by groundnut on 2009-02-21
I used the terminal with the following commands for Ubuntu 8.10 "Intrepid Ibex":

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by taurus on 2009-02-21
What's the output of this command from a terminal?

```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by groundnut on 2009-02-21
the response is:

## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by taurus on 2009-02-21
What happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get install skype
```

---

### Post by groundnut on 2009-02-21
first command:

Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid Release.gpg
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/main Translation-nl              
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/restricted Translation-nl      
Geraakt [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                     
Genegeerd [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-nl           
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg               
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-nl     
Genegeerd [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-nl       
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-nl
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-nl 
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-nl
Geraakt [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/universe Translation-nl          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/multiverse Translation-nl
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates Release.gpg
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main Translation-nl
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/restricted Translation-nl
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/universe Translation-nl
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/multiverse Translation-nl
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid Release
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates Release
Geraakt [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Geraakt [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages             
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/main Packages                    
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/restricted Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/main Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/restricted Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/universe Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/universe Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/multiverse Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/restricted Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/restricted Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/universe Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/universe Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/multiverse Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/multiverse Sources
Pakketlijsten worden ingelezen... Klaar

---

### Post by groundnut on 2009-02-21
second command:

Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
De volgende pakketten zijn automatisch geïnstalleerd en zijn niet langer nodig:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
U kunt deze verwijderen via 'apt-get autoremove'.
De volgende extra pakketten zullen geïnstalleerd worden:
  libaudio2 libmysqlclient15off libqt4-dbus libqt4-designer libqt4-network
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml
  libqtcore4 libqtgui4 mysql-common qt4-qtconfig skype-common
Voorgestelde pakketten:
  nas libqt4-dev
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  libaudio2 libmysqlclient15off libqt4-dbus libqt4-designer libqt4-network
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml
  libqtcore4 libqtgui4 mysql-common qt4-qtconfig skype skype-common
0 pakketten opgewaardeerd, 16 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
Er moeten 28,8MB aan archieven opgehaald worden.
Door deze operatie zal er 54,4MB extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? j
Ophalen:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/main libaudio2 1.9.1-4 [80,3kB]
Ophalen:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free skype-common 2.0.0.72-0medibuntu4 [2426kB]
Ophalen:3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/main mysql-common 5.0.67-0ubuntu6 [60,7kB]
Ophalen:4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid/main libmysqlclient15off 5.0.67-0ubuntu6 [1841kB]
Ophalen:5 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqtcore4 4.4.3-0ubuntu1.2 [2085kB]
Ophalen:6 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqt4-xml 4.4.3-0ubuntu1.2 [112kB]
Ophalen:7 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqt4-dbus 4.4.3-0ubuntu1.2 [216kB]
Ophalen:8 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqt4-script 4.4.3-0ubuntu1.2 [420kB]
Ophalen:9 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqtgui4 4.4.3-0ubuntu1.2 [4286kB]
Ophalen:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free skype 2.0.0.72-0medibuntu4 [13,1MB]
Ophalen:11 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqt4-designer 4.4.3-0ubuntu1.2 [2073kB]
Ophalen:12 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqt4-network 4.4.3-0ubuntu1.2 [437kB]
Ophalen:13 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqt4-sql 4.4.3-0ubuntu1.2 [109kB]
Ophalen:14 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqt4-qt3support 4.4.3-0ubuntu1.2 [1366kB]
Ophalen:15 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main libqt4-sql-mysql 4.4.3-0ubuntu1.2 [33,7kB]
Ophalen:16 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) intrepid-updates/main qt4-qtconfig 4.4.3-0ubuntu1.2 [109kB]
28,8MB opgehaald in 23s (1250kB/s)                                             
Selecteren van voorheen niet geselecteerd pakket libaudio2.
(Database inlezen ... 116537 bestanden en mappen geïnstalleerd.)
Uitpakken van libaudio2 (uit .../libaudio2_1.9.1-4_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket mysql-common.
Uitpakken van mysql-common (uit .../mysql-common_5.0.67-0ubuntu6_all.deb) ...
Selecteren van voorheen niet geselecteerd pakket libmysqlclient15off.
Uitpakken van libmysqlclient15off (uit .../libmysqlclient15off_5.0.67-0ubuntu6_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqtcore4.
Uitpakken van libqtcore4 (uit .../libqtcore4_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqt4-xml.
Uitpakken van libqt4-xml (uit .../libqt4-xml_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqt4-dbus.
Uitpakken van libqt4-dbus (uit .../libqt4-dbus_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqt4-script.
Uitpakken van libqt4-script (uit .../libqt4-script_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqtgui4.
Uitpakken van libqtgui4 (uit .../libqtgui4_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqt4-designer.
Uitpakken van libqt4-designer (uit .../libqt4-designer_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqt4-network.
Uitpakken van libqt4-network (uit .../libqt4-network_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqt4-sql.
Uitpakken van libqt4-sql (uit .../libqt4-sql_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqt4-qt3support.
Uitpakken van libqt4-qt3support (uit .../libqt4-qt3support_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket libqt4-sql-mysql.
Uitpakken van libqt4-sql-mysql (uit .../libqt4-sql-mysql_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket qt4-qtconfig.
Uitpakken van qt4-qtconfig (uit .../qt4-qtconfig_4.4.3-0ubuntu1.2_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket skype-common.
Uitpakken van skype-common (uit .../skype-common_2.0.0.72-0medibuntu4_all.deb) ...
Selecteren van voorheen niet geselecteerd pakket skype.
Uitpakken van skype (uit .../skype_2.0.0.72-0medibuntu4_i386.deb) ...
Processing triggers for man-db ...
Instellen van libaudio2 (1.9.1-4) ...

Instellen van mysql-common (5.0.67-0ubuntu6) ...
Instellen van libmysqlclient15off (5.0.67-0ubuntu6) ...

Instellen van libqtcore4 (4.4.3-0ubuntu1.2) ...

Instellen van libqt4-xml (4.4.3-0ubuntu1.2) ...

Instellen van libqt4-dbus (4.4.3-0ubuntu1.2) ...

Instellen van libqt4-script (4.4.3-0ubuntu1.2) ...

Instellen van libqtgui4 (4.4.3-0ubuntu1.2) ...

Instellen van libqt4-designer (4.4.3-0ubuntu1.2) ...

Instellen van libqt4-network (4.4.3-0ubuntu1.2) ...

Instellen van libqt4-sql (4.4.3-0ubuntu1.2) ...

Instellen van libqt4-qt3support (4.4.3-0ubuntu1.2) ...

Instellen van libqt4-sql-mysql (4.4.3-0ubuntu1.2) ...
Instellen van qt4-qtconfig (4.4.3-0ubuntu1.2) ...

Instellen van skype-common (2.0.0.72-0medibuntu4) ...
Instellen van skype (2.0.0.72-0medibuntu4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by taurus on 2009-02-21
Looks like skype is now installed.

---

### Post by groundnut on 2009-02-21
Now Skype is installed.

However I still can't find Skype and Adobe/Acrobat reader with Synaptic.

---

### Post by taurus on 2009-02-21
Did you use the **Search** function in synaptic to search for skype and/or adobe?

---

### Post by jocko on 2009-02-21
> **groundnut said:**
> Now Skype is installed.

However I still can't find Skype and Adobe/Acrobat reader with Synaptic.
Use the real search function in synaptic (= click the button "search"), not the quick search function (the text box on the toolbar, which only filters the packages you are already listing).

---

### Post by drs305 on 2009-02-21
> **groundnut said:**
> Now Skype is installed.

However I still can't find Skype and Adobe/Acrobat reader with Synaptic.

Acrobat Reader is listed as *acroread* in synaptic and is available for use via the Applications, Office menu.

---

### Post by groundnut on 2009-02-21
I used the quick search and the search button in synaptic to search for skype, acroread and adobe?

I did not find the skype and the acroread packages.

---

### Post by drs305 on 2009-02-21
> **groundnut said:**
> I used the quick search and the search button in synaptic to search for skype, acroread and adobe?

I did not find the skype and the acroread packages.

If you type *acroread* in a terminal does it start Adobe Acrobat? If so and you need a launcher because you can't find it in the Office section menu:
Right click on the panel, Add to Panel, Custom Application Launcher (if you don't see it listed), and type *acroread* in the command input box.

---

### Post by groundnut on 2009-02-21
I have not yet installed acroread.

I would like to use Synaptic for that.

But Synaptic does not show acroread which it should since Medibuntu has been installed.

---

### Post by groundnut on 2009-02-22
I have just installed the acroread and mozilla-acroread packages with sudo apt-get install. No problem.

However I would have preferred to use Synaptic.

For some reason these packages are not shown with Synaptic.

Nevertheless I got what I wanted.

Thanks from everyone.

---

