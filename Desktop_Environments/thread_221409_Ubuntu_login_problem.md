---
title: "Ubuntu login problem"
date: 2006-07-23
forum: Desktop Environments
---

### Post by protorion on 2006-07-23
Hi, 

For a couple of days I've had this strange problem.
When I log in my desktops starts to load. I see the splashscreen and the wallpaper. But when it has finished loading I'm kicked out to the login screen again. I repeat my login for a couple of times and suddenly everyting is normal again..
I understand that it can be a number of things so my question is: Where do I start looking? :) The problem is escalating, first time it was just a matter of loging back on one time, now I have to try 5-6 times.

I looked in messages and saw this: 

Jul 23 08:54:17 ubergamer2 gconfd (henrik-5002): starting (version 2.14.0), pid 5002 user 'henrik'
Jul 23 08:54:17 ubergamer2 gconfd (henrik-5002): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 23 08:54:17 ubergamer2 gconfd (henrik-5002): Resolved address "xml:readwrite:/home/henrik/.gconf" to a writable configuration source at position 1
Jul 23 08:54:17 ubergamer2 gconfd (henrik-5002): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 23 08:54:17 ubergamer2 gconfd (henrik-5002): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 23 08:54:17 ubergamer2 gconfd (henrik-5002): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 23 08:54:20 ubergamer2 gconfd (henrik-5002): Resolved address "xml:readwrite:/home/henrik/.gconf" to a writable configuration source at position 0
Jul 23 08:54:30 ubergamer2 gconfd (henrik-5002): Received signal 15, shutting down cleanly
Jul 23 08:54:30 ubergamer2 gconfd (henrik-5002): Exiting
Jul 23 08:54:30 ubergamer2 gconfd (henrik-5096): starting (version 2.14.0), pid 5096 user 'henrik'
Jul 23 08:54:30 ubergamer2 gconfd (henrik-5096): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 23 08:54:30 ubergamer2 gconfd (henrik-5096): Resolved address "xml:readwrite:/home/henrik/.gconf" to a writable configuration source at position 1
Jul 23 08:54:30 ubergamer2 gconfd (henrik-5096): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 23 08:54:30 ubergamer2 gconfd (henrik-5096): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 23 08:54:30 ubergamer2 gconfd (henrik-5096): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

That looks like the time that I tried to log in. Any ideas?
Thanks in advance.

/Henrik

---

### Post by JerMe on 2006-07-23
Are you using XGL/Compiz?

---

### Post by protorion on 2006-07-23
No, I'm not. :KS

---

