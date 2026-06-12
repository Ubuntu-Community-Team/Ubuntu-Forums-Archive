---
title: "Counterstrike:Source crash on connect"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by steevk on 2007-02-15
Hey guys-

A friend of mine purchased CS:S today, and it runs great using wine0.9.30...except for one thing.

It loads the game, we connect to a server, it sends everything, and then right before the loading bar is finished, the game just crashes.


This is the output I'm getting.

```
$ wine "C:\Program Files\Steam\steam.exe" -d3d -applaunch240
libGL warning: 3D driver claims to not support visual 0x5b
```

Now, it does this well before Steam loads. Is there any way to get the output from CS itself? Has anyone else had this problem?

Thanks in advance.

---

### Post by justin whitaker on 2007-02-16
> **steevk said:**
> Hey guys-

A friend of mine purchased CS:S today, and it runs great using wine0.9.30...except for one thing.

It loads the game, we connect to a server, it sends everything, and then right before the loading bar is finished, the game just crashes.


This is the output I'm getting.

```
$ wine "C:\Program Files\Steam\steam.exe" -d3d -applaunch240
libGL warning: 3D driver claims to not support visual 0x5b
```

Now, it does this well before Steam loads. Is there any way to get the output from CS itself? Has anyone else had this problem?

Thanks in advance.

Are you loading from the server browser, or via console? I've had success connecting via command line.

---

### Post by steevk on 2007-02-16
Via the game browser...how do you connect via the command line?

---

