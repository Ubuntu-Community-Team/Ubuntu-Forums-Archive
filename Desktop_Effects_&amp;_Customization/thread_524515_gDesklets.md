---
title: "gDesklets"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by Predrag on 2007-08-13
hi.I cant start gDesklets.I have tries all versions for amd64 but nothing

predrag@Schumacher:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [    ###      ]
==========================================================[08/13/07-14:43:04]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/bin/gdesklets: line 397 <module>
in /usr/bin/gdesklets: line 270 parse_command
in /usr/bin/gdesklets: line 174 __open_profile
in /usr/bin/gdesklets: line 155 __client_daemon
in /usr/lib/gdesklets/main/client.py: line 295 get_daemon
[EXC]/usr/lib/gdesklets/main/client.py

[---]  290                 daemon = connection
[---]  291                 if (daemon):
[---]  292                     break
[---]  293             except socket.error:
[---]  294                 pass
[ERR]> 295             time.sleep(0.1)
[---]  296 
[---]  297         print "\r" + " " * 40 + "\r",
[---]  298 
[---]  299         if (not daemon):
[---]  300             sys.exit(_("Cannot establish connection to daemon: timeout!\n"
[---]  301                         "The log file might help you solving the problem."))



do u know what to do?

---

### Post by Predrag on 2007-08-13
i have found solution.Check this [https://bugs.launchpad.net/ubuntu/gutsy/+source/gdesklets/+bug/83922](https://bugs.launchpad.net/ubuntu/gutsy/+source/gdesklets/+bug/83922)

---

### Post by Predrag on 2007-08-13
i have found solution check this [https://bugs.launchpad.net/ubuntu/gutsy/+source/gdesklets/+bug/83922](https://bugs.launchpad.net/ubuntu/gutsy/+source/gdesklets/+bug/83922)

---

### Post by Predrag on 2007-08-15
or u can dowload it form my web [http://linuxakk.ic.cz/](http://linuxakk.ic.cz/)  .its compiled and it run

---

### Post by DjBones on 2007-08-17
thanks for the package Predrag! fixed my probs haha

---

### Post by Predrag on 2007-09-09
i m happy that i could help u

---

### Post by FlowingSnake on 2007-09-18
Hmm I ran the deb you made. And i get gdesklets to start up ...but there are no desklets in the configure menus.

---

### Post by Predrag on 2007-09-18
yes i know,but in all 64 bit distros are not desklets.i dont know why

---

