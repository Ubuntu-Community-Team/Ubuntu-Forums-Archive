---
title: "DCOP Communications Error (Amark)"
date: 2006-02-04
forum: Desktop Environments
---

### Post by kend on 2006-02-04
Occasionally running Amarok in Gnome generates an error message:

There was an error setting up interprocess communications for KDE.
The message returned by the system was:

    Could not open network socket

Please check that the "dcopserver" program is running!

It's not a file ownership problem.  All the files in home are owned by the right account.

Ken

---

### Post by gattu on 2008-02-13
Anyone found a solution for this? I have the same problem. I'm running Gutsy and I had this problem in Feisty also.

---

### Post by rusyear04 on 2008-03-10
hi there... having the exactly same problem.

would be thankful for helpfull hints!
thx

---

### Post by rusyear04 on 2008-03-10
i have to admit that i don't know which one of the following was necessary. but nevertheless: amarok now works fine again :KS

here is what i did:

[http://ubuntuforums.org/showthread.php?t=687457&highlight=amarok+dcopserver](http://ubuntuforums.org/showthread.php?t=687457&highlight=amarok+dcopserver)
said
> 
open the terminal and type cd ~.
type $ sudo chown -R "user"."group" .kde (Your user name and the group you belong should placed on user and group )(remember the dot before kde)
type $ rm -r .DC* ; dcopserver

(If you dont know you user id and group id) type $ id
ur user id is where it says uid followed by a number, and then your user id in parenthesis
ur group id is where it says gid. 

[http://ubuntuforums.org/showthread.php?t=665749&highlight=amarok+dcopserver](http://ubuntuforums.org/showthread.php?t=665749&highlight=amarok+dcopserver)
basically said to do
> rm .DCOP*

and the thing that i did before it started to work again was...
> rm -rf ~/.xine/
from
[http://ubuntuforums.org/showthread.php?t=521005&highlight=amarok+klauncher](http://ubuntuforums.org/showthread.php?t=521005&highlight=amarok+klauncher)

thanx to all the helpers out there ;)
i guess, that the last one did the trick, but i don't know if the other ones were not necessary as well...
so you may as well try from bottom to top.

have phun.

---

### Post by scheer897 on 2008-05-09
thank you, Rusyear04

---

