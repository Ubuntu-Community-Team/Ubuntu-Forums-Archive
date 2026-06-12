---
title: "Since Update to Jaunty problems with Webvideos"
date: 2009-05-04
forum: General Help
---

### Post by tux1527 on 2009-05-04
Hi all!

I assume that I've a special problem but still:

Until my distribution - upgrade to Ubuntu 9.04 any Video - Website worked well without any problems in Firefox. BUT: Afterwards, almost any video on the net except ww.youtube.com refused to work properly, though I've installed the latest versions of all plugins needed! (java, swf, flash,...) And at youtube fullscreen appears to have problems, too. 
All I see at myspace.com for instance, is a black screen or even nothing. Ok, there is a grey arrow in a circle sometimes, but when I click on it, nothing happens!

Oh well, I forgot liveradio on special sites doesn't work either!!!

May you take a look on my output of about : plugins, maybe I've overseen something yet...

In desparation I have tried to reinstall anything that has to do with firefox using Synaptic. When I wanted to install the required plugins the following error occured:
(Sorry, I'm using a german copy of Ubuntu, I hope it helps you to give some hints anyway! :-)
 
```

root@billtux-laptop:~# aptitude install mozilla-mplayer
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Lese erweiterte Statusinformationen      
Initialisiere Paketstatus... Fertig
Die folgenden teilweise installierten Pakete werden konfiguriert:
  adobe-flashplugin flashplugin-installer 
0 Pakete aktualisiert, 0 zusätzlich installiert, 0 werden entfernt und 2 nicht aktualisiert.
Muss 0B an Archiven herunterladen. Nach dem Entpacken werden 0B zusätzlich belegt sein.
Schreibe erweiterte Statusinformationen... Fertig
Richte adobe-flashplugin ein (10.0.22.87-2jaunty1) ...
update-alternatives: Kann /usr/lib/firefox/plugins/flashplugin-alternative.so.dpkg-tmp nicht zu symbolischem Link auf /etc/alternatives/firefox-flashplugin machen: No such file or directory
dpkg: Fehler beim Bearbeiten von adobe-flashplugin (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Richte flashplugin-installer ein (10.0.22.87ubuntu2) ...
cd: 143: can't cd to /var/cache/flashplugin-installer
dpkg: Fehler beim Bearbeiten von flashplugin-installer (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 adobe-flashplugin
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ein Paket konnte nicht installiert werden. Versuche zu lösen:
Paketlisten werden gelesen... Fertig             
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Lese erweiterte Statusinformationen      
Initialisiere Paketstatus... Fertig

root@billtux-laptop:~# 

```Can somebody give me some advice? I would look forward to it.

Best grace in advance, 

Yours, 
Martin

---

### Post by tux1527 on 2009-05-04
Hi again!

Now, I did what's recommended on [http://ubuntuforums.org/showthread.php?t=1130582&highlight=jaunty+intel](http://ubuntuforums.org/showthread.php?t=1130582&highlight=jaunty+intel)

In system the playing of videos works better, but in firefox there are still no changes! 
I assume there's just a problem with the flashplayer-plugin! But how can I fix that? 

Currently, I have to run Virtual Windows (Virtual Box) to watch some videos online! :-(

Here's the output of lspci -v:

```

VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Kernel modules: nvidiafb

```Thank you in advance for further advice. 

Yours, Martin

---

