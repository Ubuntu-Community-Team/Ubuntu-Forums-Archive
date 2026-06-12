---
title: "Enemy Territory Quake Wars Demo installer won't execute."
date: 2011-04-18
forum: Game Specific Discussions
---

### Post by creative31 on 2011-04-18
Hello, I have recently downloaded the client for the Enemy Terriory Quake Wars demo, and I can't seem to get it to execute.

First, I went into the directory where the file is at, and did 
```
chmod +x ETQW-demo-client-1.1.full.r5.x86.run
```
And then did
```
sudo sh ETQW-demo-client-1.1.full.r5.x86.run
```

And to my dismay, I got this error back.
```
STUBBED: ftell is 32 bit!
 at /home/timo/Build/mojosetup/fileio.c:246
Error opening terminal: xterm.

```
Now, I have no idea why this is happening, I've tried making it executable via Right Click -> Properties -> Allow file to run as executable.
Tried 
```
sudo ./ETWQ-demo-client-1.1.full.r5.x86.run
```

And still get the same response..

So after doing a bit of research, I found this happens when you don't have the required libs (ia32), though, I am not running a 64 bit OS, so I don't (think) I need a 32 bit layers to run a 32 bit application. And I can't find a package for ia32 for a 32bit OS. So what else could be the cause of this? And how could I fix it?

Any help will be greatly appreciated! And let me know if you need any more information.

**Nevermind: **I managed to fix the problem, it was something with binary, so I downloaded a different one, and it ran perfectly! Maybe is was just an .x86_64 file discuised as an .x86, meh, who knows..

---

### Post by creative31 on 2011-04-20
:popcorn:

bump :s

---

