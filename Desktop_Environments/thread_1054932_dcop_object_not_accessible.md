---
title: "dcop object not accessible"
date: 2009-01-30
forum: Desktop Environments
---

### Post by ScottyDelicious on 2009-01-30
When I press the power button on my laptop it goes straight to shutdown without prompting so I looked in /etc/acpi/powerbtn.sh and found this:

```
/usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 1 2 0
```
I wondered why it wasn't being called, so just to check, I ran it from the command line and it gave me the ambiguous error:
```
object not accessible
```

I am running Kubuntu 8.10.

---

### Post by ScottyDelicious on 2009-02-01
I did a little more tinkering. I downloaded OpenSuse 11.1 KDE live cd, burned it, and booted from it. While using the OpenSuse live CD, I pressed the power button and was surprised to see the log out prompt I was expecting with Kubuntu actually worked in OpenSuse. The good news is that it is not a hardware problem like I was starting to suspect, but the bad news is that my beloved Kubuntu is doing something very wrong on my machine.

I tried to copy the OpenSuse power button script (I think it is /usr/lib/acpid/power_button.sh) to my Kubuntu /usr/acpi/powerbtn.sh, but running it from the command line gives different, but equally disappointing errors and naturally after rebooting to make sure the script is reloaded, the power button still sends my machine into 'shutdown -h now'. Unfortunately it was not the easy fix I had hoped for. I am sticking with it for now. I love Ubuntu and I am very interested in getting familiar with KDE 4, but this is really pissing me off! Arrgghh :(

---

### Post by olifhar on 2009-06-02
I've had the same problem. I found out [elsewhere]("http://kubuntuforums.net/forums/index.php?topic=3103016.0#top") that in KDE 4+ dcop has been replaced:
> With the KDE 4 the dcop was replaced by the qdbus.

Turning off + 30 sec warning (konsole):
```
qdbus org.kde.ksmserver /KSMServer org.kde.KSMServerInterface.logout 1 2 2
```

[[img]http://www.freeimagehosting.net/uploads/965ccaf15e.jpg[/img]](http://www.freeimagehosting.net/)

and those numbers are working same way as with the dcop (i think  ;)).
1 2 2 = ShutdownConfirmYes ShutdownTypeHalt ShutdownModeForceNow

Package: qt4-dev-tools (Jaunty) has a handy tool: qdbusviewer

[[img]http://www.freeimagehosting.net/uploads/th.0dca241e6d.jpg[/img]](http://www.freeimagehosting.net/image.php?0dca241e6d.jpg)

It is a qdbus viewer/browser...


The KShutdown is also in the official Jaunty repositories >  [Topic: KDE 4.2 RC: Shutdown computer withou logging out to KDM](http://kubuntuforums.net/forums/index.php?topic=3101047.0)


A plasma-widget > [LogOut](http://www.kde-look.org/content/show.php/LogOut?content=98934)
[QUOTE]Description:
This is a modification of the lock/logout plasmoid. It's for those like me, who just need the logout button on the desktop or panel.[/QUOTE]

None of this worked for me, but perhaps it might be of help to others.

---

