---
title: "Log out/kill a user's GUI session via SSH?"
date: 2013-04-16
forum: Desktop Environments
---

### Post by kolby386 on 2013-04-16
I am sure this very question has been asked around here quite a bit, but I have been looking for days and I am still unable to find a solution.

I am running Ubuntu 12.10 Desktop on a Lenovo H520s. Right now the computer is used for two things: Minecraft and Minecraft Server.
Now, I'm sure that running the server software and the client software on the same machine is probably not the most ideal thing to do, but I'm trying to work with what I have.

I have created a user account specifically for running Minecraft (the game) so that it runs at least somewhat independently of the server software. The main reason behind this is that while playing Minecraft, the entire GUI suddenly and [seemingly] randomly becomes unresponsive with the exception of the mouse cursor.

No combination of keyboard shortcuts will convince the computer to log out the user or present with a terminal of any kind. Of course, much like other similar posts here, I can still access the computer over the LAN/WAN via SSH. The only problem is that no matter what commands I send to the computer or what user I'm logged in as, the GUI doesn't budge. I can't log out, I can't use commands like pkill to kill that user's processes; nothing works but shutting down the computer.

Shutting down the computer is exactly what I am trying to avoid by having these two accounts separate from each other. Is there anything I can do to make this work? What do I need to be looking for to help me solve this? Any help or suggestion of any kind is greatly appreciated.

---

### Post by Lars Noodén on 2013-04-16
Welcome to the forums.  

You can kill a user's processes with [pkill](http://manpages.ubuntu.com/manpages/quantal/en/man1/pkill.1.html).

```

pkill -u kolby386

```

Alternately, you can kill specific processes individually.  You can see which processes that user is running using [pgrep](http://manpages.ubuntu.com/manpages/quantal/en/man1/pgrep.1.html).

```

pgrep -lfu kolby386
pkill -u kolby386 -x *someprogram*

```

---

