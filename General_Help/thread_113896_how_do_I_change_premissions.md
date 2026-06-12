---
title: "how do I change premissions??"
date: 2006-01-07
forum: General Help
---

### Post by aserre on 2006-01-07
I'm trying to install programs.. every program I've tried says I need zlib installed..
I found the zlib program I need but can't get it to install it comes up with this:

mkdir: cannot create directory `/usr/local/share/man/man3': Permission denied
make: [install] Error 1 (ignored)
cp zlib.h zconf.h /usr/local/include
cp: cannot create regular file `/usr/local/include/zlib.h': Permission denied
cp: cannot create regular file `/usr/local/include/zconf.h': Permission denied
make: *** [install] Error 1



can anyone tell me what comands to use to get the premissions changed

---

### Post by jsmidt on 2006-01-07
You might need to log in as root.  Type 
```

sudo -s -H

```

In the terminal then enter your root password.

---

### Post by aserre on 2006-01-07
ok thanx that worked but now it is  saying that:

configure: error: zinf needs GDBM installed

is that another program?

---

### Post by jsmidt on 2006-01-07
You need to install GDBM.  I don't know what exact package that is.  But go into Synaptic under System -> Administration.

Open Synaptic Package manager.
 
When it is open hit

```
ctrl-f
```

A search will pop up.  Type in gdbm.  Many packages will pop up that match that search.  Try to find which one corresponds to the gdbm your package needs. Sorry I can't say more I am not familiure with gdbm.

---

### Post by aserre on 2006-01-07
thanx its finally working

---

### Post by fealz on 2006-01-07
[QUOTE=jsmidt]You might need to log in as root.  Type 
```

sudo -s -H

```

In the terminal then enter your root password.[/QUOTE]

I know about sudo -s, but what does -H do?

---

