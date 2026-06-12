---
title: "How to display a TEXT popup to lower right corner, few seconds?"
date: 2010-07-24
forum: Desktop Environments
---

### Post by frenchn00b on 2010-07-24
Hello,

When I change my music song with mpd, I would like a popup to say bottom right the name of the song.

is there a program in the repositories that does that? plz from repositories :)

Thank you !!!

Best regards

---

### Post by frenchn00b on 2010-07-24
```
apt-get install  libnotify-bin
```

nowplaying.sh 
```

audacious2 "$1" 
notify-send  "Song: `audtool --current-song`" 

```

SOLVED

---

