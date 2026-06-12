---
title: "Banshee"
date: 2009-01-01
forum: General Help
---

### Post by Qloor on 2009-01-01
In AmaroK I can view the track title being played in Konversation in a script using ```
TITLE=$(dcop amarok player title);
```.
How would I do this with banshee? ```
TITLE=$(*what?*);
```.

---

### Post by Qloor on 2009-01-01
-OR-

If someone could mod this script to work with Banshee, I'll give you a thanks and full credit if it's given out.

```
#!/bin/sh

# Prints the currently playing song from amaroK for Konversation.

PORT=$1;
SERVER=$2;
TARGET=$3;

TITLE=$(dcop amarok player title);
ALBUM=$(dcop amarok player album);
ARTIST=$(dcop amarok player artist);
YEAR=$(dcop amarok player year);
GENRE=$(dcop amarok player genre);
TYPE=$(dcop amarok player type);
BITRATE=$(dcop amarok player bitrate);
TIME=$(dcop amarok player totalTime);
CURTIME=$(dcop amarok player currentTime);

echo "/me np: ${TITLE} [${CURTIME}/${TIME}] - ${ALBUM} - ${YEAR} by ${ARTIST} | ${GENRE} | ${TYPE} | ${BITRATE} kbps"| while read line; do dcop $PORT default say $SERVER "$TARGET" "$line"; done

# Vey easy to tune, so do whatever you like with it ;-) and preferably share it with the rest of us!
```

---

### Post by Ahadiel on 2009-01-01
It's probably more difficult than just modding that script seeing as how Amarok uses dcop and Banshee does not. You may need to make your own plugin, or modify an existing one.

---

### Post by Qloor on 2009-01-01
> **Ahadiel said:**
> It's probably more difficult than just modding that script seeing as how Amarok uses dcop and Banshee does not. You may need to make your own plugin, or modify an existing one.

Banshee uses dbus, I'm not familiar with the language at all, and I can't find an existing script for any application using Banshee.

---

### Post by Qloor on 2009-01-01
Bump FGJ.

---

### Post by Qloor on 2009-01-01
> **qloor said:**
> bump fgj.

qft. =p

---

### Post by Qloor on 2009-01-02
Lol, QUAD POST WHATTTTTTT.

---

