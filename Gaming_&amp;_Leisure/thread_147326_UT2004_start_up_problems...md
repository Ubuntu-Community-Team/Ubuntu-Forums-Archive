---
title: "UT2004 start up problems.."
date: 2006-03-20
forum: Gaming &amp; Leisure
---

### Post by mtweldon on 2006-03-20
I got the game installed, and it started up the first time and I played for probably 30 mins fine.  Logged out and now im trying to start up again and the start up screen flashes with the ut2004 and it does nothing.
did sh ut2004 in the folder and get this:


Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error

what do I do ?

---

### Post by monkey4 on 2006-03-20
In your ut2004 System folder, try renaming ut2004.ini to ut2004.bak and then copy default.ini to ut2004.ini

---

### Post by mtweldon on 2006-03-20
only thing i see in my system folder is ut2004.det, .est, . frt, . itt, .kot and ut2004-bin
no .ini

---

### Post by monkey4 on 2006-03-20
Is there a default.ini? If so, copy it to the same folder as ut2004.ini

---

### Post by Harleen on 2006-03-20
You probably have started UT2004 using sudo, resulting in a .ut2004 directory in your home directory that only root is allowed to read. This happens, if you press the "play now" button on the end of the installation. You can repair it by using this command:

sudo chown <user>:<user> ~/.ut2004 -R

<user> is to be replaced by your local user name, of course. This command will transfer the ownership of that directory to your normal user.

---

### Post by mtweldon on 2006-03-20
ahh thats exactly what I did, thanks.. Will try this once I get off school / work.

---

### Post by fiendskull9 on 2006-03-23
hey

no need to edit the permissions, just run it sudo ut2004.

it worked for me

clay

---

### Post by Harleen on 2006-03-23
Of course does this work. But you should never work as root if it's not really needed. And  gaming does not count as system administration - unless you are playing [psDoom]("http://psdoom.sourceforge.net/"). ;)

---

