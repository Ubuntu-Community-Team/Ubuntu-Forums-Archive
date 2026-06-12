---
title: "Lock the size and position of a window"
date: 2020-11-23
forum: Desktop Environments
---

### Post by kovalevskaya on 2020-11-23
Hello to everyone I want to make a very simple (but I believe that it is not so easy to answer or maybe just it is not possible) question.
Is there a way to lock the position and the size of a certain window? In other words Is there a way to disable the size change and the movement of a window?
I'm using Fluxbox if that change something (I believe , if that is possible is something related with window manager, but really I don't know)

Thanks!

---

### Post by TheFu on 2020-11-24
I've never used fluxbox nd don't thnk 'locking' s possible, but many x11 applications support the -geometry option to place and size application windows. Unfortunately, while this is automatic in x11 coding, some popular GUI toolkits break that for reasons that are unclear to me.
Some examples:```

xterm $XTERM_OPTS -geometry 80x25+0+170 &
xterm $XTERM_OPTS -geometry 80x25+430+100 &
```

---

