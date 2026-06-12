---
title: "How can an app be notified of end of user session or ecryptfs unmount?"
date: 2011-12-18
forum: Desktop Environments
---

### Post by David Olivier on 2011-12-18
I want to be able to launch an application every time I start a user session, and have it automatically shutdown in a *clean* fashion at the end of the session, *before* my ecryptfs homedir is unmounted.

Specifically, I want to run my own private mysql server, with encrypted data. My homedir is encrypted, so the simplest way to do it would seem to be to move the database files from where they currently are - /var/lib/mysql - to some location in my homedir. The mysql daemon would then be launched when I start the session, rather than at boot time.

But when I log out of the session, what will happen? The mysqld has to be notified before the homedir is unmounted, otherwise either the homedir will not unmount, or it will be unmounted but possibly with the database files left in a corrupted state, if the mysql daemon hadn't been notified to flush all outgoing data to them.

I have googled a lot but have been unable to find out how some applications - such as gedit - are notified of the end of a session. I would like to set up a script or something that would be notified before the unmount and thus have the opportunity to send a sigterm to the mysqld. But how do I do that?

Or perhaps there are alternative solutions to encrypt the mysql data?

David

---

### Post by David Olivier on 2011-12-20
Bump!

The issue is rather simple: what kills the apps when you log out of a session? It's strange no one seems to know!

---

