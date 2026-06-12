---
title: "Nautilus remote connections adding desktop items"
date: 2005-08-26
forum: Desktop Environments
---

### Post by vaalaskala on 2005-08-26
Hi!

Using Ubuntu as web developer in my everyday work and I have to deal with ~127 remote ftp connections. 

Nautilus (the file browser) allows me to connect to remote servers via gnome-vfs and thats very cool, but the bad thing is that all the connections are mounted to desktop :( so one could imagine my desktop with ~127 ftp folders on it (at 1204x786) and the usability I get from my desktop that way.

So my question is how can I configure nautilus to mount those drives to alternative foder (/home/user/ftp/ or whatever) and not to desktop?

---

### Post by sdyson on 2008-06-12
I know this is old but it may help others. 

Open gconf-editor and make sure the following option is unchecked: 

/apps/nautilus/desktop/volumes_visible

The downside is this hides all mounted volumes so you won't see USB sticks etc. on the desktop either.

---

