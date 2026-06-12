---
title: "how do I host a sauerbraten game online over my LAN (or on the internet)?"
date: 2010-12-23
forum: Gaming &amp; Leisure
---

### Post by pythonscript on 2010-12-23
I just installed the sauerbraten and sauerbraten-server packages, and I'm trying to host a game over my LAN so my friends and I can play. However, I can't find any documentation on the server online, and the man page gives me a set of commands that don't seem to help (my server doesn't show up in the search list at all). 

Does *anyone* know how I can set this up? I can't find instructions anywhere; all I can do is join games and that's not particularly interesting if none of us can start a game. 

Thank you!

---

### Post by pythonscript on 2010-12-23
I'm using this command to host a private game with only 5 players, including myself. What am I doing wrong?

```

sauerbraten-server -nMY_DESCRIPTION -c5 -mmasterserver -yMY_PASSWORD 
```

No one else on the LAN can see this, though, but I can still join games online so I don't think my firewall is the problem...

---

### Post by Baz00 on 2011-02-28
Hello,
In the multiplayer menu, your clients have to press "Update server list from master server" and tic the "Search Lan" box in order to see your server.

Hope this help.

---

