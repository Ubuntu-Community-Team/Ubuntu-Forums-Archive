---
title: "Help a noob update Beyond the Red Line???"
date: 2007-11-22
forum: Gaming &amp; Leisure
---

### Post by drawkcab on 2007-11-22
Hey, I'm relatively new to Ubuntu, just getting my bearings. I am trying to update the demo for Beyond the Red Line (based on Battlestar Galactica).  The update file is this:

BtRLDemoUpdater.jar

How do I install this into my demo?  Can anyone walk me through it? Thanks!

---

### Post by housefly7k on 2008-06-12
Ran across this post, hope you were actually able to update it...

Here is what I did in case anyone else wanders along and finds this thread.

first check the version of java, you need version 1.5

To do that in terminal type

```
java -version
```

if you have java version 1.4 which is what i had you need to install sun-java5-bin I did it from synaptics but you could 

```
sudo apt-get install sun-java5-bin
```

Check that the version is updated:
```
java -version
```

next navigate in terminal to the folder containing the demo updater and type

```
java -jar BtRLDemoUpdater.jar 
```

And there should be a window that pops up with steps you can follow.

Goodluck.

---

### Post by housefly7k on 2008-06-12
there was a file named btrlpatch_linux.tar.gz in the directory, 
I extracted the files in it to the game folder, overwrote the existing files and started the game.

Now to figure out how to play multiplayer...

---

