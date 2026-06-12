---
title: "Random Shutdowns"
date: 2005-06-17
forum: Desktop Environments
---

### Post by cmilhaus on 2005-06-17
This is become a growing irritation and issue:
I have a customer built older P-3 450 Desktop with nothing but Hoary installed on the hard disk. Recently, the computer just goes into a reboot mode on it's own, with no warning, and always when I am awat from the machine.
The urs log for the past few days reads like this:

Jun 15 08:11:15 localhost gconfd (bobm-6188): Exiting
Jun 15 08:11:16 localhost shutdown[5256]: shutting down for system reboot
Jun 15 08:16:37 localhost gconfd (bobm-6166): starting (version 2.10.0), pid 6166 user 'bobm'
Jun 15 08:16:37 localhost gconfd (bobm-6166): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 15 08:16:37 localhost gconfd (bobm-6166): Resolved address "xml:readwrite:/home/bobm/.gconf" to a writable configuration source at position 1
Jun 15 08:16:37 localhost gconfd (bobm-6166): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 15 08:16:54 localhost gconfd (bobm-6166): Resolved address "xml:readwrite:/home/bobm/.gconf" to a writable configuration source at position 0
Jun 16 07:56:56 localhost gconfd (root-24566): starting (version 2.10.0), pid 24566 user 'root'
Jun 16 07:56:56 localhost gconfd (root-24566): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 16 07:56:56 localhost gconfd (root-24566): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 16 07:56:56 localhost gconfd (root-24566): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 16 07:57:26 localhost gconfd (root-24566): SIGHUP received, reloading all databases
Jun 16 07:57:26 localhost gconfd (root-24566): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 16 07:57:26 localhost gconfd (root-24566): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 16 07:57:26 localhost gconfd (root-24566): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 16 09:08:13 localhost gconfd (bobm-6186): starting (version 2.10.0), pid 6186 user 'bobm'
Jun 16 09:08:13 localhost gconfd (bobm-6186): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 16 09:08:13 localhost gconfd (bobm-6186): Resolved address "xml:readwrite:/home/bobm/.gconf" to a writable configuration source at position 1
Jun 16 09:08:13 localhost gconfd (bobm-6186): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 16 09:08:32 localhost gconfd (bobm-6186): Resolved address "xml:readwrite:/home/bobm/.gconf" to a writable configuration source at position 0
Jun 17 08:29:21 localhost shutdown[5242]: shutting down for system halt
Jun 17 08:33:48 localhost gconfd (bobm-6159): starting (version 2.10.0), pid 6159 user 'bobm'
Jun 17 08:33:48 localhost gconfd (bobm-6159): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 17 08:33:48 localhost gconfd (bobm-6159): Resolved address "xml:readwrite:/home/bobm/.gconf" to a writable configuration source at position 1
Jun 17 08:33:48 localhost gconfd (bobm-6159): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 17 08:34:05 localhost gconfd (bobm-6159): Resolved address "xml:readwrite:/home/bobm/.gconf" to a writable configuration source at position 0
Jun 17 09:18:42 localhost gconfd (bobm-6173): starting (version 2.10.0), pid 6173 user 'bobm'
Jun 17 09:18:42 localhost gconfd (bobm-6173): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 17 09:18:42 localhost gconfd (bobm-6173): Resolved address "xml:readwrite:/home/bobm/.gconf" to a writable configuration source at position 1
Jun 17 09:18:42 localhost gconfd (bobm-6173): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 17 09:19:00 localhost gconfd (bobm-6173): Resolved address "xml:readwrite:/home/bobm/.gconf" to a writable configuration source at position 0

The daemon log seems not to contain anything pertinant.
Does anyone have a solution to this? It has only been since Hoary was installed that this occured, Warty ran like a gem!

Very confused user  :^o

---

### Post by intangible on 2005-06-17
Since it is always happening when you are away from the computer, it may be trying to go into some kindof powersave mode.  Do a search in Synaptic and remove **laptop-mode acpi acpid acpi-support**.  Another thing it could be is maybe one of the GL screensavers is hitting some kindof issue with the video card, try just using standard blank screen for a screen saver and disabling Power Management for the monitor.  Hopefully that will keep you going, then you can start reenabling those things and see if any of them shut down the computer.

---

### Post by cmilhaus on 2005-06-23
Thank you for the good advice, I turned off the OpenGL Flying Toasters Screensaver and this did the trick. Not a random shut down since.
Many many thanks

 \\:D/

---

### Post by sal on 2005-07-26
[QUOTE=intangible]Since it is always happening when you are away from the computer, it may be trying to go into some kindof powersave mode.  Do a search in Synaptic and remove **laptop-mode acpi acpid acpi-support**.  Another thing it could be is maybe one of the GL screensavers is hitting some kindof issue with the video card, try just using standard blank screen for a screen saver and disabling Power Management for the monitor.  Hopefully that will keep you going, then you can start reenabling those things and see if any of them shut down the computer.[/QUOTE]

if i remove the packages you mention will i still be able to have the computer shut down with out having to push the power button?

---

### Post by intangible on 2005-07-27
I believe so, but give it a try, you can always reinstall them.

---

