---
title: "how do I run games"
date: 2005-06-20
forum: Gaming &amp; Leisure
---

### Post by bloodpuppy on 2005-06-20
downloaded some games using Synaptic, found them in /usr/games, but I cannot execute them. what do I need to do?

---

### Post by desdinova on 2005-06-20
the command line in the terminal will be

/usr/games/commandname

then if it works,add it to your Gnome Menu

---

### Post by bloodpuppy on 2005-06-20
I type in:

$ /usr/games/spellcast

and get this:

usage: spellcast RemoteDisplay [ RemoteDisplay2 ... ]
$

what now?

---

### Post by amohanty on 2005-07-13
spellcast is a multiplayer game, the remotedisplay spec is used to define the hostnames and display specs of other players.
docs at: [http://hpux.connect.org.uk/hppd/hpux/Games/Networking/spellcast-1.1/man.html](http://hpux.connect.org.uk/hppd/hpux/Games/Networking/spellcast-1.1/man.html)

---

