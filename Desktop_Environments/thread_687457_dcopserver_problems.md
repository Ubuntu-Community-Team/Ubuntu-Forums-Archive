---
title: "dcopserver problems"
date: 2008-02-04
forum: Desktop Environments
---

### Post by misterfixit on 2008-02-04
dave@misterfixit:~$ amarok
WARNING: Waiting for already running klauncher to exit.
WARNING: Another instance of klauncher is already running!
kdeinit: Communication error with launcher. Exiting!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
DCOP aborting call from 'amarok' to 'klauncher'
DCOP aborting (delayed) call from 'kded' to 'klauncher'
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/dave/.DCOPserver_misterfixit__0
and start dcopserver again.
dave@misterfixit:~$ rm /home/dave/.DCOPserver_misterfixit__0
dave@misterfixit:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdeinit: Shutting down running client.
kio (KSycoca): WARNING: Found version -1334557726, expecting version 94 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KDEDModule not found
DCOP aborting (delayed) call from 'kded' to 'klauncher'
kbuildsycoca running...
kio (KSycoca): WARNING: Found version 0, expecting version 94 or higher.
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
no ****, sherlock ...

Seems like I am now receiving these errors with korganizer also.

You think I should go ahead and call Comcast for help :-)  .... oh, wait, no, I'll just reformat the HD and put everything back using the Repair Disk.  :-)  ... no wiat!  I'll ask my Ubuntu Buddies for help!  Yeah!

TIA

Dave

---

### Post by afonsec2 on 2008-02-06
i solved my solution this way.
 
open the terminal and type cd ~. 
type $ sudo chown -R  "user"."group" .kde   (Your user name and the group you belong should placed on user and group )(remember the dot before kde)
type $ rm -r .DC* ; dcopserver

(If you dont know you user id and group id) type $ id
ur user id is where it says uid followed by a number, and then your user id in parenthesis
ur group id is where it says gid. 


good luck !

It did work for me, good luck!

---

### Post by phatdad on 2008-02-07
I had the same problem, which the solution seems to have solved. Thanks.
However the command
**rm -r .DC* ; dcopserver** 
threw up the error
rm: cannot remove `.DC*': No such file or directory

---

### Post by marcelo.matos on 2008-07-10
phatdad, i have the same message and issue here.

Anyone have a hint? Thanks!

---

