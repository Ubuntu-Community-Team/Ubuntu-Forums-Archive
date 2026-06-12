---
title: "Peculiar Azureus problem"
date: 2006-06-29
forum: Desktop Environments
---

### Post by zarathustra on 2006-06-29
I noticed that Azureus had started taking an age to load up, so I tried starting up via the CLI. I have a custom installation in my home folder, so just ran it from there with the necessary commands:

> nick@ubuntu:~/azureus$ ./azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/nick/azureus/Azureus2.jar:/home/nick/azureus/swt.jar" -Djava.library.path="/home/nick/azureus" -Dazureus.install.path="/home/nick/azureus" org.gudy.azureus2.ui.swt.Main ''
StartSocket: passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]


So it seems to think it is already running before I've started it! I also noticed that when I tried opening a torrent from Firefox, rather than adding it to the Azureus that was running, it decided to run a new one. Any ideas what's going on?

---

### Post by kaveraj on 2006-07-07
I had the same problem.

Just went to process manager and killed the couple of extra java programs that were running. Restarted azureus. And everything worked fine.

---

### Post by sandpaperback on 2006-07-07
I've noticed that if you close Azureus with the X button on the window, Azureus will keep running in the background.  While handy in a way, it's not what you'd expect.  If you choose File > Quit, it completely closes the program.  Not sure if that's related or not.

---

