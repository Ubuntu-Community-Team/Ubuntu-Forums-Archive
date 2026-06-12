---
title: "Lethal League won't start (non-wine)"
date: 2016-04-13
forum: Gaming &amp; Leisure
---

### Post by connerst on 2016-04-13
EDIT: Solution is to install 32bit libglew. But now, I cannot run from steam. I am going to try to start the game from steam and look for logs now.




When I run executable from the terminal, this is the output:
```
./LethalLeague: error while loading shared libraries: libGLEW.so.1.10: cannot open shared object file: No such file or directory
```
I have installed packages libglew-dbg, libglew-dev, libglew1.10, libglewmx-dbg, libglewmx-dev, libglewmx1.10, glew-utils. This game has worked previously with no problems on the same computer, but a different install(xubuntu). I have since wiped it and installed regular ubuntu, but I'm getting off topic.

Any suggestions? Am I just so retarded that I can't notice a glaring issue(most likely)?

---

### Post by Dennis N on 2016-04-14
That file should be provided by libglew1.10


_File list of package libglew1.10 in wily of architecture amd64_

```
[COLOR="#FF0000"]/usr/lib/x86_64-linux-gnu/libGLEW.so.1.10[/COLOR]
/usr/lib/x86_64-linux-gnu/libGLEW.so.1.10.0
/usr/share/doc/libglew1.10/changelog.Debian.gz
/usr/share/doc/libglew1.10/copyright

```

You could check that it is installed in the given location.

---

### Post by connerst on 2016-04-14
> **Dennis N said:**
> That file should be provided by libglew1.10


_File list of package libglew1.10 in wily of architecture amd64_

```
[COLOR=#FF0000]/usr/lib/x86_64-linux-gnu/libGLEW.so.1.10[/COLOR]
/usr/lib/x86_64-linux-gnu/libGLEW.so.1.10.0
/usr/share/doc/libglew1.10/changelog.Debian.gz
/usr/share/doc/libglew1.10/copyright

```

You could check that it is installed in the given location.

All the files you listed are there, still does not work.

---

### Post by Dennis N on 2016-04-14
Is the game a 32-bit application? If so, you need the 32-bit version of the package, and the file in question gets installed to another location. That may be why you get the file not found message.


> File list of package libglew1.10 in wily of architecture i386

[COLOR="#FF0000"]/usr/lib/i386-linux-gnu/libGLEW.so.1.10[/COLOR]
/usr/lib/i386-linux-gnu/libGLEW.so.1.10.0
/usr/share/doc/libglew1.10/changelog.Debian.gz
/usr/share/doc/libglew1.10/copyright

In Synaptic Package Manager, the 32-bit version is libglew1.10:i386

---

### Post by connerst on 2016-04-14
> **Dennis N said:**
> Is the game a 32-bit application? If so, you need the 32-bit version of the package, and the file in question gets installed to another location. That may be why you get the file not found message.

In Synaptic Package Manager, the 32-bit version is libglew1.10:i386

I installed libglew1.10:i386, and rebooted(just to be safe).

I can run the executable and the game opens, but I cannot open it from Steam. Now this is a totally different problem.

---

### Post by connerst on 2016-04-17
OK I've been looking around and I can't find a solution to the not starting from steam thing. Any help?

---

