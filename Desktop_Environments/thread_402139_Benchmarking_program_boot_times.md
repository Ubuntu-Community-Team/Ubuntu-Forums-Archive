---
title: "Benchmarking program boot times"
date: 2007-04-05
forum: Desktop Environments
---

### Post by bmartin on 2007-04-05
Is it possible to time the startup of a program that includes a UI?

I want to do an accurate comparison of how long it takes programs to boot in various window managers without using a watch (i.e. I want the computer to act as a stopwatch). Is there a program to do this, or better yet, is there some way of scripting this? It might be possible by monitoring levels of disk access and processor usage by the program; I'm looking for a clean, accurate way to tell how long it takes for programs such as Gaim and Firefox to boot.

---

### Post by dreadlord_chris on 2007-04-05
install bootchart
```

sudo aptitude install bootchart

```

This will make a graph of the boot process. you can find these graphs in /var/log/bootchart/

---

### Post by bmartin on 2007-04-05
I read up on the program at [http://www.bootchart.org/;](http://www.bootchart.org/;) can I log events after the boot process is done? I'm current at work and I don't have a way of trying this out (we use XP here @ AIG :-(, I have to restart my computer every day so that it's usable).

---

