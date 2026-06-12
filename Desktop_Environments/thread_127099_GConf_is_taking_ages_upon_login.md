---
title: "GConf is taking ages upon login"
date: 2006-02-08
forum: Desktop Environments
---

### Post by itmarshall on 2006-02-08
Hi all,

I have been "playing around" with my Breezy laptop (IBM T41) because of the installation of a new PCMCIA wireless card, and the disabling of the inbuilt ethernet card.

After disabling the ethernet card (in /etc/network/interfaces) I have noticed that it takes several minutes for GNOME to start loading after I've entered in my login details. The delay is after entering in my user name/password in GDM, and before the splash screen with the loading status icons appears - just a blank brown monitor.

Examination of the /var/log/messages file makes it look like a problem with gconf. I have pasted some of the output below. I have tried deleting my ~/.gconf and ~/.gconfd directories to no avail.

Have I stuffed something up badly? And if so, how do I un-stuff it? ;)
Any pointers as to *how* GDM starts up a GNOME session would be helpful too.

Thanks in advance,
Ian

=====

The log output (pertaining to the gconf entries) is below. Note the time difference between the last two lines.


Feb  8 22:15:52 localhost gconfd (itmarshall-10025): starting (version 2.12.0), pid 10025 user 'itmarshall'
Feb  8 22:15:52 localhost gconfd (itmarshall-10025): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  8 22:15:52 localhost gconfd (itmarshall-10025): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb  8 22:15:52 localhost gconfd (itmarshall-10025): Resolved address "xml:readw
rite:/home/itmarshall/.gconf" to a writable configuration source at position 2
Feb  8 22:15:52 localhost gconfd (itmarshall-10025): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb  8 22:15:52 localhost gconfd (itmarshall-10025): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb  8 22:15:52 localhost gconfd (itmarshall-10025): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb  8 22:15:52 localhost gconfd (itmarshall-10025): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb  8 22:15:52 localhost gconfd (itmarshall-10025): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only
configuration source at position 7
Feb  8 22:19:06 localhost gconfd (itmarshall-10025): Resolved address "xml:readwrite:/home/itmarshall/.gconf" to a writable
configuration source at position 0

---

### Post by itmarshall on 2006-02-13
Replying to my own post here...

 I don't know if anyone is still interested in my problem, but it's fixed now. \\:D/  It seems that I'd somehow stupidly commented out the "auto lo"  line from /etc/network/interfaces, disabling the loopback connection!

Quite how the system ran as well as it did without a loopback, I don't understand, but hey, the Linux box kept going *despite* gross stupidity by the sys admin (me)!

---

### Post by suxen on 2006-02-22
Hi,
i have the same trouble. Could you post your /etc/network/interfaces file?

---

