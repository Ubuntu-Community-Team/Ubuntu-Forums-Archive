---
title: "Help with configuration error"
date: 2005-11-05
forum: Desktop Environments
---

### Post by jsvidyad on 2005-11-05
Hi!!!

  Whenever the login window shows up, I get a message saying invalid command in configuration file, using default command, please edit configuration file.  I am not sure which configuration file I have to edit and what i have to do.

---

### Post by Joe_lurker on 2005-11-05
Check the log files.  Click on Applications | System Tools | System Log.  Choose the /var/log/messages file to view.  You might want to check out the other log files also.

Do that right after you boot.  You will have to scroll down to the bottom to see if there are any messages related to the problem.

-Joe

---

### Post by jsvidyad on 2005-11-05
I believe these are the relevant lines relating to the problem.

Nov  5 09:58:47 localhost gconfd (jyothish-8738): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Nov  5 09:58:47 localhost gconfd (jyothish-8738): Resolved address "xml:readwrite:/home/jyothish/.gconf" to a writable configuration source at position 2
Nov  5 09:58:47 localhost gconfd (jyothish-8738): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Nov  5 09:58:47 localhost gconfd (jyothish-8738): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Nov  5 09:58:47 localhost gconfd (jyothish-8738): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Nov  5 09:58:47 localhost gconfd (jyothish-8738): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Nov  5 09:58:47 localhost gconfd (jyothish-8738): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Nov  5 09:58:52 localhost gconfd (jyothish-8738): Resolved address "xml:readwrite:/home/jyothish/.gconf" to a writable configuration source at position 0
Nov  5 09:59:28 localhost gconfd (root-8852): starting (version 2.12.0), pid 8852 user 'root'
Nov  5 09:59:28 localhost gconfd (root-8852): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov  5 09:59:28 localhost gconfd (root-8852): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Nov  5 09:59:28 localhost gconfd (root-8852): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Nov  5 09:59:28 localhost gconfd (root-8852): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Nov  5 09:59:28 localhost gconfd (root-8852): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Nov  5 09:59:28 localhost gconfd (root-8852): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Nov  5 09:59:28 localhost gconfd (root-8852): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Nov  5 09:59:28 localhost gconfd (root-8852): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7

---

### Post by Joe_lurker on 2005-11-05
I have the same output in my /var/log/mesages yet I don't get the error.  I would look beyond those errors and see if there are others.

-Joe

---

