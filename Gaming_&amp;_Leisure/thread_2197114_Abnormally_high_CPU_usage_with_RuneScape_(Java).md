---
title: "Abnormally high CPU usage with RuneScape (Java)"
date: 2014-01-02
forum: Gaming &amp; Leisure
---

### Post by cdavison on 2014-01-02
Hey guys! I recently installed Ubuntu for the first time, and everything (more or less) has been working brilliantly, up until this morning when I logged in to RuneScape (via the unix-runescape-client by HikariKnight) to find myself bouncing around everywhere at <10 FPS. I ran the `top' command to find:

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8948 connor    20   0 3564m 538m  31m S  254 13.9   3:20.16 java               
 1195 root      20   0  283m  96m  76m S   15  2.5   4:29.44 Xorg               
 2147 connor    20   0 1138m  84m  29m S   11  2.2   3:56.94 compiz 

```

Nothing, to my knowledge, had changed from the last time I'd logged in. I've also tried the browser client ([http://www.runescape.com/game](http://www.runescape.com/game)), it demonstrated the same performance. I've tried restarting, using different JVMs, using different audio drivers (for all that was worth), and running the game in safe mode (as opposed to using OpenGL). I've tried running different Java-based games (although I couldn't find many) and the performance doesn't seem to be too poor in contrast - up to 100% CPU.

I'd love to hear your thoughts!

**Edit:** Given the circumstance, I decided it would be a good time to reinstall and upgrade to Ubuntu 13.10. The problem, however, persists.
[B]
Edit2:[/B] Updating & upgrading the drivers for my card seemed to solve the problem. Whilst this is technically solved, I'd love to hear any thoughts as to why they might have stopped working overnight. Thanks all!

---

### Post by soloman469 on 2014-01-03
What is your CPU Speed?

---

