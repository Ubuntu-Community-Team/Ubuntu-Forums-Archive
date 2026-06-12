---
title: "wine on synaptic"
date: 2005-07-28
forum: Gaming &amp; Leisure
---

### Post by jarg on 2005-07-28
I searched through synaptic for "wine" but am confused about which packets I need. I have no clue which is what,
Anybody know which packets I need or should have on hand?

---

### Post by MikeyXX on 2005-07-28
[QUOTE=jarg]I searched through synaptic for "wine" but am confused about which packets I need. I have no clue which is what,
Anybody know which packets I need or should have on hand?[/QUOTE]
 If you go to a command prompt and type:

sudo apt-get install wine

that should get you wine and it's dependencies. It worked for me. Obviously you might not have a complete sources.list but give it a try.

---

### Post by jarg on 2005-07-28
[QUOTE=MikeyXX]If you go to a command prompt and type:

sudo apt-get install wine

that should get you wine and it's dependencies. It worked for me. Obviously you might not have a complete sources.list but give it a try.[/QUOTE]
 > 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

It gave me two errors after I entered my password. I don't really understand these errors. I think the first one is saying that not everything is avlible and the second is saying somthing else is running.

---

### Post by Olrich on 2005-07-28
You need to close the Synaptic package manager before running that command.  That should get rid of those errors.

---

### Post by jarg on 2005-07-28
[QUOTE=Olrich]You need to close the Synaptic package manager before running that command.  That should get rid of those errors.[/QUOTE]

Thanks, could you also tell what I type in the terminal to run games?

---

### Post by ORTOXIC on 2005-07-29
I put that command into the terminal and got this message.

"Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate"

I don't get it. I NEED WINE. Someone please help!

---

### Post by strikeforce on 2005-07-29
You need to add the extra repostiories in /etc/apt/sources.list

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)


Also in the forums there is a backports.  When it happens the latest wine will be there.

---

