---
title: "TORCS 1.3.0 won't start"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by bravemosquito on 2007-04-03
```
root@xxx:/usr/local/games/torcs# torcs
**TORCS location not found**
```

The .run package was healthy and before installation I removed Torcs 1.2.4 through Synaptic.

Any ideas?

---

### Post by xopher on 2007-04-03
Ok firstly, Ill try to say this as nicely as possible..

**DO NOT RUN THINGS AS ROOT. (period)**

Now, let's see what's your problem. If /usr/local/games isn't in your $PATH

```
echo $PATH
``` to check.. Then running it by typing 'torcs' won't do.
If the executable is named torcs, then** when in */usr/local/games/torcs***, run: ```
./torcs
```

This should most certainly give you at least some feedback, maybe a new problem ;)

---

### Post by bravemosquito on 2007-04-03
Thanks for coop, but I managed to fix the problem. Just edit /usr/local/games/torcs/torcs (where TORCS is installed):

```
nano /usr/local/games/torcs/torcs
**preffix=@prefix@** should be **prefix=/usr/local/games/torcs**
```

Save the file and run **'torcs'** again :)

---

