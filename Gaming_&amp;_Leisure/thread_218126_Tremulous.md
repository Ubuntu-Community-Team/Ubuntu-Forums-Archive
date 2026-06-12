---
title: "Tremulous"
date: 2006-07-18
forum: Gaming &amp; Leisure
---

### Post by Sp00ne on 2006-07-18
I downloaded Tremulous, and i have no idea how to install *.run files. I've tried various commands, but it always says "command not found".

Much help would be appriciated.

---

### Post by nickless on 2006-07-18
try searching the forum...

---

### Post by Footissimo on 2006-07-18
> **Sp00ne said:**
> I downloaded Tremulous, and i have no idea how to install *.run files. I've tried various commands, but it always says "command not found".

Much help would be appriciated.

```
sudo sh tremulous-1.1.0-installer.x86.run
```

sudo = temporarily change to root user, sh = run something

type 'tremulous' to run the game.  Use alacarte menu editor to make a menu item (see post I wrote to you earlier)

---

### Post by Sp00ne on 2006-07-18
Ok, i type in "sudo sh tremulous-1.1.0-installer.x86.run", then it came up with "sh: tremulous-1.1.0-installer.x86.run: No such file or directory"

---

### Post by grim1234 on 2006-07-18
you need to be in the same directory as the run file with the terminal.

Another way to do it is to make the file executable :

> chmod +x programname.run

again, from the same directory.

then just run the program :

> ./programname.run

have fun,

G.

---

### Post by Sp00ne on 2006-07-18
Ok, i got it installed and running. No need to post in this thread anymore.

---

### Post by Flare183 on 2008-08-07
Just install it using Apt-get or synaptic. Like this:
```
sudo apt-get install tremulous tremulous-data
```

Its that easy. Then go and get the update and find and replace the actual executable file with the updated file.

---

