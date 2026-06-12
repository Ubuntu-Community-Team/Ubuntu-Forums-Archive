---
title: "HOWTO: StarCraft II Flash Ripper"
date: 2007-10-25
forum: Gaming &amp; Leisure
---

### Post by bashologist on 2007-10-25
Searches starcraft2.com for those small flash clips in the features section and downloads them to a directory in /tmp.
```

#!/bin/bash
OLDIFS=$IFS
DEST=$(mktemp -d)
pushd $DEST >/dev/null
echo "$(date +%H:%M:%S): Downloading: http://www.starcraft2.com/features/ ..."
wget --no-directories --no-parent --accept '*.xml,*.XML' -rq 'http://www.starcraft2.com/features/'
IFS=$'\n' URLS=($(grep -ioh '[^"]*\(movieplayer\|unitsplayer\)_[zpt][^"]*\.swf' *.xml)) IFS=$OLDIFS
wget "${URLS[@]/#\//http://www.starcraft2.com/}"
rm *.xml
rename 's/([a-z]+)_([a-z]+)_([a-z]+)_?(\d*).*/\u$2 \u$3 \u$1$4.swf/' *.swf
popd >/dev/null
nautilus $DEST || konqueror $DEST || dolphin $DEST

```
[INDENT][[IMG]http://img131.imagevenue.com/loc253/th_44408_snapshot1_122_253lo.jpg[/IMG]](http://img131.imagevenue.com/img.php?image=44408_snapshot1_122_253lo.jpg)[/INDENT]

---

### Post by K.Mandla on 2007-10-26
Moved to Gaming and Leisure.

---

### Post by blacksm1th on 2007-10-26
Very handy script. Thanks :)

---

