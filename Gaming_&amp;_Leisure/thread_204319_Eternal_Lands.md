---
title: "Eternal Lands"
date: 2006-06-26
forum: Gaming &amp; Leisure
---

### Post by Ryan H on 2006-06-26
I've installed Eternal Lands and I put it in /home/ryan/eternal-lands, I chmodded  el.x86_64.linux.bin but when I tried to excecute el.x86_64.linux.bin it says:
> ./el.x86_64.linux.bin: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory

I am currently running Ubuntu 6.06 64-Bit.

-Ryan H

---

### Post by thunderduck3141 on 2006-06-26
try 
apt-cache search libsdl

---

### Post by thunderduck3141 on 2006-06-26
then install the package that fits (like libsdl-2.0 or something)

---

### Post by LKRaider on 2006-06-26
Searching **libsdl-net** on Synaptic returns just the package you need: libsdl-net1.2

I think it should work on a 64-bit system too.

---

### Post by Ryan H on 2006-06-26
That worked! I did that a few more times for some other packages that it asked for. But now when I execute el.86_64.linux.bin, nothing happens, no error or anything, just nothing happens. How do I play the game?

-Ryan H

---

### Post by digimars on 2006-06-26
Just downloaded this game, what am I supposed to do with chmod?  I've never used that before.  I tried the man pages for it, but it doesn't make too much sense for what options I need to use.

Ok, figured it out:
```

chmod 775 <app>

```

To run the game, I cd'd to the directory and ran:
```

./el.x86.linux.bin

```

And now I have the game running.

---

### Post by LKRaider on 2006-06-27
@**Ryan_H** : you are trying to run some 64bit version of the game?
Maybe try running the 32bit version and see if that works.
If it does, then file a bug report to whoever compiled the 64bit package for you ;)

---

### Post by Ryan H on 2006-06-27
Neither one does anything. I got the download of the Eternal Land's main site.

-Ryan H

---

### Post by LKRaider on 2006-06-27
Did you run it from a terminal? If not, try it and see if any messages appear there.

If nothing appears, try running with the debug command strace, like this:
```
strace ./el.x86.linux.bin
```

Then post the output of this at the [pastebin]("http://paste.ubuntu-nl.org") and link it here, so maybe we can help.

---

### Post by gigaferz on 2006-07-25
well im looking for the libsdl on the packet manager..and there is nothing like it...there are many lib's..but..nothing with a "-net"

---

### Post by Perfect Storm on 2006-07-25
You need to enable universe in your sourcelist to get access to libsdl-net

---

### Post by gigaferz on 2006-07-25
will automatix do that for me?? (once i check the universe box)

Or should I use the synaptic manager?

---

### Post by Perfect Storm on 2006-07-25
It's up to you.
You can manually editing the sourcelist.

```
sudo nano /etc/apt/sources.list
```

Then uncomment the universe.
Save and exit.
Then:
```
sudo apt-get update
```

---

