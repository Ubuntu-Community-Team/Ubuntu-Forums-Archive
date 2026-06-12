---
title: "Got Wakfu to finally work in Ubuntu 12.04"
date: 2013-07-20
forum: Gaming &amp; Leisure
---

### Post by DarkAmbient on 2013-07-20
I installed Wakfu from the Software Center, then started it, updated and pressed Play, then nothing happened. No errors nothing, even when running from the terminal. 
Though I could share how to get it to work in case someone else encounter this issue.

So, from parsing logs I figured out how to launch the game more directly in a terminal:

```
bash java_launcher -L en -C en -n "~/.local/share/data/Ankama/Wakfu/game/carousel" -p "/opt/ankama/wakfu/game"
```

I was finally getting some output, libjogl.so had problem with libGL.so.1. There was no libGL.so.1 in the same folder as libjogl.so though.
So I tried copying libGL.so.1 to Wakfus game/library-folder.
 
```
sudo cp /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /opt/ankama/wakfu/game
```

Then I got the game running! :-):)

---

