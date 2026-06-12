---
title: "Howto sync PocketPC with dapper / kubuntu?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by scotty64 on 2006-07-24
I want to synchronize my Windows Mobile 2003 PDA with Ubuntu/Dapper (either Evolution or KDEPim), preferrably bluetooth, but USB is o.k. The information I found on the web is all very fragmented and nothing worked until now.
I found a howto for Hoary in these forums, but SynCE just does not work as it should: 
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
starting dccm -f tells me it is listening on port 5679.
Has anybody got PocketPC syncing going with dapper?
BTW: My PDA is a Fujitsu-Siemens LOOX 710

---

### Post by mdbarton on 2006-07-26
I gave up trying to get this working and have resorted to running windows under vmware server.

---

### Post by Mouth on 2006-07-26
Yes, I too gave up getting it to work.

---

### Post by andreh on 2007-03-13
Building SynCE with Windows Mobile 2005 support from Subversion
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion)

[http://www.opensync.org/wiki/DeviceCompatibilityList](http://www.opensync.org/wiki/DeviceCompatibilityList)

> LDAP Plugin
Moto Plugin
Opie Plugin
Palm Plugin
Python Plugin
Sunbird Plugin
Synce Plugin ¶
How could i sync my WM5 device?
[b]
The libopensync-plugin-synce in OpenSync is currently not able to sync with WM5 devices.
There exist a in project for syncing OpenSync with WM5 Devices. 
SyncML[/b]

[http://www.opensync.org/wiki/syncml-guide](http://www.opensync.org/wiki/syncml-guide) 
I got Error XYZ ... what does it mean?

[[http://libsyncml.opensync.org/wiki/ErrorCodes]](http://libsyncml.opensync.org/wiki/ErrorCodes])
[http://www.opensync.org/wiki/DeviceCompatibilityList](http://www.opensync.org/wiki/DeviceCompatibilityList)

Building SynCE with Windows Mobile 2005 support from Subversion
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion)


The ACCESS Linux Platform enables the creation of world-class mobile devices and mobile services by providing a complete and flexible commercial-grade Linux® based operating system designed for the worldwide mobile and converged device markets.
[http://www.access-company.com/products/linux/alp.html](http://www.access-company.com/products/linux/alp.html)

---

### Post by andreh on 2007-03-19
Hoi,
Is er trouwens iemand die een van de volgende toestellen werkend/verbonden  heeft gekregen onder Linux ?

Een **smartphone met GPS (SPV M2000/QTEK 9090/HTC Blue Angel/MDA III of een SPV M3000/QTEK9100/HTC Wizard/MDA Vario )**

of

een **PDA met GPS ( Mio P350 , Mio P550 , QTEC g100 of ASUS 632N )** .


De Ubuntu bible is overigens een zeer goed boek

** Uit de Linux Bible (aanrader !!)  pag 508 Settings vor PDA Synchronisation **
> **Configuring PDA and Smart Phone Recognition**
The GNOME desktop recognizes PDAs running the Palm OS, PDAs running Microsoft Windows CE, PDAs
running Microsoft Windows, Pocket PC edition, and most types of smart phones running any of these oper-
ating systems, and can be configured to automatically run specific applications when a device running the
Palm OS or some teeny, tiny version of Windows is connected and you request synchronization. These are
all considered to be PDAs by Ubuntu Linux. Configuring how and if your system recognizes different types
of PDAs is done by selecting the System &#10154; Preferences &#10154; Removable Drives and Media Preferences, and
then selecting the PDAs tab, as shown in the dialog in Figure 17.3.

    * ** PDAs running Palm OS: Select the Sync Palm** devices when connected checkbox to activate a
         specified application when you request synchronization from your Palm. When this checkbox is
         selected, Ubuntu is configured to run the gpilotd-control-applet panel applet when a
         Palm Sync event is detected. You can specify another application or shell script to run on sync
         by clicking Browse and navigating to that application in the Select program to sync Palm device
         dialog that displays.
    * ** PDAs running Microsoft Windows: Select the Sync PocketPC** devices when connected check-
         box to activate a specified application when you request synchronization from your PocketPC
         or other **Windows CE device**. When this checkbox is selected, Ubuntu is configured to run the
         multisync application when a PocketPC Sync event is detected. You can specify another appli-
         cation or shell script to run on sync by clicking Browse and navigating to that application in the
         Select program to sync PocketPC device dialog that displays.
Depending on the operating system that your PDA uses, you must configure the[b] gpilotd-control-
applet or multisync[/b] applications before you can successfully synchronize data in either direction. See
&#8220;PDAs, Smart Phones, and Ubuntu&#8221; later in this chapter for details.

**PDAs, Smart Phones, and Ubuntu**
Personal Digital Assistants are a great tool for simple tasks such as managing calendars and making quick
notes. If yours is network-enabled and your eyesight is good enough, it&#8217;s also possible to browse the Web,
send and receive e-mail, and even work with documents in a variety of popular desktop software formats,
all from a device that you can easily tuck into a purse or shirt pocket. All of the software that you need to
synchronize a PDA that runs the Palm OS comes preinstalled on your Ubuntu system, and the software to
synchronize a Microsoft Windows for PocketPC or Microsoft Windows CE PDA is just a repository away.
The next two sections discuss how to install, configure, and use the software that you&#8217;ll need to synchronize
almost any PDA with the data stored on your Ubuntu Linux system.

** Configuring and Synchronizing Palm OS Devices**
 As discussed in &#8220;Configuring PDA and Smart Phone Recognition&#8221; earlier in this section, a standard Ubuntu
 Linux installation includes a panel applet called gpilot. (This application is also sometimes referred to as
 gnome-pilot, its package name, or as pilot-link.) The section of Chapter 5 entitled &#8220;Customizing
 Panel Contents&#8221; explained how to add an applet to the panel &#8212; in a nutshell, click on the panel, select the
 applet that you want to add from the dialog that displays, and drag it to the panel location where you want
 it to appear. The panel applet synchronizing with PDA running the Palm OS is called &#8220;Pilot Applet,&#8221; and is
 located in the utilities section of the Add to Panel dialog.
 Once you add the gpilot applet to your panel, you&#8217;ll need to configure how it communicates with your
 Palm.
                 The first time that you start the gpilot applet, it displays a wizard that walks you through the
TIP              configuration process. These steps are the same as those discussed in this section and occur in
 the same sequence. This section discusses them as manual steps because the gpilot wizard only runs the
 first time that you start gpilot &#8212; if you ever need to reconfigure or modify your synchronization settings,
 you&#8217;ll need to do that manually, as described in this section.

[http://ubuntuforums.org/showthread.php?t=136257](http://ubuntuforums.org/showthread.php?t=136257) (vertrouwde link)

De Ubuntu bible is overigens een zeer goed boek.
Connecten met mobile phone MDA VARIO
[http://forum.ubuntu-nl.org/topic/8159](http://forum.ubuntu-nl.org/topic/8159)

Sync your Pocket PC with Ubuntu **Dell Axim Pocket PC with Ubuntu Edgy.** 
I have reached the point of establishing the connection with my pocket PC and listing the files in there. I haven&#8217;t yet started working on syncing Evolution or other programs with my pocket PC. I&#8217;m not sure if the instructions **here will work with new pocket PCs (with new Windows mobile OS).**
[http://www.blog.arun-prabha.com/2007/02/21/how-to-sync-your-pocket-pc-with-ubuntu/](http://www.blog.arun-prabha.com/2007/02/21/how-to-sync-your-pocket-pc-with-ubuntu/)

> [http://www.mail-archive.com/synce-devel@lists.sourceforge.net/index.html#00398](http://www.mail-archive.com/synce-devel@lists.sourceforge.net/index.html#00398)

I'm trying to connect a pocket pc to Ubuntu 6.10. When I connect the
device Linux seems to pick it up correctly but then disconnects almost
immediately. Below is the output from dmesg. I've
checked /proc/bus/usb/devices and for a short while it also lists the
device correctly. Does anyone have any suggestions?

   Thanks,
    Rich


[17187573.004000] usb 3-2: new full speed USB device using uhci_hcd and
address 4
[17187573.172000] usb 3-2: configuration #1 chosen from 1 choice
[17187573.172000] ipaq 3-2:1.0: PocketPC PDA converter detected
[17187573.176000] usb 3-2: PocketPC PDA converter now attached to


[http://www.mail-archive.com/synce-devel@lists.sourceforge.net/index.html#00398](http://www.mail-archive.com/synce-devel@lists.sourceforge.net/index.html#00398)

[http://sourceforge.net/mailarchive/forum.php](http://sourceforge.net/mailarchive/forum.php)
> Artikel Januari 2007[b]The purpose of this guide is to allow newer *WM5 devices like HTC Wizard, Prophet to connect to Ubuntu Edgy 6.10*and be able to share files, install stuff. This guide will take about one hour to complete, depending on your skills etc.
First, let's install synce-trayicon. It won't work yet, but when we're done, it will give you a tray icon like this:[/b]
[http://ubuntuforums.org/showthread.php?p=2181420](http://ubuntuforums.org/showthread.php?p=2181420)
> **Connecting your Windows Mobile 2005 device via USB (usb-rndis-lite)**
These instructions let you connect your Windows Mobile 2005 device, via USB, to your computer, using the usb-rdnis-lite kernel module.
[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_%28usb-rndis-lite%29](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_%28usb-rndis-lite%29)
> [http://foro.todopocketpc.com/showthread.php?t=133646&page=3](http://foro.todopocketpc.com/showthread.php?t=133646&page=3)
Buscando por ahí la forma de instalar Linux en mi iPaq (misión imposible por ahora, según parece) me he encontrado con esto. Se refiere a la iPaq 1950, modelo que lleva incluido WM5.

[b]Cita textual:
No funciona en Linux. Parece que el problema está en el protocolo de comunicaciones RNDIS del nuevo Windows Mobile 5.0 porque en[/b] anteriores versiones si que funciona la sincronización. El protocolo está cerrado a cal y canto para que sólo se pueda comunicar con lo que Microsoft dicte y mande, como no.
Por tanto no entiendo como hay gente que ha conseguido conectar una PDA con WM5 a Ubuntu Edgy

RECTIFICO: sí es posible instalar linux en la rx1950, hay quien lo ha conseguido. Ahora solo me falta aprender ruso [http://foro.todopocketpc.com/showthread.php?t=133646&page=3](http://foro.todopocketpc.com/showthread.php?t=133646&page=3)
> ** SYNCE overzicht email lijst Synchronisatie UBUNTU**
[http://www.mail-archive.com/synce-devel@lists.sourceforge.net/index.html#00398](http://www.mail-archive.com/synce-devel@lists.sourceforge.net/index.html#00398)
> ** Email Archive: synce-windowsmobile5 (read-only) **
WM5 devices are not supported via the HOWTO.
See the Windows Mobile 5 mailing list archives for info on how to
connect your WM5 device:
[http://sourceforge.net/mailarchive/forum.php?forum_id=47384](http://sourceforge.net/mailarchive/forum.php?forum_id=47384)
> Artikel oktober 2006
**La synchronisation evolution/pocketPC enfin Possible pour tous! **
Ces derniers temps j'ai essayé d'aider quelques personnes à synchronniser leur PPC avec evolution ([http://forum.ubuntu-fr.org/viewtopic.php?id=44245)](http://forum.ubuntu-fr.org/viewtopic.php?id=44245))... Je me suis rendu compte que j'étais assez chanceux car mon Qtek S100 fonctionne à peu près bien. J'ai dit à peu près car j'avais toujours quelques petits "bugs" de synchronisation... Des évennements ou des contacts qui refusent de se synchroniser par exemple... Donc j'ai poursuivi mes recherches pour essayer de trouver LA solution de synchronisation universelle.
Et je suis tombé sur ça:
[http://www.funambol.com/](http://www.funambol.com/)
> Gebruik vna synchronisatie bij Evolution: Via Synce
Outil de synchronisation pour evolution : syncevolution
[http://doc.ubuntu-fr.org/syncevolution](http://doc.ubuntu-fr.org/syncevolution)
> [http://www.funambol.com/](http://www.funambol.com/)
Funambol provides push email, PIM synchronization, and device management for mobile devices, with all the advantages of open source software.
We are the de facto standard implementation of SyncML, giving you greater strategic freedom and lower costs. We're also:
    * The world&#8217;s most popular mobile open source software project
    * Compatible with over 75% of the mobile phones shipping today
    * In production use on 5 continents
Funambol v3 GA software offers customized versions for mobile carriers, the open source community and enterprises. Read More »
[http://www.funambol.com/](http://www.funambol.com/)
> [http://de.wikipedia.org/wiki/Multisync](http://de.wikipedia.org/wiki/Multisync)
OpenSync ist ein Computerprogramm zur Synchronisation von Adressen, Kalendereinträgen und anderen Daten zwischen verschiedenen Geräten wie Computern, PDAs oder Handys.

Das Programm ist modular aufgebaut und Plugin-basiert. Die Synchronisation zwischen zwei Parteien A und B läuft dabei über die für A und B zuständigen Plugins ab, dabei können A und B sowohl Geräte als auch Programme sein. Sobald sich ein Datensatz einer Partei ändert, wird diese Änderung bei der anderen Partei repliziert. Es ist auch möglich, nur in eine Richtung oder auch automatisch zu synchronisieren, wenn sich z. B. ein Gerät in Reichweite befindet. Das Plugin-Konzept erlaubt eine einfache Anpassung des Programms an neue Geräte oder Programme, denn es muss lediglich ein neues Plugin erstellt werden, während die Synchronisationslogik immer gleich bleibt.
*Seit 22. April 2006 ist das Projekt der offizielle Nachfolger von Multisync geworden.*

 Plugins [Bearbeiten]

Im Moment sind folgende Plugins für Opensync verfügbar:

    * Ximian Evolution / Evolution 2 Synchronisation (Kalender, ToDos und Kontakte)
    * IrMC Mobile Client Synchronisation via Bluetooth-, Infrarot- oder kabelgebundener Verbindung (wird von vielen Handys unterstützt).
    * Synce Plugin für WinCE 2003 Geräte
    * Opie und Zaurus Synchronisation.
    * SyncML Support (erlaubt auch eine verschlüsselte Verbindung zweier Multisync-Instanzen über das Internet).
    * Palm Synchronisation.
    * LDAP Synchronisation.
    * Plugin zu Synchronisation mit KDE PIM
    * Plugin zur Filesynchronisation von PIM Daten und anderen Dateien / Verzeichnissen.
    * Gnokii Plugin zur Synchronisation über [1].
    * Sunbird Plugin für dir Synchronisation über WebDAV.
    * Moto Plugin für Synchronisation zu Motorola L7 oder RAZR.
    * Google Calendar Plugin
    * Jescs Plugin (Java Enterprise System Calendar)

    * Windows CE / Pocket PC Synchronisation für WM5. Dieses Plugin ist Teil des SynCE-Projektes und kann von dort heruntergeladen werden.

[http://de.wikipedia.org/wiki/Multisync](http://de.wikipedia.org/wiki/Multisync)
[http://de.wikipedia.org/wiki/Microsoft_Pocket_PC](http://de.wikipedia.org/wiki/Microsoft_Pocket_PC)
> [http://www.synce.org/index.php/Windows_Mobile](http://www.synce.org/index.php/Windows_Mobile)
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
[http://www.synce.org/index.php/Windows_Mobile_2005_Support](http://www.synce.org/index.php/Windows_Mobile_2005_Support)
[http://www.funambol.com/opensource/](http://www.funambol.com/opensource/)
Windows Mobile is a compact operating system combined with a suite of basic applications for mobile devices based on the Microsoft Win32 API. Devices which run Windows Mobile include Pocket PCs, Smartphones, and Portable Media Centers. It is designed to be somewhat similar to desktop versions of Windows.[1]
SynCE has support for Smartphones and Pocket PCs, using Windows CE, Windows Mobile 2003 and Windows Mobile 2005. 
[http://www.synce.org/index.php/Windows_Mobile](http://www.synce.org/index.php/Windows_Mobile)

[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
Windows Mobile 2005, originally codenamed "Magneto", was released on May 9, 2005. It is powered by Windows CE 5.0 and uses the .NET Compact Framework 1.0 SP2 &#8212; an environment for programs based on .NET to be used.
SynCE has support for Windows Mobile 2005, on its support pages. 

[http://www.synce.org/index.php/Windows_Mobile](http://www.synce.org/index.php/Windows_Mobile)
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
[http://www.synce.org/index.php/Windows_Mobile_2005_Support](http://www.synce.org/index.php/Windows_Mobile_2005_Support)
[http://www.funambol.com/opensource/](http://www.funambol.com/opensource/)
> [http://ubuntuforums.org/showthread.php?p=2271744#post2271744](http://ubuntuforums.org/showthread.php?p=2271744#post2271744)
Yes, under ** Fiesty I can sync my HP Ipaq1930 with Evolution**, the contacts and calendar are perfect . The Howto worked first time with out problems.

 could sync an **eten m600 and a linux box using a vmware virtual machine to sync files and emails (w/ the virtual machine running windows) **.
> ** Bluetooth gsm sony-ericsson Z530 d  of [b] Sony K750i is**
[http://forum.ubuntu-nl.org/topic/8383](http://forum.ubuntu-nl.org/topic/8383)
[https://wiki.ubuntu.com/NlBluetooth?highlight=%28nlbluetooth%29](https://wiki.ubuntu.com/NlBluetooth?highlight=%28nlbluetooth%29)

Ik synchroniseer opie adresboek, calendar en todo met evolution. Dat werkt super. 
Dat schijnt overigens ook te kunnen tussen evo en pocketpc. 
Hier is een heel goed programma voor: multisync. 
[http://multisync.sourceforge.net/index.shtml](http://multisync.sourceforge.net/index.shtml)
[http://forum.nedlinux.nl/viewtopic.php?id=11836](http://forum.nedlinux.nl/viewtopic.php?id=11836)
> Volgens mij zou je al veel hulp kunnen bieden door uit te zoeken wat nu standaard wel zou moeten werken en wat niet.
Op internet slagen verscheidene mensen er nl wel in om hun Pocketpc aan de praat te krijgen.
Florian, Je spreekt hopelijk wel een beetje engels ?

Welke versies van Windows PocketPC worden nu wel ondersteunt..en welke niet ?
Welke fabrikanten met Windows PocketPC worden nu wel ondersteunt..en welke niet ?
Welke desktops/window mangers van Windows PocketPC worden nu wel ondersteunt..en welke niet ? Ik krijg de indruk dat er met KDE minder problemen zijn.
Welke mobile phones en PDA's van Windows PocketPC worden nu wel ondersteunt..en welke niet ?
> [http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
MultiSync is a free modular program to synchronize calendars, addressbooks and other PIM data between programs on your computer and other computers, mobile devices, PDAs or cell phones. MultiSync works on any Gnome platform, such as Linux.

Currently MultiSync has plugins for
Ximian Evolution synchronization, supporting calendar, ToDos and contacts. Multisync also support Evolution 2 
IrMC Mobile Client synchronization (supported by e.g. SonyEricsson T68i/T610/Z600, Siemens S55 phones etc.) via Bluetooth or IR on Linux, or cable connection. [b]
[Windows CE / Pocket PC synchronization](http://www.microsoft.com/windowsmobile/pocketpc/default.mspx). This plugin is part of the SynCE project, and can be downloaded there. 
Opie and Zaurus synchronization. [/b]
SyncML support (supported by e.g. SonyEricsson P800/P900 and many other phones and devices, for example the SyncML server Sync4j). SyncML also allows you to do remote connection of two MultiSync programs via an encrypted connection over the net. 
Palm synchronization. 
LDAP synchronization. 
Backup of your PIM data.
[http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
> [http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
Attention Windows Mobile 2005 device owners!

These devices do not work with SynCE. If you are interested in getting these 
[devices supported by SynCE, please join the SynCE-WindowsMobile5 mailing list](http://sourceforge.net/mailarchive/forum.php?forum=synce-windowsmobile5). Se also bug report 1332550.
[http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
> Voor Pocket PC Windwow Mobile 2005/2003 Moet je ** SyncCE ** gebruiken, CE zal wel voor Windows CE staan.
OpenSync zelf zal in elk geval niet werken. Onderstaande link is van 27 jan 2007
[http://www.synce.org/index.php/Syncing_via_OpenSync](http://www.synce.org/index.php/Syncing_via_OpenSync)


Building SynCE with Windows Mobile 2005 support from Subversion
These instructions build Windows Mobile 5 support for SynCE by using the latest bleeding edge software from SynCE's Subversion repository. 
You must have a Subversion client installed.
Distribution-Specific Build Scripts 

Some linux distribution's package management tools even allow subversion sources to be managed and uninstalled, therefore if you have one of those, it's probably best to use the package tool to install the wm5 branch of SynCE. If your distribution isn't listed, proceed to the manual instructions below.
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion)

---

