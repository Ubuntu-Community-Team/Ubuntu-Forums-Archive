---
title: "Multi-game/Universal Master Server"
date: 2008-09-04
forum: Gaming &amp; Leisure
---

### Post by curvedinfinity on 2008-09-04
Hey all,
I want to get some feedback from any other OSS game devs out there who might frequent this forum. Basically, I have a pretty potent server running for MirthKit, and one of the features I was going to add coming up soon is a multi-game master/lobby server so people can publish multiplayer MirthKit games and not have to worry about server logistics. However, I'd be shooting for interoperability, so potentially non-MirthKit games could use the server too.

The current plan is to have an extremely simple protocol on top of HTTP. This means it'll be cake to add support for this master server into any game, since libraries like CURL (as MK uses) are so easy to setup. This protocol is what I'd specifically like feedback about, because I want to make sure everyone who would potentially use it is happy.

Just as an example of how it could work:

Want to get a list of games for the game "CosmicConquest"?

```
http://arcade.mirthkit.com/arcadeList.py?game=CosmicConquest
```

returns the plain-text document...

```
{{name="Joe's Server",address="32.322.51.203",port="2222"},{...}}
```

Then, your game picks apart whatever syntax it ends up looking like, and pings all the game servers for latency, number of players connected, and so on. The protocol would also feature register and keepalive commands so game servers can add themselves.

Does this sound like a good idea?

---

### Post by Perfect Storm on 2008-09-04
Link not found, curvedinfinity :-/

---

### Post by curvedinfinity on 2008-09-04
Oh, the link isn't a link ... its a CGI argument format

So it doesn't do the little ellipses, here's the part after the .com:

/arcadeList.py?game=CosmicConquest

---

### Post by Bios Element on 2008-09-04
I'm not a game dev but I've been considering several projects and one thought i had was that a single system aka, Steam would work great. If it could be launched right and updated and so forth that could work out great.

---

### Post by curvedinfinity on 2008-09-04
Actually, MirthKit is a lot like a 2D steam that's a lot more open, so that front is being worked on. ;)

[www.mirthkit.com](www.mirthkit.com)

Bump for game devs...

---

