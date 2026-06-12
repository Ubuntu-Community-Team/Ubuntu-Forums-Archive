---
title: "Need help with bash script"
date: 2009-01-25
forum: General Help
---

### Post by rozbarwinek on 2009-01-25
This is my script for running screenlet with banshee:

```
#!/bin/bash
banshee-1 --redirect-log --play-enqueued %U &
sleep 4 && python -u /usr/share/screenlets/NowPlaying/NowPlayingScreenlet.py &
```

I run it like that because theme that I'm using with NowPlaying screenlet is loading a little glitchy so I set to start after Banshee so I could only see when it's loaded completely :D
The problem is that when I close banshee and start banshee again the second NowPlaying screenlet runs with it :|
So is there a way to set that script to recognize is there already NowPlaying screenlet running so it wont run it twice?
Please help :)

---

### Post by dcstar on 2009-01-25
> **rozbarwinek said:**
> This is my script for running screenlet with banshee:

```
#!/bin/bash
banshee-1 --redirect-log --play-enqueued %U &
sleep 4 && python -u /usr/share/screenlets/NowPlaying/NowPlayingScreenlet.py &
```

I run it like that because theme that I'm using with NowPlaying screenlet is loading a little glitchy so I set to start after Banshee so I could only see when it's loaded completely :D
The problem is that when I close banshee and start banshee again the second NowPlaying screenlet runs with it :|
So is there a way to set that script to recognize is there already NowPlaying screenlet running so it wont run it twice?
Please help :)

You can write a script that looks for an already running instance, do a search and you should be able to find something for another app that you can adapt for yours.

---

### Post by rozbarwinek on 2009-01-25
> **dcstar said:**
> You can write a script that looks for an already running instance, do a search and you should be able to find something for another app that you can adapt for yours.

Is there now easier way? :)

---

### Post by sisco311 on 2009-01-25
try something like:
```


#!/bin/bash
banshee-1 --redirect-log --play-enqueued %U &
if ! pgrep NowPlayingScreenlet.py > /dev/null; then
  sleep 4 
  python -u /usr/share/screenlets/NowPlaying/NowPlayingScreenlet.py &
fi

```

---

### Post by rozbarwinek on 2009-01-25
> **sisco311 said:**
> try something like:
```


#!/bin/bash
banshee-1 --redirect-log --play-enqueued %U &
if ! pgrep NowPlayingScreenlet.py > /dev/null; then
  sleep 4 
  python -u /usr/share/screenlets/NowPlaying/NowPlayingScreenlet.py &
fi

```

Same result... :/

---

